{
	"disqus_url" : "http://spf13.com/post/mongodb-hadoop-humongous-data-mongosv-2012/",
	"disqus_identifier" : "1934 http://spf13.com/?p=1934",
	"disqus_title" : "MongoDB, Hadoop and humongous data at MongoSV 2012",
	"Title": "MongoDB, Hadoop and humongous data at MongoSV 2012",
	"Description": "Presentation given at MongoSV 2012 on processing big data with MongoDB using Hadoop integration & the MongoDB aggregation framework.",
	"Keywords": [
		"MongoDB",
		"Presentations",
		"Apache Hadoop",
		"big data",
		"Data Processing",
		"Data Tools",
		"Distributed Data Processing",
		"hadoop",
		"mapreduce",
		"mongodb"
	],
	"Tags": [
		"Apache Hadoop",
		"big data",
		"Data Processing",
		"Data Tools",
		"Distributed Data Processing",
		"hadoop",
		"mapreduce",
		"mongodb"
	],
	"Pubdate": "2012-12-06",
	"Topics": [
		"MongoDB",
		"Presentations"
	],
	"Url": "presentation/mongodb-hadoop-humongous-data-mongosv-2012",
	"Slug": "mongodb-hadoop-humongous-data-mongosv-2012",
	"Section": "presentation",
	"Thumbnail": ""
}
This presentation given at MongoSV 2012 focuses on data processing when
using [MongoDB](http://www.mongodb.org/ "MongoDB") as your primary
database including integration with
[Hadoop](http://hadoop.apache.org/ "Hadoop") & the new MongoDB
aggregation framework. Learn how to integrate MongoDB with Hadoop for
large-scale distributed data processing. Using tools like MapReduce, Pig
and Streaming you will learn how to do analytics and ETL on large
datasets with the ability to load and save data against MongoDB. With
Hadoop MapReduce, Java and Scala programmers will find a native solution
for using MapReduce to process their data with MongoDB. Programmers of
all kinds will find a new way to work with ETL using Pig to extract and
analyze large datasets and persist the results to MongoDB. Python and
Ruby Programmers can rejoice as well in a new way to write native Mongo
MapReduce using the Hadoop Streaming interfaces.

{{% slideshare 15509900 %}}

**[MongoDB, Hadoop and humongous data – MongoSV
2012](http://www.slideshare.net/spf13/mongodb-hadoop-and-humongous-data-mongosv-2012 "MongoDB, Hadoop and humongous data - MongoSV 2012")**
from **[Steve Francia](http://www.slideshare.net/spf13)**

MongoDB, Hadoop and humongous data – MongoSV 2012 — Presentation Transcript
---------------------------------------------------------------------------

-   1. MongoDB, Hadoop & humongous data
-   2. Talking about. What is Humongous Data. Humongous Data & You.
    MongoDB & Data processing. Future of Humongous Data
-   3. @spf13 AKA Steve Francia. 15+ years building the internet.
    Father, husband, skateboarder. Chief Solutions Architect @ 10gen
    responsible for drivers, integrations, web & docs
-   4. What is humongous data ?
-   5. 2000 Google Inc. Today announced it has released the largest
    search engine on the Internet.Google’s new index, comprisingmore
    than 1 billion URLs
-   6. 2008 Our indexing system for processing links indicates that we
    now count 1 trillion unique URLs (and the number of individual
    webpages out there is growing by several billion pages per day).
-   7. An unprecedented amount of data is being created and isaccessible
-   8. Data Growth 1,0001000 750 500 500 250 250 120 55 4 10 24 1 0 2000
    2001 2002 2003 2004 2005 2006 2007 2008 Millions of URLs
-   9. Truly Exponential Growth Is hard for people to grasp A BBC
    reporter recently: “Your current PCis more powerful than the
    computer they had on board the ﬁrst ﬂight to the moon”.
-   10. Moore’s Law Applies to more than just CPUs Boiled down it is
    that things double at regular intervals. It’s exponential growth..
    and applies to big data
-   11. How BIG is it?
-   12. How BIG is it?2008
-   13. How BIG is it? 20072008 2005 2006 2003 2004 2001 2002
-   14. Why all this talk about BIG Data now?
-   15. In the past few years open source software emerged enabling ‘us’
    to handle BIG Data
-   16. The Big Data Story
-   17. Is actually two stories
-   18. Doers & Tellers talking about different things
    http://www.slideshare.net/siliconangle/trendconnect-big-data-report-september
-   19. Tellers
-   20. Doers
-   21. Doers talk a lot more about actual solutions
-   22. They know it’s a two sided story Storage Processing
-   23. Take aways MongoDB and Hadoop MongoDB for storage & operations
    Hadoop for processing & analytics
-   24. MongoDB & Data Processing
-   25. Applications have complex needs. MongoDB ideal operational
    database MongoDB ideal for BIG data. Not a data processing engine,
    but provides processing functionality
-   26. Many options for Processing Data • Process in MongoDB using Map
    Reduce • Process in MongoDB using Aggregation Framework • Process
    outside MongoDB (using Hadoop)
-   27. MongoDB Map Reduce Map() MongoDB Data Group(k) emit(k,v) map
    iterates on documents Document is \$this Sort(k) 1 at time per shard
    Reduce(k,values) k,v Finalize(k,v) Input matches output k,v Can run
    multiple times
-   28. MongoDB Map Reduce MongoDB map reduce quite capable… but with
    limits- Javascript not best language for processing map reduce-
    Javascript limited in external data processing libraries- Adds load
    to data store
-   29. MongoDB Aggregation Most uses of MongoDB Map Reduce were for
    aggregationAggregation Framework optimized for aggregate
    queriesRealtime aggregation similar to SQL GroupBy
-   30. MongoDB & Hadoop same as Mongos Many map operationsMongoDB shard
    chunks (64mb) 1 at time per input split Creates a list each split
    Map (k1,1v1,1ctx) Runs on same of Input Splits Map (k ,1v ,1ctx)
    thread as map each split Map (k , v , ctx)single server orsharded
    cluster (InputFormat) each split ctx.write(k2,v2)2 ctx.write(k2,v )2
    Combiner(k2,values2)2 RecordReader ctx.write(k2,v )
    Combiner(k2,values )2 Combiner(k2,values ) k2, 2v3 3 k , 2v 3 k ,v
    Partitioner(k2)2 Partitioner(k )2 Partitioner(k ) Sort(keys2)
    Sort(k2)2 Sort(k )MongoDB Reducer threads Reduce(k2,values3) Output
    Format Runs once per key kf,vf
-   31. DEMOTIME
-   32. DEMO Install Hadoop MongoDB Plugin Import tweets from twitter
    Write mapper in Python using Hadoop streamingWrite reducer in Python
    using Hadoop streaming Call myself a data scientist
-   33. Installing Mongo-hadoop
    https://gist.github.com/1887726hadoop\_version 0.23
    hadoop\_path=”/usr/local/Cellar/hadoop/\$hadoop\_version.0/libexec/lib”git
    clone git://github.com/mongodb/mongo-hadoop.gitcd mongo-hadoopsed -i
    “s/default/\$hadoop\_version/g” build.sbtcd streaming./build.sh
-   34. Groking Twitter curl
    https://stream.twitter.com/1/statuses/sample.json
    -u\<login\>:\<password\> | mongoimport -d test -c live … let it run
    for about 2 hours
-   35. DEMO 1
-   36. Map Hashtags in Python\#!/usr/bin/env pythonimport
    syssys.path.append(“.”)from pymongo\_hadoop import BSONMapperdef
    mapper(documents): for doc in documents: for hashtag in
    doc[entities][hashtags]: yield {\_id: hashtag[text], count:
    1}BSONMapper(mapper)print \>\> sys.stderr, “Done Mapping.”
-   37. Reduce hashtags in Python\#!/usr/bin/env pythonimport
    syssys.path.append(“.”)from pymongo\_hadoop import BSONReducerdef
    reducer(key, values): print \>\> sys.stderr, “Hashtag %s” %
    key.encode(utf8) \_count = 0 for v in values: \_count += v[count]
    return {\_id: key.encode(utf8), count: \_count}BSONReducer(reducer)
-   38. All together hadoop jar
    target/mongo-hadoop-streaming-assembly-1.0.0-rc0.jar -mapper
    examples/twitter/twit\_hashtag\_map.py -reducer
    examples/twitter/twit\_hashtag\_reduce.py -inputURI
    mongodb://127.0.0.1/test.live -outputURI
    mongodb://127.0.0.1/test.twit\_reduction -file
    examples/twitter/twit\_hashtag\_map.py -file
    examples/twitter/twit\_hashtag\_reduce.py
-   39. Popular Hash Tags db.twit\_hashtags.find().sort( {count : -1 }){
    “\_id” : “YouKnowYoureInLoveIf”, “count” : 287 }{ “\_id” :
    “teamfollowback”, “count” : 200 }{ “\_id” : “RT”, “count” : 150 }{
    “\_id” : “Arsenal”, “count” : 148 }{ “\_id” : “milars”, “count” :
    145 }{ “\_id” : “sanremo”, “count” : 145 }{ “\_id” :
    “LoseMyNumberIf”, “count” : 139 }{ “\_id” : “RelationshipsShould”,
    “count” : 137 }{ “\_id” : “Bahrain”, “count” : 129 }{ “\_id” :
    “bahrain”, “count” : 125 }{ “\_id” : “oomf”, “count” : 117 }{ “\_id”
    : “BabyKillerOcalan”, “count” : 106 }{ “\_id” : “TeamFollowBack”,
    “count” : 105 }{ “\_id” : “WhyDoPeopleThink”, “count” : 102 }{
    “\_id” : “np”, “count” : 100 }
-   40. DEMO 2
-   41. Aggregation in Mongo 2.1 db.live.aggregate( { \$unwind :
    “\$entities.hashtags” } , { \$match : { “entities.hashtags.text” : {
    \$exists : true } } } , { \$group : { \_id :
    “\$entities.hashtags.text”, count : { \$sum : 1 } } } , { \$sort : {
    count : -1 } }, { \$limit : 10 })
-   42. Popular Hash Tags db.twit\_hashtags.aggregate(a){ “result” : [ {
    "\_id" : "YouKnowYoureInLoveIf", "count" : 287 }, { "\_id" :
    "teamfollowback", "count" : 200 }, { "\_id" : "RT", "count" : 150 },
    { "\_id" : "Arsenal", "count" : 148 }, { "\_id" : "milars", "count"
    : 145 }, { "\_id" : "sanremo","count" : 145 }, { "\_id" :
    "LoseMyNumberIf", "count" : 139 }, { "\_id" : "RelationshipsShould",
    "count" : 137 }, { "\_id" : "Bahrain", "count" : 129 }, { "\_id" :
    "bahrain", "count" : 125 } ],”ok” : 1}
-   43. The Future of humongous data
-   44. What is BIG? BIG today is normal tomorrow
-   45. Data Growth 9,00090006750 4,4004500 2,1502250 1,000 500 55 120
    250 1 4 10 24 0 2000 2001 2002 2003 2004 2005 2006 2007 2008 2009
    2010 2011 Millions of URLs
-   46. Data Growth 9,000 9000 6750 4,4004500 2,1502250 1,000 500 55 120
    250 1 4 10 24 0 2000 2001 2002 2003 2004 2005 2006 2007 2008 2009
    2010 2011 Millions of URLs
-   47. 2012 Generating over 250 Millions of tweets per day
-   48. MongoDB enables us to scale with the redeﬁnition of BIG. New
    processing tools like Hadoop & Storm are enabling us to process the
    new BIG.
-   49. Hadoop is our ﬁrst step
-   50. MongoDB iscommitted to working with best data tools including
    Hadoop, Storm, Disco, Spark & more
-   51. http://spf13.com http://github.com/spf13 @spf13 Questions?
    download at github.com/mongodb/mongo-hadoop

