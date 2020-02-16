---
title:  "Threadly 5.7 release"
published: true
permalink: release20171219.html
summary: 
tags: [news, release, release-threadly]
---

Released version 5.7.  This is a fairly significant feature expansion release.  Allowing limiters to not be impacted by the listener (monads) execution if desired.  As well as the newly added `CentralThreadlyPool`.  Allowing the limiters to not limit listeners / map functions allows you to be sure you are limiting a core task functionality, and not also including limits towards operations which may occur after that core task completes.  The `CentralThreadlyPool` allows you to gain access to a scheduler / executor for the immediate needs, without having to worry about a scheduler life cycle (ie shutting down).  Internally this pool will try to reduce thread churn as much as possible while also making sure that the threads are available for the task demand requested (and not letting any single scheduler fully take control over the pool).  This feature has been one in the works for a while, and I am pretty happy with how it came out, so I highly encourage you to <a href="javadocs/threadly/5.7/org/threadly/concurrent/CentralThreadlyPool.html">look at it!</a>

{% include links.html %}
