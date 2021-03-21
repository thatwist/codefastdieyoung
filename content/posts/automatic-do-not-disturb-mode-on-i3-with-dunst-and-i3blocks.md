+++
title = "automatic do-not-disturb mode on i3 with dunst and i3blocks"
author = ["Yurii Ostapchuk"]
publishDate = 2021-03-12T00:00:00+02:00
lastmod = 2021-03-21T22:45:32+02:00
weight = 2002
draft = true
+++

Wwhat I really like about linux is it's modularity and simplicity
when it comes to arch and i3 it is even more modular and simple at the same time.
don't get me wrong - it of course requires some sort of learning curve but then you understand ..
out of the box these combo gives you pretty good starting point, although lacks some features here and there
which usually you can live without but through the time it annoys you.
And then the exciting part starts when you get your hand dirty creating something твоє
One of those cases is when I'm on the meeting, sharing my screen, and then dunst bubbles up
sometimes it can be personal leak

-   dunstctl
    -   fortunately provides toggle, lets use it
-   i3blocks
    -   (use icons / make sure font)
-   cron & determine camera on
    ok what's left, in general I want always go into do-not-disturb when on meeting
    this requires determining state of the camera

[//]: # "Exported with love from a post written in Org mode"
[//]: # "- https://github.com/kaushalmodi/ox-hugo"
