---
Description: Symfony2 is the latest brainchild of Fabien Potencier. Essentially he
  took the excellent advancements brought by PHP 5.3 and combined all the learnings
  he took away from building Symfony2 as well as established design patterns and best
  practices often from the Java world and created a modern web framework. Fully utilizing
  things like namespaces, closures and late static binding Symfony2 is an extremely
  full featured, modular, and crazy fast framework.
Keywords:
- Development
- php
- development
- Framework
- PHP
- Symfony2
Section: post
Slug: symfony2
Tags:
- development
- Framework
- PHP
- Symfony2
Thumbnail: /images/1243_symfony-logo.jpg-200x200.jpg
Title: On Symfony2
Topics:
- Development
- php
Url: post/symfony2
date: 2011-02-01
disqus_identifier: 1235 http://spf13.com/?p=1235
disqus_title: On Symfony2
disqus_url: http://spf13.com/post/symfony2/
---

{{% img src="/media/symfony_ss.png" alt="symfony" %}}

### Disclaimer

*I’ve got a couple disclaimers in writing this. 1. I’m one of the
primary authors of the [Zoop Framework for
PHP](http://zoopframework.com). It’s pretty much the first web framework
for PHP dating back to 2001. In spite of it’s age it’s still quite
relevant and in use by thousands worldwide. 2. I run engineering for
[OpenSky](http://shopopensky.com) where we elected to build our
ecommerce platform on the [Symfony2
framework](http://symfony-reloaded.org) and have since become the 2nd
largest contributors to it. You may wonder why given my background I
chose to use a different framework. This post should answer that well…*

Introduction to Symfony2
------------------------

### Related Posts

-   [Next Gen PHP
    Frameworks](http://spf13.com/post/next-gen-php-frameworks/)
-   [Getting Started with
    Symfony2](http://spf13.com/post/getting-started-with-symfony2/)
-   [Creating your own Symfony2
    Bundle](http://spf13.com/post/creating-your-own-symfony2-bundle/)
-   [Creating a Symfony2 Console
    Command](http://spf13.com/post/creating-a-symfony2-console-command/)

Symfony2 is the latest brainchild of Fabien Potencier. Essentially he
took the excellent advancements brought by PHP 5.3 and combined all the
learnings he took away from building Symfony as well as established
design patterns and best practices often from the Java world and created
a modern web framework. Fully utilizing things like namespaces, closures
and late static binding, Symfony2 is an extremely full featured,
modular, and crazy fast framework.

Why Symfony2?
=============

Symfony2 has a lot going for it. I’m going to highlight some of what I
consider some of the most impressive features, but recognize it goes
quite a bit deeper than what I’ll cover.

Highly Customizable
-------------------

Symfony2 brings new definition to the word customizable. As Fabien
writes

> Symfony2 is probably one of the most flexible PHP frameworks ever
> created. You can literally change everything. To allow such a level of
> customization and still keep things simple for the developer, Symfony2
> relies on well-know design patterns, and best practices coming from
> the Java world. Of course, we have adapted those techniques to the PHP
> way of doing things, and the result is amazingly powerful.

Really everything about the framework can be configured and changed. It
makes no decisions on what you should use or how you should do it. Even
the configuration is configurable allowing you to choose from XML, YAML,
PHP or any combination of the three.

Blazing Fast
------------

At OpenSky our standard is that every single page on our website needs
to load in under 200 ms. With Symfony2 many pages load in 1/10 that.
Symfony2 uses intelligent caching to eliminate the need for most parsing
resulting in an extremely fast and efficient framework. Symfony2
performed their own benchmarks it what appears to be a fairly honest and
impartial way and found that Symfony2 is a magnitude faster than pretty
much every other framework out there. See
[http://symfony-reloaded.org/fast](http://symfony-reloaded.org/fast).

On a personal note, they didn’t evaluate Zoop, but in my performing
similar benchmarks with Zoop my findings were similar across the
frameworks. Zend and Cake are slow dogs and really shouldn’t be used,
Symfony and Solar were in the middle of the pack and Zoop and CI were
the quickest.

That said, just about every framework (except Zend and Cake) can perform
well in an isolated test, the real challenge is with a full fledged
application with loads of files, routes and configurations. As one who
has a Symfony2 based application in production with many tens of
thousands of lines of code Symfony2 handles it like a champ. No real
measurable degredation because of application size.

Modular and compatible with everything
--------------------------------------

Symfony2 is the most modular framework I’ve ever seen. Symfony2 calls a
module a bundle as Fabien explains:

> A bundle is a structured set of files that implements a single feature
> and can be easily shared with other developers. In Symfony2,
> everything is a bundle, from the application you develop, to the
> features provided by the framework itself. Bundles easily hook into
> the configuration system to give to the developer a clean way to
> semantically configure and customize them.

So in Symfony2 everything is a first class citizen. All core bundles are
treated the exact same as your bundles and everything is a bundle.
Bundles are easily portable and configurable. They are really the key to
Symfony2’s real power. A bundle can extend another bundle. It can be
distributed independently from it’s application. Just checkout
[http://symfony2bundles.org](http://symfony2bundles.org) to see all the
great bundles already written for Symfony2 (and it hasn’t even been
released yet). Want to integrate with Twitter, include the bundle. Want
to incorporate a forum, include the bundle.

Symfony2 also easily works with many 3rd party libraries. All that is
required is a simple bundle to provide an interface between Symfony2 and
the library. Symfony2 is Symfony2 comes with support for Doctrine, a
number of Zend classes, and …..

Very Testable
-------------

Symfony2 is built with testing in mind from the ground up. Due to it’s
lightweight and robust Dependency Injection Container, which was
inspired by the Spring one, virtually everything in Symfony2 is
testable. PHP Unit is fully supported as are many different approaches
including mocking, stubbing, unit and functional tests. Symfony2
provides it’s own library for functional tests where it can simulate
requests and test output without the browser.

Symfony2 also provides four different environments so that it can be
fully used within the dev, test, staging, production lifecycle.

Engineering Excellence
----------------------

As the framework is the foundation it’s critical that it is engineered
properly, efficiently and bug free. Symfony2 is extremely well written
code. Speaking from experience in developing a framework, there are some
rather challenging pieces to get right (eg CLI, modularity, efficient
routing). Fabien and friends have done an amazing job in writing a well
crafted framework suitable for building anything on. In spite of being
inspired by a number of java patterns, it’s a PHP framework. Other’s
have tried building a java framework in PHP with rather poor results
(Zend ahem).

Useful Tools
------------

Symfony2 provides a set of extremely useful tools. The Web Debug toolbar
and profiler simplify development and give real time feedback on how
well your application is performing. The CLI integration is second to
none. It’s rather easy to develop your own console commands for just
about anything in Symfony2. Read more about these tools for yourself
[http://symfony-reloaded.org/tools](http://symfony-reloaded.org/tools)

What doesn’t work… yet
======================

It can’t all be good, right? So here’s the list of things that aren’t
working well in Symfony2. I say yet, as I believe that all will be
addressed in time. It’s a rather young framework and still pre-release.

Too customizable
----------------

Probably my biggest complaint is that there are literally dozens of ways
to do anything. It’s also unclear what the best practices are so it’s
even harder to know if you are doing something the right way. This
either makes for a very scattered application or for a development team
to establish clear standards for their application. My approach here has
always been one of extreme customizability but with sane defaults. I
feel that this is the best of both worlds as you can change anything you
want, but don’t need to, things just work the way you’d expect them to.
Symfony2’s approach is everything needs to be explicitly defined,
resulting in the next criticism…

Lots of Typing
--------------

The Symfony2 team is taking the right approach. Get the foundation
perfect before moving up to making things automated and easier for the
developer. As it is now though, there’s lots of tedious work. Loads of
typing to do even simple things. I know there are efforts to build
scaffolding and other automations, but as it stands now, be ready to
type a lot. This dovetails into my first criticism well as without sane
defaults it’s rather hard to build scaffolding etc. This also isn’t to
say that there isn’t some of this.. for instance there’s a great console
command for initializing a bundle and another for bootstrapping an
application, but it’s pretty limited now.

Work in Progress
----------------

Symfony2 is slated for release in March 2011.. in two months. So all the
things that come with a pre-release piece of software come along with
it. This means this is beta code, the API isn’t fixed yet and changes
pretty frequently. At OpenSky we dedicate time to catching up to HEAD
every week or two. Additionally the approach to bundles will make an
amazing pool of includable community modules to facilitate rapid
building. However these are in their infancy. There are handful of them
and some of excellent quality, but with a frequently changing API, not
all are up to date. It’s reasonable to assume that once released, this
will be an amazing resource, but until then it just hints of one.

[Get Started with Symfony2](http://symfony.com)

Check out my follow up article..[Getting Started with
Symfony2](http://spf13.com/post/getting-started-with-symfony2 "Getting Started with Symfony2").

Agree / Disagree? Share your experiences in the comments below.
