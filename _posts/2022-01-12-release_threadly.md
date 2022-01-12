---
title:  "Threadly 6.7 released"
published: true
permalink: release20220112.html
summary: 
tags: [news, release, release-threadly]
---

We released Threadly 6.7 today.  This release is primarily in prep for a future 7.0 major version.  Notably the implementation of ListenableFutureTask will be changing in order to support the removal of UnsafeAccess for JDK 17+ support.  In 7.0 we no longer will be supporting ListenableFutureTasks to be used in a recurring fashion.  This was not a feature used by Threadly (the concept is awkward with ListenableFuture's), but is used by our compatibility layer.  The comparability layer will continue to function in 7.0 normally but ListenableFutureTask will not have a public API that allows for recurring usage.

As always, if you are using our last version with no depreciated API's, this should indicate an upgrade to the next major version with no other needed changes.

You can read more about this release in the <a href="https://github.com/threadly/threadly/releases/tag/release-6.7">release notes</a>.

{% include links.html %}
