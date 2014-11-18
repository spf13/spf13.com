---
date: 2014-10-02T13:28:42-04:00
description: ""
tags:
- go
- development
- hugo
- community
title: Hugo Summer 2014 Update
topics:
- Development
- golang
---

Hugo, the fast and flexible static site generator, is really coming of
age. I wanted to give a quick update about the progress Hugo has been
making over the past couple months.

New Website
===========

Hugo can now be found at http://gohugo.io. Update your bookmarks.

New Team Members
================

I want to formally welcome our newest team members.

[Tatsushi Demachi](https://github.com/tatsushid) has been making
excellent contributions hugo, particularly with extensions to the
template capabilities. The two biggest additions to the layouts, where and
groupBy both came from him.

[Anthony Fok](https://github.com/anthonyfok) is on a mission to improve
the Hugo documentation. He’s making improvements across the entire
documentation and we all benefit from his efforts.

[Nate Finch](http://npf.io/) has joined and injected some much needed
support. He’s been helping everywhere, from code contributions, to
supporting developers to setting up our new discussion forum (see
below).

Hugo doesn’t have a official “team”. We welcome contributions from
everyone and have received contributions by over 90 people so far. If
anyone is interested in helping out, please do. Once you’ve made a few
contributions ask for contributor access. Currently Nate and Steve
manage this.

New Discussion Forum
====================

Hugo has a brand [new discussion forum](http://discuss.gohugo.io). It
became apparent to me that google groups was no longer serving our
growing community. We really needed a discussion forum that had a great
web experience as well as the ability to continue with the email only
interface. I also wanted the ability to easily categorize things into
different channels. Lastly I didn’t want people to need to setup new
accounts. We decided to go with [Discourse](http://www.discourse.org/),
an open source modern discussion platform. It provided all the features
we needed and has been great for our community. We soft launched it and
within two weeks the amount of discussions being had has risen
significantly. Most importantly, users are helping other users.


Nate contributed a lot of work setting it all up. He wrote up his
experience on his blog at [deploy discourse with
juju](http://npf.io/2014/10/deploy-discourse-juju/).


v0.12 Release
===============

A lot has happened since Hugo v0.11.0 was released. Most of the work has been
focused on polishing the theme engine and adding critical functionality to the
templates.

This release represents over 90 code commits from 28 different contributors.

  * 10 [new themes](https://github.com/spf13/hugothemes) created by the community
  * fully themable [partials](http://hugo.spf13.com/templates/partials)
  * [404 template](http://hugo.spf13.com/templates/404/) support in themes
  * [shortcode](http://hugo.spf13.com/extras/shortcodes/) support in themes
  * [views](http://hugo.spf13.com/templates/views/) support in themes
  * inner [shortcode](http://hugo.spf13.com/extras/shortcodes/) content now treated as markdown
  * support for header ids in markdown (# header {#myid})
  * [where](http://hugo.spf13.com/templates/list) template function to filter lists of content, taxonomies, etc
  * [groupby](http://hugo.spf13.com/templates/list) & [groupbydate](/templates/list) methods to group pages
  * taxonomy [pages list](http://hugo.spf13.com/taxonomies/methods/) now sortable, filterable, limitable & groupable
  * general cleanup to taxonomies & documentation to make it more clear and consistent
  * [showcase](http://hugo.spf13.com/showcase/) returned and has been expanded
  * pretty links now always have trailing slashes
  * [baseurl](http://hugo.spf13.com/overview/configuration/) can now include a subdirectory
  * better feedback about draft & future post rendering
  * a variety of improvements to [the website](http://gohugo.io)


What’s next?
============

The community is really expanding. Alongside the new discussion forum we
are also launching a hugo blog where updates like this will reside in
the future.

We will also be launching a theme gallery where users can view the
various themes available for Hugo.

We’re focused on the v0.13 release. There’s a lot to look forward to in
this release. Check the [v0.13 Milestone](https://github.com/spf13/hugo/issues?q=is%3Aopen+is%3Aissue+milestone%3Av0.13) for which tickets we are working on.
