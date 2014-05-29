---
Description: A round up of projects created during the driver days hack day by the
  10gen drivers team focused on the MongoDB user experience.
Keywords:
- Development
- MongoDB
- Personal
- 10gen
- Driver Team
- github
- Hack
- Hack Day
- mongodb
- Thon
Section: post
Slug: 10gen-driver-days-mongodb-hack-a-thon
Tags:
- 10gen
- Driver Team
- Drivers
- github
- Hack
- Hack Day
- mongodb
- Thon
Thumbnail: /images/1916_try-aggro-1.png-200x200.png
Title: MongoDB Driver days hackathon round up
Topics:
- Development
- MongoDB
- Personal
date: 2012-11-16
disqus_identifier: 1912 http://spf13.com/?p=1912
disqus_title: MongoDB Driver days hackathon round up
disqus_url: http://spf13.com/post/10gen-driver-days-mongodb-hack-a-thon/
---

Two times a year the drivers team at 10gen gathers together for a face
to face meeting to spend time together working on issues and setting
forth our goals for the upcoming six months. In September 2012 we all
converged on New York City for the second ever driver days. This time we
split up into teams for a hack-a-thon. As maintainers of drivers &
integrations in over a dozen different languages while we are on the
same team, it isn’t often that we actually work together on the same
codebase. The hack-a-thon gave us a chance to do just that. We split up
into 5 teams each having members from different languages. Without
further ado, here is what we came up with.

*Disclaimer.. Each project currently represents exactly one evenings
worth of work. Our intent is to pick the best project or two, polish
them up and move them to the [10gen Labs](https://github.com/10gen-labs)
account on github.*

As with all things open source, contributions welcome.

Mongo Contributor Hub
---------------------

![](/media/mongodb-gh-projects.png "mongodb-gh-projects")

Ever wonder what type of open source MongoDB related projects are being
developed these days? We did. So we hacked together a quick Github
search & explore interface for any project Github reports as associated
to MongoDB! Projects are organized by language, fully searchable and
sorted by followers and forks. Built with Nodejs, Express and MongoDB.


[https://github.com/TylerBrock/mongo-contributor-hub](https://github.com/TylerBrock/mongo-contributor-hub)

Try Aggro
---------

![](/media/try-aggro-1.png "try-aggro-1")

With thirteen challenging questions you’ll learn the ins and outs of
aggregation with MongoDB. Will you be able to complete all the
challenges and become an aggregation master?

[https://github.com/rozza/try-aggro](https://github.com/rozza/try-aggro)

MongoDB.OData
-------------

![](/media/MongoDB.OData.png "MongoDB.OData")

OData is a highly used protocol with clients in .NET, Java, jquery, and
many more. It makes sense to be able to support these clients with a
MongoDB backend. With OData v3, the protocol is now rich enough to
support the rich document model MongoDB already provides. MongoDB.OData
let’s you expose your entites (MongoDB documents), complex types
(MongoDB embedded documents), and collections (MongoDB arrays) via OData
and includes full support for queries and OData service operations.
Support for updating is almost ready.

[https://github.com/craiggwilson/mongo-dotnet-odata](https://github.com/craiggwilson/mongo-dotnet-odata)

Slow Query Profiler
-------------------

![](/media/pXLc4.png "pXLc4")

Logging slow queries is essential for any database application, and
MongoDB makes doing so relatively painless with its database profiler.
Unfortunately, making sense of the system.profile collection and tying
its contents back to your application requires a bit more effort. The
heart of mongoqp [Mongo Query
Profiler](https://github.com/jmikola/mongoqp) is a bit of map/reduce JS
that aggregates those queries by their BSON skeleton (i.e. keys
preserved, but values removed). With queries reduced to their bare
structure, any of their statistics can be aggregated, such as average
query time, index scans, counts, etc.

As big fans of [Genghis](http://genghisapp.com), a single-file MongoDB
admin app, the initial intent was to contribute a new UI with the
profiler results, but one night was not enough time to wrap our heads
around Backbone.js and develop the query aggregation. Instead, we
whipped up a quick frontend using the [Silex](http://silex-project.org)
PHP micro-framework. With the hack day deadline no longer looming, there
should be plenty of time to get this functionality ported over to
Genghis. Additionally, the map/reduce JS may also show up in Tyler
Brock’s [mongo-hacker](https://github.com/TylerBrock/mongo-hacker) shell
enhancement package.

While presenting mongoqp to our co-workers, we learned about [Dan
Crosta’s professor](https://github.com/dcrosta/professor), which already
provides many of the features we hoped to implement, such as incremental
data collection. We think there is still a benefit to developing the JS
innards of mongoqp and getting its functionality ported over to other
projects, but I would definitely encourage you to check out professor if
you’d like a stand-alone query profile viewer.

[https://github.com/jmikola/mongoqp](https://github.com/jmikola/mongoqp)

Aggregation Pipeline Web Interface
----------------------------------

![](/media/Screen-Shot-2012-10-01-at-3.20.19-PM.png "Screen Shot 2012-10-01 at 3.20.19 PM")

We built a web app for the new aggregation framework. It allows you to
create pipelines using a web interface, making it easy for a user to
play around with the new framework without having to use the command
syntax. Users can incrementally add pipeline operators to test running
aggregations with different operators, and can use the easy interface as
an educational tool to learn how the pipelines work. The app also allows
you to pipe the results of aggregation framework jobs straight to
user-defined output collections and see a history of past jobs along
with their run-time. The app is built in Ruby on Rails, using the
MongoMapper ODM.

[https://github.com/estolfo/aggre-great](https://github.com/estolfo/aggre-great)
