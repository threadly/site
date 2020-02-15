---
title:  "Threadly 5.36 released"
published: true
permalink: release20190328.html
summary: 
tags: [news, release, release-threadly]
---

A couple days ago we silently released 5.35 which included the new <a href="javadocs/5.35/org/threadly/util/debug/FilteredStackProfiler.html">FilteredStackProfiler</a> as an additional Profiler implementation.  This quickly following release includes protection against Exception cause cycles for <a href="javadocs/5.35/org/threadly/util/ExceptionUtils.html">ExceptionUtils</a>.  A `cause` which loops to a previous exception could easily result in an infinite loop.  This change detects and guards against this condition without impacting performance generally.

{% include links.html %}
