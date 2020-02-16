---
title:  "Threadly 5.16 released"
published: true
permalink: release20180428.html
summary: 
tags: [news, release, release-threadly]
---

Version 5.16 was released today.  I had planned for 5.16 to be a feature expansion release.  I have been working on a new sub-pool that will help threadly's central pool.  However it's not ready yet.  Instead this release contains a bug fix for the central pool where `isolatedTask` recurring tasks could decrement the central pools size after every run, eventually resulting in logging exceptions as the pool tries to shrink itself below zero.  This critical bug fix pushed the release forward.  But I am also excited to announce a new feature in <a href="javadocs/threadly/5.16/org/threadly/concurrent/future/FutureUtils.html">FutureUtils</a>.  Now in addition to `scheduleWhile` there is `executeWhile`.  This is more flexible to other pool types (as it does not even require a pool, just a <a href="javadocs/threadly/5.16/org/threadly/concurrent/future/ListenableFuture.html">ListenableFuture</a>).  It is conceptually the same, except where a delay for retry is not desired.

{% include links.html %}
