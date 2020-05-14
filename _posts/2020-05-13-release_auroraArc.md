---
title:  "AuroraArc 0.14 released"
published: true
permalink: release20200513.html
summary: 
tags: [news, release, release-auroraArc]
---

The new 0.14 version of auroraArc provides a long wanted feature to be able to weight servers in how they may be randomly chosen.  Details about this and the other changes included are listed on the <a href="https://github.com/threadly/auroraArc/releases/tag/release-0.14">release details</a>.

The ability to set a server weight at runtime allows for a number of new features in how an Aurora cluster can be utilized.  The easiest and most obvious use case is if you have a server of a larger instance type.  Having weights set to match instance types can allow for more fluid deployment / cluster rotation strategies.  It can also make a cluster more stable in a failover condition where the readers and writers are of different types.

This can also be useful in cost and latency optimizations.  If you know what availability zone you are in you may choose to set servers in other zones to a weight of '0'.  Making them only used if there is no healthy servers in your availability zone.

This marks another huge step in providing the unique load and failover capabilities this driver is hoping to provide.

{% include links.html %}
