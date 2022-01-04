+++
title = "Beware of SQL `not in (select .. from)` statement.."
author = ["Yuri Ostapchuk"]
date = 2022-01-03T19:47:00-06:00
lastmod = 2022-01-03T19:47:03-06:00
tags = ["sql", "data"]
draft = false
weight = 2003
[menu.main]
  weight = 2003
  identifier = "beware-of-sql-not-in--select-dot-dot-from--statement-dot-dot"
+++

Stumbled upon this "corner case" while debugging queries in Redshift today - has stolen a full day (probably more) from me.

Consider simple example:

```sql
create table test1 (a varchar, b varchar);
create table test2 (c varchar);

insert into test1 values ('a1', 'active'), ('a2', 'inactive'), (null, 'inactive');
insert into test2 values ('a1'), ('a2');
```

now, this one is ok:

```sql
select * from test2 where c in (select distinct a from test1 where b != 'active');
>> a2
```

and this one - do you think it returns a1?

```sql
select * from test2 where c not in (select distinct a from test1 where b != 'active');
```

no - empty result set :facepalm:

There is something specific about how SQL handles comparison like `1 = NULL` - it uses three-valued logic so the result of this statement is `UNKNOWN` and not `FALSE`.

The `NOT IN (1, 2, NULL)` statement would be equivalent to `NOT (c = 1 OR c = 2 OR c = NULL)` which will propagate `UNKNOWN` as a result of the whole condition.

So given above logic, again, this does not return:

```sql
select 1 where not (1=2 or 1=null);
```

while this returns 1:

```sql
select 1 where not (1=2 or 1=3);
```

This is how it is implemented in most of the major DB query engines including Redshift, Postgres, MySQL.

Beware of filtering out nulls in `not in` :slightly_smiling_face:

[//]: # "Exported with love from a post written in Org mode"
[//]: # "- https://github.com/kaushalmodi/ox-hugo"