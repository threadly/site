---
title:  "Threadly 5.18"
published: true
permalink: release20180504.html
summary: 
tags: [news, release, release-threadly]
---

A feature expansion release of 5.18 was published to maven central today.  The primary feature in this release is the add of <a href="javadocs/5.18/org/threadly/concurrent/future/ListenableFuture.html#mapFailure-java.lang.Class-java.util.function.Function-">mapFailure</a> and <a href="javadocs/5.18/org/threadly/concurrent/future/ListenableFuture.html#mapFailure-java.lang.Class-java.util.function.Function-">flatMapFailure</a> to <a href="javadocs/5.18/org/threadly/concurrent/future/ListenableFuture.html">ListenableFuture</a>.  These functions allow you to async transform futures from the error conditions back into results or into different error conditions.

{% include links.html %}
