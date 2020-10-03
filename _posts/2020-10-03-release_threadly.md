---
title:  "Threadly 6.5 released"
published: true
permalink: release20201003.html
summary: 
tags: [news, release, release-threadly]
---

Threadly 6.5 was released today.  This release provides improvements to <a href="javadocs/threadly/6.5/org/threadly/concurrent/ReschedulingOperation.html">ReschedulingOperation</a> and <a href="javadocs/threadly/6.5/org/threadly/concurrent/ConfigurableThreadFactory.html">ConfigurableThreadFactory</a>.

<a href="javadocs/threadly/6.5/org/threadly/concurrent/ReschedulingOperation.html">ReschedulingOperation</a> got an internal performance improvement to avoid re-queuing through the executor if it was signaled to run while it was currently executing.  Instead looping on the thread it already has (for a limited number of loops).  This provides a notable performance improvement by avoiding to re-queue through the executor, but it can also prevent a stack overflow when <a href="javadocs/threadly/6.5/org/threadly/concurrent/SameThreadSubmitterExecutor.html">SameThreadSubmitterExecutor</a> is used.

<a href="javadocs/threadly/6.5/org/threadly/concurrent/ConfigurableThreadFactory.html">ConfigurableThreadFactory</a> now additionally has the ability to configure a Consumer to accept threads as they are created.  This can be useful to provide additional custom logic for each thread.  Notably this can be useful for tracking threads for debugging purposes, like when <a href="javadocs/threadly/6.5/org/threadly/util/debug/ControlledThreadProfiler.html">ControlledThreadProfiler</a> is used.

You can read more about this release in the <a href="https://github.com/threadly/threadly/releases/tag/release-6.5">release notes</a>.

{% include links.html %}
