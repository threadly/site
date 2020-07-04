---
title:  "Threadly 6.4 released"
published: true
permalink: release20200704.html
summary: 
tags: [news, release, release-threadly]
---

Threadly 6.4 was released today.  This mostly minor release includes a bug fix to the recently added <a href="javadocs/threadly/6.3/org/threadly/concurrent/wrapper/limiter/OrderedExecutorLimiter.html">OrderedExecutorLimiter</a> for when returned ListenableFuture's are canceled.  This also includes an improvement to the <a href="javadocs/threadly/6.3/org/threadly/util/debug/Profiler.html">Profiler</a> to be able to identify idle ForkJoinPool threads.  This reduces the output of the profiler for these threads as well as slightly optimizes the memory overhead for tracking these traces.

The above is also summarized in the <a href="https://github.com/threadly/threadly/releases/tag/release-6.4">release notes</a>.  There is no new javadocs published for this release as no API changes occurred.

{% include links.html %}
