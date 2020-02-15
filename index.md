---
title: "Threadly - High performance java libraries"
keywords: threadly concurrency java aurora jdbc
tags: [getting_started]
sidebar: mydoc_sidebar
permalink: index.html
summary: A collection of java libraries to assist with development of java services to help bring new levels of safety, performance, and reliability.concurrent java applications.  Ranging from concurrency tools designed to complement to java.util.concurrent, unit testing tools, NIO netwrking, AWS Aurora JDBC driver.
---

## Threadly Concurrency Overview

[Threadly](https://github.com/threadly/threadly/) provides a variety of thread pooling designs, ranging from the unique priority based, high performance, thread pools ([PriorityScheduler](javadocs/5.43/org/threadly/concurrent/PriorityScheduler.html) and [SingleThreadScheduler](javadocs/5.43/org/threadly/concurrent/SingleThreadScheduler.html) for example).  To the ability to create a hierarchy of thready pools (sub pools in threadly named ["Limiters"](javadocs/5.43/org/threadly/concurrent/wrapper/limiter/package-summary.html), or behavior controlling pool wrappers like the [KeyDistributedExecutor](javadocs/5.43/org/threadly/concurrent/wrapper/KeyDistributedExecutor.html).  In all cases threadly pools are designed to be safe, able to be garbage collected (or even use the [CentralThreadlyPool](javadocs/5.43/org/threadly/concurrent/CentralThreadlyPool.html) for when you really don't want to worry about the pool life cycle).

Beyond the pools, threadly's [ListenableFuture](javadocs/5.4333rg/threadly/concurrent/future/ListenableFuture.html) provides a very clean and functional way to implement async callback / transformation operations.  Allowing for simple [".map"]("javadocs/5.43/org/threadly/concurrent/future/ListenableFuture.html#map(java.util.function.Function)") and [".flatMap"]("javadocs/5.43/org/threadly/concurrent/future/ListenableFuture.html#flatMap(java.util.function.Function)") like transformations to provide monad like semantics.  In addition tools like [FutureUtils](javadocs/5.43/org/threadly/concurrent/future/FutureUtils.html) helps easily make powerful use of these basic features, as well as tooling when managing collections of futures.

To get a more complete overview of our features take a look at our [threadly features wiki page](https://github.com/threadly/threadly/wiki/Threadly-Features).

Include threadly in your project with the maven coordinates `org.threadly:threadly:5.43`.

## Threadly Unit Test Overview
[Threadly-Test](https://github.com/threadly/threadly-test) provides utilities to take asynchornous designs and make them easy to unit test deterministicly and quickly.  Fitting into the threadly ecosystem is the [TestableScheduler](https://threadly.github.io/threadly-test/javadocs/0.1/org/threadly/test/concurrent/TestableScheduler.html) which will only execute the provided tasks when `.tick()` is invoked.  Other examples are the [AsyncVerifier](https://threadly.github.io/threadly-test/javadocs/0.1/org/threadly/test/concurrent/AsyncVerifier.html) and the [TestCondition](https://threadly.github.io/threadly-test/javadocs/0.1/org/threadly/test/concurrent/TestCondition.html) which help in checking async operations, or blocking till an async operation completes as expected.

To get a more complete overview of our test features take a look at our [threadly-test features wiki page](https://github.com/threadly/threadly-test/wiki/Threadly-Features,-Unit-Testing).

Include threadly-test in your project with the maven coordinates `org.threadly:threadly-test:0.1`.

## AuroraArc Overview
[AuroraArc](https://github.com/threadly/auroraArc) is an AWS Aurora aware JDBC driver.  This JDBC driver takes advantage of Aurora's rapid failover capabilities.  The driver monitors all members in the cluster individually and will distribute requests across the cluster to try and provide the best performance and reliability.  This includes using hints from the application to know when requests should be sent to replica servers.  It also interpets errors to try and provide degraded service if possible, or otherwise make use of Aurora's rapid failover capabilities.

Use the mysql AuroraArc driver with the maven coordinates `org.threadly:auroraArc-mysql:0.13` and the postgresql AuroraArc driver with the coordinates `org.threadly:auroraArc-psql:0.13`.

## Litesockets Overview

[Litesockets](https://github.com/threadly/litesockets/) provides a high performance non-blocking networking abstraction.  It uses the [KeyDistributedExecutor](javadocs/5.43/org/threadly/concurrent/wrapper/KeyDistributedExecutor.html) to have every individual connections be handled in a single threaded manner.  This allows the user to not need to consider concurrency concerns unless using datastructures that are shared by multiple connections.

Litesockets can be included from the maven central coordinates `org.threadly:litesockets:4.14`.

## News

### February 16th - New website
A long overdue replacement of the website.  This new site allows us to better provide documentation across all of our libraries and tools.  We can now provide a lot more information with this layout, and links to all our javadocs.

### February 13th - threadly 5.43 + threadly-test 0.1 released
Most notable is the move of the org.threadly.test package to the new <a href="https://github.com/threadly/threadly-test">threadly-test</a> archive (maven coordinates `org.threadly:threadly-test:0.1`).  This is planned to be the last release before we switch to the 6.0 API.  The <a href="https://github.com/threadly/threadly/releases/tag/release-5.43">release details</a> as always provides complete details on included changes.

### December 9th - threadly 5.42 released
5.42 provides performance improvements to RateLimiterExecutor and ExecutorLimiter.  The gains in RateLimiterExecutor being most significant, providing huge improvements in cases where thread contention exists. 

### October 24th - threadly 5.41 released
Another 5.X release focused primarily on performance improvements and other internal updates.  The <a href="https://github.com/threadly/threadly/releases/tag/release-5.41">release details</a> outlines the specific areas of improvement.

### September 4th - threadly 5.40 released
As we start to think more about a 6.0 release, backwards compatible API changes have been provided in the new <a href="https://github.com/threadly/threadly/releases/tag/release-5.40">5.40 release</a>.  In this we moved and renamed Watchdog into the new watchdog package.  As part of this we also added a new "PollingWatchdog" to be able to provide more flexible timeout mechanics when desired.

### August 25th - threadly 5.39 released
<a href="https://github.com/threadly/threadly/releases/tag/release-5.39">5.39</a> released, adding ConfigureableThreadFactory.builder() as an easier way to configure the ThreadFactory.  Also included are some minor internal improvements to ListenableFuture.map operations.  We are starting to formalize a 6.0 release, take a look at the <a href="https://github.com/threadly/threadly/milestone/53">6.0 Release Milestone</a>.  If you have any ideas of what would be good to include in a upcoming 6.0, or even a future 7.0 release, feel free to open an <a href="https://github.com/threadly/threadly/issues">issue</a>.

### June 25th - threadly 5.38 released
This release provides some minor feature expansions to FutureUtils and the new ArrayIterator.  Read about them in the <a href="https://github.com/threadly/threadly/releases/tag/release-5.38">release details</a>.

### May 23rd - threadly 5.37 released
This release includes new features around queue consumption and work processing.  See the new package org.threadly.concurrent.processing and the <a href="https://github.com/threadly/threadly/releases/tag/release-5.37">release details</a>.

### March 13th - threadly 5.34 released
This release includes significant changes to the ListenableFuture API.  Defined in the <a href="https://github.com/threadly/threadly/releases/tag/release-5.34">release details</a>, the most significant changes are the depreciation of `addCallback` and `addListener`.  Now providing more functionality with a `callback` and `listener` function that return the instance, as well as a `resultCallback` and `failureCallback` function for when there is only one state needing checked.

### May 18th
5.20 was released which includes important bug fixes for communicating the "canceled" state after a map / flatMap operation on a future.  It also includes internal performance improvements and minor features expansions (which can be read about in the changelog).

### May 15th
Following closely behind 5.18, 5.19 provides internal improvements as well as minor features that can be read about in the changelog.

### May 4th
A feature expansion release of 5.18 was published to maven central today.  The primary feature in this release is the add of `mapFailure` and `flatMapFailure` to `ListenableFuture`.  These functions allow you to async transform futures from the error conditions back into results or into different error conditions.

### April 20th
5.16 was released today.  I had planned for 5.16 to be a feature expansion release.  I have been working on a new sub-pool that will help threadly's central pool.  However it's not ready yet.  Instead this release contains a bug fix for the central pool where `isolatedTask` recurring tasks could decrement the central pools size after every run, eventually resulting in logging exceptions as the pool tries to shrink itself below zero.  This critical bug fix pushed the release forward.  But I am also excited to announce a new feature in FutureUtils.  Now in addition to `scheduleWhile` there is `executeWhile`.  This is more flexible to other pool types (as it does not even require a pool, just a `ListenableFuture`).  It is conceptually the same, except where a delay for retry is not desired.

### March 6th
5.15 was released today with new features, improvements, and some small bug fixes.  All the details can be found in the <a href='https://github.com/threadly/threadly/releases/tag/release-5.15'>Release notes</a>.

### February 16th
5.14 minor release with new StringUtils functionality and javadoc improvements.

### February 4th
5.13 incremental improvements release. <a href='https://github.com/threadly/threadly/releases/tag/release-5.13'>Release notes</a> contain all the details, but this includes a variety of small incremental improvements.  Typically not enough to warrant a release, with 5.X we plan to have more small releases like this.

### January 22nd
5.12 bug fix release for unlikely, but possible, race condition when using the new ListenableFuture listener execution optimizations introduced in 5.10.

### January 17th
5.11 release to provide pre-5.10 functionality when mapping ListenableFutures as `throwMap`.  It was discovered that there is good reason to sometimes have the mapper function throw an exception, and that those should not be treated as "uncaught" exceptions.  The default behavior of `map` will still report the exception to `ExceptionUtils.handleException`, since that is the behavior most people probably expect.  But `throwMap` was added to facilitate the rare use case where you want / expect an exception to be thrown.

### January 16th
5.10 release to include more minor bug fixes, as well as the opportunity to further optimize listeners being executed on `ListenableFuture`'s.  Read more in the <a href='javadocs/5.10/org/threadly/concurrent/future/ListenableFuture.ListenerOptimizationStrategy.html'>ListenableFuture.ListenerOptimizationStrategy javadocs</a>.

### December 19th
Released version 5.7.  This is a fairly significant feature expansion release.  Allowing limiters to not be impacted by the listener (monads) execution if desired.  As well as the newly added `CentralThreadlyPool`.  Allowing the limiters to not limit listeners / map functions allows you to be sure you are limiting a core task functionality, and not also including limits towards operations which may occur after that core task completes.  The `CentralThreadlyPool` allows you to gain access to a scheduler / executor for the immediate needs, without having to worry about a scheduler life cycle (ie shutting down).  Internally this pool will try to reduce thread churn as much as possible while also making sure that the threads are available for the task demand requested (and not letting any single scheduler fully take control over the pool).  This feature has been one in the works for a while, and I am pretty happy with how it came out, so I highly encourage you to <a href="javadocs/5.7/org/threadly/concurrent/CentralThreadlyPool.html">look at it!</a>

### November 27th
Released version 5.6 which includes minor quality of life improvements as well as improvements to canceling futures from threadly monads.  As always the details are included in the <a href='https://github.com/threadly/threadly/releases/tag/release-5.6'>full release notes</a>.

### October 31st
Patch version 5.5 to address low priority tasks not completing on scheduler shutdown.  There is no javadocs for this release due to there being no API changes.

### July 22nd
Released version 5.2 that includes performance improvements in ListenableFuture/RunnableListenerHelper and ExecutorLimiter.  Changes are mostly simple, but with 5.X we plan to release more frequent but smaller releases.  Because of that we are trying to reduce some extra processes.

### July 2nd
Patch version 5.1 fixes regression in 5.0 PriorityScheduler where threads may forever go idle.  This is a regression due to an optimization when interactions with other blocking actions using LockSupport.  It is critical that all 5.0 usage is upgraded to use version 5.1 or newer.

### June 28th
After months of work, released version 5.0!  This is easily the best threadly yet.  It does require the use of java 8 and newer, but that means we are also able to take advantage of java 8 performance improvements and ergonomic improvements.  I have been hesitant to release this because there is still so much more I want to do.  Other projects like <a href="https://github.com/threadly/auroraArc">auroraArc</a> have been taking more of my time.  That said, I do plan to bring some improved documentation and benchmarks out soon.  Right now the <a href="https://github.com/threadly/threadly/wiki">wiki</a> is the best source of information, but if anyone would like to help improve this website it would be greatly appreciated!.

## Configure the sidebar

There are several products in this theme. Each product uses a different sidebar. This is the essence of what makes this theme unique -- different sidebars for different product documentation. The idea is that when users are reading documentation for a specific product, the sidebar navigation should be specific to that product. (You can read more of my thoughts on why multiple sidebars are important in this [blog post](http://idratherbewriting.com/2016/03/23/release-of-documentation-theme-for-jekyll-50/).)

The top navigation usually remains the same, because it allows users to navigate across products. But the sidebar navigation adapts to the product.

In each page's frontmatter, you must specify the sidebar you want that page to use. Here's an example of the page frontmatter showing the sidebar property:

<pre>
---
title: Alerts
tags: [formatting]
keywords: notes, tips, cautions, warnings, admonitions
last_updated: July 3, 2016
summary: "You can insert notes, tips, warnings, and important alerts in your content. These notes are stored as shortcodes made available through the linksrefs.hmtl include."
<span class="red">sidebar: mydoc_sidebar</span>
permalink: mydoc_alerts
---
</pre>

The `sidebar: mydoc_sidebar` refers to the \_data/sidebars/mydoc_sidebar.yml file.

Note that your sidebar can only have 2 levels (expand the **Tag archives** option to see an example of the second level). Given that each product has its own sidebar, this depth should be sufficient (it's really like 3 levels). Deeper nesting goes against usability recommendations.

You can optionally turn off the sidebar on any page (e.g. landing pages). To turn off the sidebar for a page, you should set the page frontmatter tag as `hide_sidebar: true`.

If you don't declare a sidebar, the `home_sidebar` file gets used as the default because this is the default specified in the config file:

```yaml
-
  scope:
    path: ""
    type: "pages"
  values:
    layout: "page"
    comments: true
    search: true
    sidebar: home_sidebar
    topnav: topnav
```

If you want to set different sidebar defaults based on different folders for your pages, specify your defaults like this:

```
-
  scope:
    path: "pages/mydoc"
    type: "pages"
  values:
    layout: "page"
    comments: true
    search: true
    sidebar: mydoc_sidebar
    topnav: topnav
```

This would load the `mydoc_sidebar` for each file in **pages/mydoc**. You could set different defaults for different path scopes.

For more detail on the sidebar, see [Sidebar navigation][mydoc_sidebar_navigation].

## Top navigation

The top navigation works just like the sidebar. You can specify which topnav data file should load by adding a `topnav` property in your page, like this:

```yaml
topnav: topnav
```

Here the topnav refers to the `_data/topnav.yml` file.

Because most topnav options will be the same, the `_config.yml` file specifies the topnav file as a default:

```yaml
-
  scope:
    path: ""
    type: "pages"
  values:
    layout: "page"
    comments: true
    search: true
    sidebar: home_sidebar
    topnav: topnav
```

## Sidebar syntax

The sidebar data file uses a specific YAML syntax that you must follow. Follow the sample pattern shown in the theme, specically looking at `mydoc_sidebar.yml` as an example: Here's a code sample showing all levels:

```yaml
entries:
- title: sidebar
  product: Jekyll Doc Theme
  version: 6.0
  folders:
  - title: Overview
    output: web, pdf
    folderitems:

    - title: Get started
      url: /index.html
      output: web, pdf
      type: homepage

    - title: Introduction
      url: /mydoc_introduction.html
      output: web, pdf

  - title: Release Notes
    output: web, pdf
    folderitems:

    - title: 6.0 Release notes
      url: /mydoc_release_notes_60.html
      output: web, pdf

    - title: 5.0 Release notes
      url: /mydoc_release_notes_50.html
      output: web, pdf

  - title: Tag archives
    output: web
    folderitems:

    - title: Tag archives overview
      url: /mydoc_tag_archives_overview.html
      output: web

      subfolders:
      - title: Tag archive pages
        output: web
        subfolderitems:

        - title: Formatting pages
          url: /tag_formatting.html
          output: web

        - title: Navigation pages
          url: /tag_navigation.html
          output: web

        - title: Content types pages
          url: /tag_content_types.html
          output: web
```

Each `folder` or `subfolder` must contain a `title` and `output` property. Each `folderitem` or `subfolderitem` must contain a `title`, `url`, and `output` property.

The two outputs available are `web` and `pdf`. (Even if you aren't publishing PDF, you still need to specify `output: web`).

The YAML syntax depends on exact spacing, so make sure you follow the pattern shown in the sample sidebars. See my [YAML tutorial](mydoc_yaml_tutorial) for more details about how YAML works.

{% include note.html content="If you have just one character of spacing off, Jekyll won't build due to the YAML syntax error. You'll see an error message in your console that says \"Error ... did not find expected key while parsing a block mapping at line 22 column 5. Error: Run jekyll build --trace for more information.\" If you encounter this, it usually refers to incorrect indentation or spacing in the YAML file. See the example mydoc_sidebar.yml file to see where your formatting went wrong." %}

Each level must have at least one topic before the next level starts. You can't have a second level that contains multiple third levels without having at least one standalone topic in the second level. If you need a hierarchy that has a folder that contains other folders and no loose topics, use a blank `-` item like this:

```yaml
entries:
- title: sidebar
  product: Jekyll Doc Theme
  version: 6.0
  folders:
  - title: Overview
    output: web, pdf
    folderitems:

    -

  - title: Release Notes
    output: web, pdf
    folderitems:

    - title: 6.0 Release notes
      url: /mydoc_release_notes_60.html
      output: web, pdf

    - title: 5.0 Release notes
      url: /mydoc_release_notes_50.html
      output: web, pdf

  - title: Installation
    output: web, pdf
    folderitems:

    - title: About Ruby, Gems, Bundler, etc.
      url: /mydoc_about_ruby_gems_etc.html
      output: web, pdf

    - title: Install Jekyll on Mac
      url: /mydoc_install_jekyll_on_mac.html
      output: web, pdf

    - title: Install Jekyll on Windows
      url: /mydoc_install_jekyll_on_windows.html
      output: web, pdf
```

To accommodate the title page and table of contents in PDF outputs, each product sidebar must list these pages before any other:

```yaml
- title:
  output: pdf
  type: frontmatter
  folderitems:
  - title:
    url: /titlepage
    output: pdf
    type: frontmatter
  - title:
    url: /tocpage
    output: pdf
    type: frontmatter
```

Leave the output as `output: pdf` for these frontmatter pages so that they don't appear in the web output.

For more detail on the sidebar, see [Sidebar navigation][mydoc_sidebar_navigation] and [YAML tutorial][mydoc_yaml_tutorial].

## Relative links and offline viewing

This theme uses relative links throughout so that you can view the site offline and not worry about which server or directory you're hosting it. It's common with tech docs to push content to an internal server for review prior to pushing the content to an external server for publication. Because of the need for seamless transferrence from one host to another, the site has to use relative links.

To view pages locally on your machine (without the Jekyll preview server), they need to have the `.html` extension. The `permalink` property in the page's frontmatter (without surrounding slashes) is what pushes the files into the root directory when the site builds.

## Page frontmatter

When you write pages, include these same frontmatter properties with each page:

```yaml
---
title: "Some title"
tags: [sample1, sample2]
keywords: keyword1, keyword2, keyword3
last_updated: Month day, year
summary: "optional summary here"
sidebar: sidebarname
permalink: filename.html
---
```

(You will customize the values for each of these properties, of course.)

For titles, surrounding the title in quotes is optional, but if you have a colon in the title, you must surround the title with quotation marks. If you have a quotation mark inside the title, escape it first with a backlash `\`.

Values for `keywords` get populated into the metadata of the page for SEO.

Values for `tags` must be defined in your \_data/tags.yml list. You also need a corresponding tag file inside the tags folder that follows the same pattern as the other tag files shown in the tags folder. (Jekyll won't auto-create these tag files.)

If you don't want the mini-TOC to show on a page (such as for the homepage or landing pages), add `toc: false` in the frontmatter.

The `permalink` value should be the same as your filename and include the ".html" file extension.

For more detail, see [Pages][mydoc_pages].

## Where to store your documentation topics

You can store your files for each product inside subfolders following the pattern shown in the theme. For example, product1, product2, etc, can be stored in their own subfolders inside the \_pages directory. Inside \_pages, you can store your topics inside sub-subfolders or sub-sub-folders to your heart's content. When Jekyll builds your site, it will pull the topics into the root directory and use the permalink for the URL.

Note that product1, product2, and mydoc are all just sample content to demonstrate how to add multiple products into the theme. You can freely delete that content.

For more information, see [Pages][mydoc_pages] and [Posts][mydoc_posts].

## Configure the top navigation

The top navigation bar's menu items are set through the \_data/topnav.yml file. Use the top navigation bar to provide links for navigating from one product to another, or to navigate to external resources.

For external URLs, use `external_url` in the item property, as shown in the example topnav.yml file. For internal links, use `url` the same was you do in the sidebar data files.

Note that the topnav has two sections: `topnav` and `topnav_dropdowns`. The topnav section contains single links, while the `topnav_dropdowns` section contains dropdown menus. The two sections are independent of each other.

## Blogs / News

For blog posts, create your markdown files in the \_posts folder following the sample formats. Post file names always begin with the date (YYYY-MM-DD-title).

The news/news.html file displays the posts, and the news_archive.html file shows a yearly history of posts. In documentation, you might use the news to highlight product features outside of your documentation, or to provide release notes and other updates.

See [Posts][mydoc_posts] for more information.
