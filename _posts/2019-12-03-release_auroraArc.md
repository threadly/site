---
title:  "AuroraArc 0.13 released"
published: true
permalink: release20191203.html
summary: 
tags: [news, release, release-auroraArc]
---

The newly released 0.13 of auroraArc marks a notable improvement in reliability when a replica is an unhealthy state but being unused. It adds additional state setting cases to the connections which it ignores.  When the connection is actually used for a query or other server side change then the error will be thrown.

{% include links.html %}
