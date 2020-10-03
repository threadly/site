---
title: "Threadly Overview"
keywords: threadly concurrency java aurora jdbc
sidebar: home_sidebar
permalink: index.html
summary: A collection of java libraries to assist with development of java services to help bring new levels of safety, performance, and reliability.concurrent java applications.  Ranging from concurrency tools designed to complement to java.util.concurrent, unit testing tools, NIO netwrking, AWS Aurora JDBC driver.
---

## Threadly Concurrency Overview
![Build status](https://badge.buildkite.com/a6b3c844ce059f96c577ec485ab9fb36925790deec8e26dcd9.svg?branch=master)

[Threadly](https://github.com/threadly/threadly/) provides a variety of thread pooling designs, ranging from the unique priority based, high performance, thread pools ([PriorityScheduler](javadocs/threadly/6.5/org/threadly/concurrent/PriorityScheduler.html) and [SingleThreadScheduler](javadocs/threadly/6.5/org/threadly/concurrent/SingleThreadScheduler.html) for example).  To the ability to create a hierarchy of thready pools (sub pools in threadly named ["Limiters"](javadocs/threadly/6.5/org/threadly/concurrent/wrapper/limiter/package-summary.html), or behavior controlling pool wrappers like the [KeyDistributedExecutor](javadocs/threadly/6.5/org/threadly/concurrent/wrapper/KeyDistributedExecutor.html).  In all cases threadly pools are designed to be safe, able to be garbage collected (or even use the [CentralThreadlyPool](javadocs/threadly/6.5/org/threadly/concurrent/CentralThreadlyPool.html) for when you really don't want to worry about the pool life cycle).

Beyond the pools, threadly's [ListenableFuture](javadocs/threadly/6.5/threadly/concurrent/future/ListenableFuture.html) provides a very clean and functional way to implement async callback / transformation operations.  Allowing for simple [".map"]("javadocs/threadly/6.5/org/threadly/concurrent/future/ListenableFuture.html#map(java.util.function.Function)") and [".flatMap"]("javadocs/threadly/6.5/org/threadly/concurrent/future/ListenableFuture.html#flatMap(java.util.function.Function)") like transformations to provide monad like semantics.  In addition tools like [FutureUtils](javadocs/threadly/6.5/org/threadly/concurrent/future/FutureUtils.html) helps easily make powerful use of these basic features, as well as tooling when managing collections of futures.

To get a more complete overview of our features take a look at our [threadly features wiki page](https://github.com/threadly/threadly/wiki/Threadly-Features).

Include threadly in your project with the maven coordinates `org.threadly:threadly:6.5`.

## Threadly Unit Test Overview
![Build status](https://badge.buildkite.com/8bfb74c7efa06fb26fd53f710996951a4e907a8b72d76ae8a6.svg?branch=master)

[Threadly-Test](https://github.com/threadly/threadly-test) provides utilities to take asynchornous designs and make them easy to unit test deterministicly and quickly.  Fitting into the threadly ecosystem is the [TestableScheduler](javadocs/threadly-test/0.1/org/threadly/test/concurrent/TestableScheduler.html) which will only execute the provided tasks when `.tick()` is invoked.  Other examples are the [AsyncVerifier](javadocs/threadly-test/0.1/org/threadly/test/concurrent/AsyncVerifier.html) and the [TestCondition](javadocs/threadly-test/0.1/org/threadly/test/concurrent/TestCondition.html) which help in checking async operations, or blocking till an async operation completes as expected.

To get a more complete overview of our test features take a look at our [threadly-test features wiki page](https://github.com/threadly/threadly-test/wiki/Threadly-Features,-Unit-Testing).

Include threadly-test in your project with the maven coordinates `org.threadly:threadly-test:1.0`.

## AuroraArc Overview
![Build status](https://badge.buildkite.com/a2ee5480877e0b8effd44d52e5c71673abff406b8fb8d994d8.svg?branch=master)

[AuroraArc](https://github.com/threadly/auroraArc) is an AWS Aurora aware JDBC driver.  This JDBC driver takes advantage of Aurora's rapid failover capabilities.  The driver monitors all members in the cluster individually and will distribute requests across the cluster to try and provide the best performance and reliability.  This includes using hints from the application to know when requests should be sent to replica servers.  It also interpets errors to try and provide degraded service if possible, or otherwise make use of Aurora's rapid failover capabilities.

Use the mysql AuroraArc driver with the maven coordinates `org.threadly:auroraArc-mysql:0.15` and the postgresql AuroraArc driver with the coordinates `org.threadly:auroraArc-psql:0.15`.

## Litesockets Overview
![Build status](https://badge.buildkite.com/2a02aa42abb9df40641a133c719792b7c94a435f8a3c692653.svg?branch=master)

[Litesockets](https://github.com/threadly/litesockets/) provides a high performance non-blocking networking abstraction.  It uses the [KeyDistributedExecutor](javadocs/threadly/6.5/org/threadly/concurrent/wrapper/KeyDistributedExecutor.html) to have every individual connections be handled in a single threaded manner.  This allows the user to not need to consider concurrency concerns unless using datastructures that are shared by multiple connections.

Litesockets can be included from the maven central coordinates `org.threadly:litesockets:4.14`.

## News
<div class="post-list">
    {% for post in site.posts limit:10 %}

<h8><a class="post-link" href="{{ post.url | remove: "/" }}">{{ post.title }}</a></h8>
    <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }} /
        {% for tag in post.tags %}
            <a href="{{ "tag_" | append: tag | append: ".html"}}">{{tag}}</a>{% unless forloop.last %}, {% endunless%}
            {% endfor %}</span>

    <p>{% if post.summary %} {{ post.summary | strip_newlines | truncatewords: 200 }} {% else %} {{ post.content | truncatewords: 200 }} {% endif %}</p>

    {% endfor %}
</div>

{% include links.html %}
