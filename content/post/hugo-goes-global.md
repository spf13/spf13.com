---
date: 2016-10-07T10:56:02-04:00
description: ""
tags:
- go
- development
- hugo
title: Hugo goes global
topics:
- Development
- golang
---

Hugo is going Global! Hugo 0.17, released today, is our best and fastest
release ever! **Hugo 0.17 is nearly twice as fast as Hugo 0.16** and adds
**full support for multilingual websites** with i18n support throughout all
of Hugo.

<!--more-->

Hugo is going global with our 0.17 release. We put a lot of thought into
how we could extend Hugo to support multilingual websites with the most
simple and elegant experience. Hugo’s multilingual capabilities rival
the best web and documentation software, but Hugo’s experience is
unmatched. If you have a single language website, the simple Hugo
experience you already love is unchanged. Adding additional languages to
your website is simple and straightforward. Hugo has been completely
internally rewritten to be multilingual aware with translation and
internationalization features embedded throughout Hugo.

Hugo continues its trend of each release being faster than the last.
It’s quite a challenge to consistently add significant new functionality
and simultaneously dramatically improve performance.
[@bep](//github.com/bep) has made it his personal mission to apply the
Go mantra of “Enable more. Do less” to Hugo. Hugo’s consistent
improvement is a testament to his brilliance and his dedication to his
craft. Hugo is further benefited from the performance improvements from
the Go team in the Go 1.7 release.

This release represents **over 300 contributions by over 70
contributors** to the main Hugo code base. Since last release Hugo has
**gained 2000 stars, 50 new contributors and 20 additional themes.**

Hugo now has:

*   12,000 stars on GitHub
*   370+ contributors
*   110+ themes  

[@bep](//github.com/bep) continues to lead the project with the
lionshare of contributions and reviews. A special thanks to
[@bep](//github.com/bep) and [@abourget](//github.com/abourget) for
their considerable work on multilingual support.

A big welcome to newcomers
[@MarkDBlackwell](//github.com/MarkDBlackwell) ,
[@bogem](//github.com/bogem) and [@g3wanghc](//github.com/g3wanghc) for
their critical contributions.

### Highlights

**Multilingual Support:** Hugo now supports multiple languages
side-by-side. A single site can now have multiple languages rendered
with full support for translation and i18n.

**Performance:** Hugo is faster than ever! Hugo 0.17 is not only our
fastest release, it’s also the most efficient. Hugo 0.17 is **nearly
twice as fast as Hugo 0.16** and uses about 10% less memory. This means
that the same site will build in nearly half the time it took with Hugo
0.16. For the first time Hugo sites are averaging well under 1ms per
rendered content.

**Docs overhaul:** This release really focused on improving the
documentation. [Gohugo.io](http://gohugo.io) is more accurate and
complete than ever.

**Support for Mac OS Sierra**

### New Features

*   Multilingual support [#2303](//github.com/spf13/hugo/issues/2303)
*   Allow content expiration [#2137](//github.com/spf13/hugo/issues/2137)
*   New templates functions:
    *   `querify` function to generate query strings inside templates [#2257](//github.com/spf13/hugo/issues/2257)
    *   `htmlEscape` and `htmlUnescape` template functions [#2287](//github.com/spf13/hugo/issues/2287)
    *   `time` converts a timestamp string into a time.Time structure [#2329](//github.com/spf13/hugo/issues/2329)

### Enhancements

*   Render the shortcodes as late as possible [ed0985](//github.com/spf13/hugo/commit/ed0985404db4630d1b9d3ad0b7e41fb186ae0112)
*   Remove unneeded casts in page.getParam [#2186](//github.com/spf13/hugo/issues/2186)
*   Automatic page date fallback [#2239](//github.com/spf13/hugo/issues/2239)
*   Enable safeHTMLAttr [#2234](//github.com/spf13/hugo/issues/2234)
*   Add TODO list support for markdown [#2296](//github.com/spf13/hugo/issues/2296)
*   Make absURL and relURL accept any type [#2352](//github.com/spf13/hugo/issues/2352)
*   Suppress ‘missing static’ error [#2344](//github.com/spf13/hugo/issues/2344)
*   Make summary, wordcount etc. more efficient [#2378](//github.com/spf13/hugo/issues/2378)
*   Better error reporting in `hugo convert` [#2440](//github.com/spf13/hugo/issues/2440)
*   Reproducible builds thanks to govendor [#2461](//github.com/spf13/hugo/issues/2461)

### Fixes

*   Fix shortcode in markdown headers [#2210](//github.com/spf13/hugo/issues/2210)
*   Explicitly bind livereload to hugo server port [#2205](//github.com/spf13/hugo/issues/2205)
*   Fix Emojify for certain text patterns [#2198](//github.com/spf13/hugo/issues/2198)
*   Normalize file name to NFC [#2259](//github.com/spf13/hugo/issues/2259)
*   Ignore emacs temp files [#2266](//github.com/spf13/hugo/issues/2266)
*   Handle symlink change event [#2273](//github.com/spf13/hugo/issues/2273)
*   Fix panic when using URLize [#2274](//github.com/spf13/hugo/issues/2274)
*   `hugo import jekyll`: Fixed target path location check [#2293](//github.com/spf13/hugo/issues/2293)
*   Return all errors from casting in templates [#2356](//github.com/spf13/hugo/issues/2356)
*   Fix paginator counter on x86-32 [#2420](//github.com/spf13/hugo/issues/2420)
*   Fix half-broken self-closing shortcodes [#2499](//github.com/spf13/hugo/issues/2499)

