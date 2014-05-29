---
Description: This tutorial given at OSCON 2012  will introduce the features of MongoDB
  by building a simple location-based application using MongoDB.
Keywords:
- MongoDB
- Presentations
- mongodb
- Ruby
Section: presentation
Slug: building-your-first-mongodb-app-oscon-2012
Tags:
- mongodb
- Ruby
Thumbnail: /images/1836_MongoDB-at-oscon-2012.png-200x200.png
Title: Building your first MongoDB app - OSCON 2012
Topics:
- MongoDB
- Presentations
Url: presentation/building-your-first-mongodb-app-oscon-2012
date: 2012-07-24
disqus_identifier: 1816 http://spf13.com/?p=1816
disqus_title: Building your first MongoDB app &#8211; OSCON 2012
disqus_url: http://spf13.com/post/building-your-first-mongodb-app-oscon-2012/
---

{{% img src="/media/MongoDB-at-oscon-2012.png" %}}

This is a 3 hour tutorial I wrote for and gave at OSCON 2012.

Here is the summary:

This tutorial will introduce the features of
[MongoDB](http://www.mongodb.org/ "MongoDB") by building a simple
location-based application using MongoDB. The tutorial will cover the
basics of MongoDB’s document model, query language, map-reduce framework
and deployment architecture.

The tutorial will be divided into 5 sections:

-   Data modeling with MongoDB: documents, collections and databases
-   Querying your data: simple queries, geospatial queries, and
    text-searching
-   Writes and updates: using MongoDB’s atomic update modifiers
-   Trending and analytics: Using mapreduce and MongoDB’s aggregation
    framework
-   Deploying the sample application

Besides the knowledge to start building their own applications with
MongoDB, attendees will finish the session with a working application
they use to check into locations around Portland from any HTML5 enabled
phone!

**TUTORIAL PREREQUISITES**<br>
 Each attendee should have a running version of MongoDB. Preferably the
latest unstable release 2.1.x, but any install after 2.0 should be fine.
You can dowload MongoDB
at [http://www.mongodb.org/downloads](http://www.mongodb.org/downloads).

Instructions for installing MongoDB are
at [http://docs.mongodb.org/manual/installation/](http://docs.mongodb.org/manual/installation/).

Additionally we will be building an app in Ruby. Ruby 1.9.3+ is required
for this. The current latest version of ruby is 1.9.3-p194.

-   For windows download
    the [http://rubyinstaller.org/](http://rubyinstaller.org/)
-   For OSX download [http://unfiniti.com/software/mac/jewelrybox/](http://unfiniti.com/software/mac/jewelrybox/)
-   For linux most users should know how to for their own distributions.

We will be using the following GEMs and they **MUST BE** installed ahead
of time so you can be ahead of the game and safe in the event that the
Internet isn’t accommodating.

-   bson (1.6.4)
-   bson\_ext (1.6.4)
-   haml (3.1.4)
-   mongo (1.6.4)
-   rack (1.4.1)
-   rack-protection (1.2.0)
-   rack shotgun (0.9)
-   sinatra (1.3.2)
-   tilt (1.3.3)

Prior ruby experience isn’t required for this. We will NOT be using
rails for this app.

{{% slideshare 13658354 %}}

**[OSCON 2012 MongoDB
Tutorial](http://www.slideshare.net/spf13/oscon-2012 "OSCON 2012 MongoDB Tutorial")**
from **[Steve Francia](http://www.slideshare.net/spf13)**

## Related articles

-   [Big Data for the rest of us at NYC Strata
    2012](http://spf13.com/post/big-data-for-the-rest-of-us-at-nyc-strata-2012/)
-   [How I gave the most viewed presentation in the history of
    OSCON](http://spf13.com/post/how-i-gave-the-most-viewed-presentation-in-the-history-of-oscon/)
-   [Optimizing MongoDB Compound
    Indexes](http://emptysquare.net/blog/optimizing-mongodb-compound-indexes/)
-   [New features in the driver for MongoDB
    2.2](http://christiankvalheim.com/post/29753345741/new-features-in-the-driver-for-mongodb-2-2)

