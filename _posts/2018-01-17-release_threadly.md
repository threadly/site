---
title:  "Threadly 5.10 and 5.11 release"
published: true
permalink: release20180117.html
summary: 
tags: [news, release, release-threadly]
---

Released yesterday, 5.10 includes more minor bug fixes, as well as the opportunity to further optimize listeners being executed on `ListenableFuture`'s.  Read more in the <a href='javadocs/5.10/org/threadly/concurrent/future/ListenableFuture.ListenerOptimizationStrategy.html'>ListenableFuture.ListenerOptimizationStrategy javadocs</a>.

Released today, 5.11 provides pre-5.10 functionality when mapping ListenableFutures as `throwMap`.  It was discovered that there is good reason to sometimes have the mapper function throw an exception, and that those should not be treated as "uncaught" exceptions.  The default behavior of `map` will still report the exception to `ExceptionUtils.handleException`, since that is the behavior most people probably expect.  But `throwMap` was added to facilitate the rare use case where you want / expect an exception to be thrown.

{% include links.html %}
