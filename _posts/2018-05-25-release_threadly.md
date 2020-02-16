---
title:  "4 Threadly releases (5.20 -> 5.23)"
published: true
permalink: release20180525.html
summary: "Details around a series of recent releases.  These releases are focused around the `ListenableFuture` and include a variety of feature improvements and bug fixes."
tags: [news, release, release-threadly]
---  

On May 18th 5.20 was released which includes important bug fixes for communicating the "canceled" state after a map / flatMap operation on a future.  It also includes internal performance improvements and minor features expansions (which can be read about in the <a href="https://github.com/threadly/threadly/releases/tag/release-5.20">5.20 changelog</a>).

Shortly after 5.21 and 5.22 was released, focused around another bug fix around canceling collections of Futures produced by FutureUtils.

Along the way we also made the change to use <a href="http://buildkite.com">buildkite</a> to perform our CI solution.  Having talked with them I am pretty confident this will be a better fit for our needs.

As threadly continued to recieve more attention, today 5.23 was released.  This release includes a small bug fix for the `Profiler` when used with the `SameThreadSubmitterExecutor`.  This release also provides a number of improvements in performance with futures and other minor improvements described in the <a href="https://github.com/threadly/threadly/releases/tag/release-5.23">5.23 changelog</a>.</p>

{% include links.html %}
