---
title:  "Threadly 5.29 release"
published: true
permalink: release20181101.html
summary: 
tags: [news, release, release-threadly]
---

Bug fix release 5.29 to provide improvements when mapping futures (either with `.map` or things like `FutureUtils.executeWhile`).  Changes are focused around stack trace communication, and propagating future cancellations to ensure unnecessary processing does not go un-interrupted.

{% include links.html %}
