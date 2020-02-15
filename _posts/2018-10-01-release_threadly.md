---
title:  "Threadly 5.28 release"
published: true
permalink: release20181001.html
summary: 
tags: [news, release, release-threadly]
---

5.28 released with several improvements around `ListenableFuture`.  Described in detail on the <a href="https://github.com/threadly/threadly/releases/tag/release-5.28">changelog</a>, this release includes a minor bugfix around canceling flatMap'ed futures, as well as significant debugging improvements.  This release provides the ability to get the stack of a running future (or if a mapped future waiting on a result, the stack of the currently executing parent future).</p>

{% include links.html %}
