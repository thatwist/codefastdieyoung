+++
title = "What outputMode in Spark Structured Streaming really means"
author = ["Yuri Ostapchuk"]
lastmod = 2021-12-29T00:46:29-06:00
tags = ["data", "structuredstreaming"]
draft = true
weight = 2001
+++

## Thesises {#thesises}

provide some facts that are rather unclear from documentation and api but available only when looking into code

-   (first, ref to table in spark docs)
-   if no aggregations - Update &lt;=&gt; Append, Complete is not available if no aggregations
-   !outputMode param in flatMapGroupsWithState - has no real effect, just semantics + UnsupportedOperationChecker
-   watermark should be available on grouping expression for aggregates (but not flatMapGroups as it is not really an aggregate)
-   watermark should be availeble in child of groupby for \*mapgroupswithstate
-   on of the hacks is to group-by without time-columns + flatmapgroups - you get watermark timeout functionality but should manage timeouts yourself
-   any regular aggregation will be wrapped into StateStoreRestore/StateStoreSave
-   ?query outputmode update/append have no real diff for flatmapgroupwithstate (as well as mappingfunc outputMode)
-   ?outputMode no diff for memory sink

[//]: # "Exported with love from a post written in Org mode"
[//]: # "- https://github.com/kaushalmodi/ox-hugo"