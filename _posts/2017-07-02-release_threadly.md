---
title:  "Threadly 5.1 critical bug fix"
published: true
permalink: release20170702.html
summary: 
tags: [news, release, release-threadly]
---

Patch version 5.1 fixes regression in 5.0 `PriorityScheduler` where threads may forever go idle.  This is a regression due to an optimization when interactions with other blocking actions using `LockSupport`.  It is critical that all 5.0 usage is upgraded to use version 5.1 or newer.

{% include links.html %}
