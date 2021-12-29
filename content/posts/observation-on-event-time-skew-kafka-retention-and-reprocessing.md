+++
title = "Observation on event-time skew, kafka retention and reprocessing of events with watermark-based streaming aggregation"
author = ["Yuri Ostapchuk"]
lastmod = 2021-12-29T00:46:29-06:00
tags = ["data", "structuredstreaming", "kafka"]
draft = true
weight = 2002
+++

one interesting observation on kafka event time skew and reprocessing backlog of events by watermark-based streaming aggregation:
earliest events available in kafka topic might be skewed by event-time between partitions very much
e.g. in audio topic earlest event in partition1 might be 10:00 while in partition2 10:10 - skew by 10mins
while latest events are always aligned (few seconds skew) - obviously
this might make big difference while reprocessing of data by job which does aggregation with watermark
if watermark is low (2 minutes), starting with earliest with some rate limitation e.g. 10msgs/sec will have a lot of events filtered out by watermark for some partitions which are skewed
as streaming engine will move in equal 10-message batches in each partition preserving the skew almost for the whole backlog of events being processed
I'm wondering how kafka retention log cleaner then works - I assumed it cleans log messages based on time it came to the system - but it seems like the longer the retention period is the bigger skew is

[//]: # "Exported with love from a post written in Org mode"
[//]: # "- https://github.com/kaushalmodi/ox-hugo"