---
title:  "Threadly 5.34 released"
published: true
permalink: release20190313.html
summary: 
tags: [news, release, release-threadly]
---

This release includes significant changes to the `ListenableFuture` API.  Defined in the <a href="https://github.com/threadly/threadly/releases/tag/release-5.34">release details</a>, the most significant changes are the depreciation of `addCallback` and `addListener`.  Now providing more functionality with a `callback` and `listener` function that return the instance, as well as a `resultCallback` and `failureCallback` function for when there is only one state needing checked.

{% include links.html %}
