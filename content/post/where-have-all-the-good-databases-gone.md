---
Description: ""
Keywords:
- MongoDB
- Scalability
- Systems
- Database
- mongodb
- nosql
Section: post
Slug: where-have-all-the-good-databases-gone
Tags:
- Database
- mongodb
- nosql
Thumbnail: /images/1082_mongodb-sq.png-200x200.png
Title: Where have all the good databases gone?
Topics:
- MongoDB
- Scalability
- Systems
Url: post/where-have-all-the-good-databases-gone
date: 2011-07-13
disqus_identifier: 1471 http://spf13.com/?p=1471
disqus_title: Where have all the good databases gone?
disqus_url: http://spf13.com/post/where-have-all-the-good-databases-gone/
---

{{% img src="/media/mongodb-sq.png" class="third right" alt="mongodb" %}}

Perhaps you’ll recognize these words, “About five years ago I started to
notice an odd thing. The products that the database vendors were
building had less and less to do with what the customers wanted. … So,
what is this growing disconnect?” Those words were [written in 2004 by
Adam
Bosworth](http://adambosworth.wordpress.com/2004/12/29/where-have-all-the-good-databases-gone/),
a veteren of Microsoft, Google and BEA. In the 7 years since things have
only gotten worse. Open source products came to maturity (if you can
call it that), but none improved on any of the challenges Bosworth
outlines. He points out 3 things that everyone wants in a database, but
nobody is providing.. well nobody except
[MongoDB](http://www.mongodb.org/ "MongoDB").

# 1. Dynamic Schema

He writes:

> Dynamic schema so that as the business model/description of goods or
> services changes and evolves, this evolution can be handled seamlessly
> in a system running 24 by 7, 365 days a year. This means that Amazon
> can track new things about new goods without changing the running
> system. It means that Federal Express can add Federal Express Ground
> seamlessly to their running tracking system and so on. In short, the
> database should handle unlimited change.

Mongo with it’s document design handles this elegantly and gracefully.
We’ve made loads of changes to our database without even needing to
worry about migrations. The responsibility to maintain changes falls on
the application and isn’t a constrained by the database.

# 2. Dynamic Partitioning

He Writes:

> Dynamic partitioning of data across large dynamic numbers of machines.
> … The only issue is that it needs to be dynamic so that as items are
> added or get “busy” the system dynamically load balances their data
> across the machines. In short, the database should handle unlimited
> scale with very low latency. It can do this because the vast majority
> of queries will be local to a product or a customer or something over
> which you can partion.

Mongo has solved this as well with it’s automatic sharding. It runs
pretty much exactly as he requests. Mongo automatically distributes data
among shards and balances them dynamically.

# 3. Modern Indexing

He Writes:

> Google has spoiled the world. Everyone has learned that just typing in
> a few words should show the relevant results in a couple of hundred
> milliseconds.

He is a bit vague on what he means here, so taken one way, everyone has
solved this, but then again if taken that way, it was solved long before
2004 when this was written. I’m going to take it to mean real indexing
across highly distributed data stores. So you can find a set of data
across many nodes all extremely quickly. I’d like to add this to
automatic indexing. There is no reason not to do this using a similar
approach to how mongo tackled sharding. Again as he ins’t clear on what
he is asking for it’s not clear if MongoDB has solved it or not. I think
with their map reduce framework and the ability to create combined
indexes on rich structured documents I think they are heading in the
right direction, but I don’t think they’ve quite solved this yet.

## Related articles

-   [Craigslist Adopting
    MongoDB](http://www.readwriteweb.com/cloud/2011/05/craigslist-adopting-mongodb.php)
    (readwriteweb.com)
-   [MongoDB Competes on Speed and
    Flexibility](http://www.pcworld.com/article/229844/mongodb_competes_on_speed_and_flexibility.html)
    (pcworld.com)
-   [Ten things I didn’t know about
    MongoDB](http://slowping.com/2011/ten-things-i-didnt-know-about-mongodb/)
    (slowping.com)
-   [Blending Mongo and RDBMS for
    ecommerce](http://spf13.com/post/blending-mongo-and-rdbms-for-ecommerce)
    (spf13.com)

