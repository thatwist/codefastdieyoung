+++
title = "what is bigdata"
author = ["Yurii Ostapchuk"]
lastmod = 2021-07-23T10:29:15-04:00
tags = ["data"]
draft = true
weight = 2001
+++

What is bigdata
The classical definition of BigData is emphasized in so called 3 Vs of BigData:
Volume
whenever you have increased sizes of datasets you need to process and/or analyze (Tera-,Peta-,etc -byte scale), traditional relational databases will fail. This need, early encountered in the big companies like Google, Yahoo, Facebook, etc. gave born to particular programming models and toolset specific to solving a problem of such scale. Nowadays  almost all of the businesses of middle to big size demand and will benefit from applying BigData methodologies.
Velocity
Once volumes rises, the need to not degrade in latency faced, not to mention that the modern world demands quicker insights from data, so, a standalone problem of managing speed is faced. A certain hardware engineering new-founds enabled to move from on-disk to in-memory data processing, transitioning certain workloads from CPU to GPU for even faster processing. To mention, you may not need to store a lot of data or may not even have much of it, but if you need sub-second latency from ingestion to decision-making - this is the problem for BigData.
Variety
Not only data can be big, but metadata as well. Structuring, governing and doing other management tasks on many types of your data can be and is challanging. Especially in a large organizations, if not done correctly, a lake of data can quickly become a data swamp.

[//]: # "Exported with love from a post written in Org mode"
[//]: # "- https://github.com/kaushalmodi/ox-hugo"
