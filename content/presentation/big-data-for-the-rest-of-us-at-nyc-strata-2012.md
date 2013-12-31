{
	"disqus_url" : "http://spf13.com/post/big-data-for-the-rest-of-us-at-nyc-strata-2012/",
	"disqus_identifier" : "1884 http://spf13.com/?p=1884",
	"disqus_title" : "Big Data for the rest of us at NYC Strata 2012",
	"Title": "Not Just Hadoop: NoSQL in the Enterprise at Strata NYC 2012",
	"Description": "open source NoSQL solution MongoDB and data processor Hadoop have made  big data accessible.  Previously big data meant proprietary software and big hardware.",
	"Keywords": [
		"Architecture",
		"MongoDB",
		"Presentations",
		"Scalability",
		"Systems",
		"Tech Industry",
		"Apache Hadoop",
		"Architecture",
		"big data",
		"data",
		"Data analysis",
		"Data Processor",
		"Data Storage",
		"hadoop",
		"Information technology",
		"mongodb",
		"nosql",
		"nyc",
		"Orbitz",
		"Strata",
		"Strata Nyc",
		"structured storage"
	],
	"Tags": [
		"Apache Hadoop",
		"Architecture",
		"big data",
		"data",
		"Data analysis",
		"Data Processor",
		"Data Storage",
		"hadoop",
		"Information technology",
		"mongodb",
		"nosql",
		"nyc",
		"Orbitz",
		"Strata",
		"Strata Nyc",
		"structured storage"
	],
	"Pubdate": "2012-10-29",
	"Topics": [
		"Architecture",
		"MongoDB",
		"Presentations",
		"Scalability",
		"Systems",
		"Tech Industry"
	],
	"Url": "presentation/big-data-for-the-rest-of-us-at-nyc-strata-2012",
	"Slug": "big-data-for-the-rest-of-us-at-nyc-strata-2012",
	"Section": "presentation",
	"Thumbnail": "/images/1892_Screen-Shot-2012-10-29-at-6.12.38-PM.png-200x200.png"
}
At the NYC Strata & Hadoop World conference I presented on ‘Not Just
Hadoop: NoSQL in the Enterprise’. [Robert
Lancaster](http://twitter.com/rob1lancaster) from
[Orbitz](http://orbitz.com) joined me on stage for the final
presentation of the [Bridge to Big
Data](http://strataconf.com/stratany2012/public/schedule/topic/Bridge+to+Big+Data) track.
[Mark Madsen](http://twitter.com/markmadsen) did a great job moderating
the session and kept the energy high the entire day. Robert shared how
Orbitz uses MongoDB with Apache Hadoop to provide real time rates. This
is my second time presenting at Strata’s Big Data conference.  There are
few things I enjoy more in my work than presenting to an engaged
audience full of good questions which is exactly what I found at Strata.

While Hadoop is the most well-known technology in big data, it’s not
always the most approachable or appropriate solution for data storage
and processing. In this session you’ll learn about enterprise NoSQL
architectures, with examples drawn from real-world deployments, as well
as how to apply big data regardless of the size of your own enterprise.

{{% slideshare 14939019 %}}

**[Big data for the rest of
us](http://www.slideshare.net/spf13/big-data-for-the-rest-of-us "Big data for the rest of us")**
from **[Steve Francia](http://www.slideshare.net/spf13)**

Tweets
------

As the talk was going on the following tweets mentioned some highlights

> .@[spf13](https://twitter.com/spf13): “Moore’s Law applies to more
> than just CPUs.It also applies to data”
> [\#structureconf](https://twitter.com/search/%23structureconf)
>
> — Matt Asay (@mjasay) [October 23,
> 2012](https://twitter.com/mjasay/status/260839414463332352)

> .@[spf13](https://twitter.com/spf13): “For 10+ years, Big Data =
> ‘custom sw w/ big hw.’” In the past few years open source has made Big
> Data accessible to the rest of us
>
> — Matt Asay (@mjasay) [October 23,
> 2012](https://twitter.com/mjasay/status/260840149720649728)

> Learning from @[spf13](https://twitter.com/spf13) of
> @[10gen](https://twitter.com/10gen) how MongoDB enables
> [\#BigData](https://twitter.com/search/%23BigData) (for the rest of
> us) [\#strataconf](https://twitter.com/search/%23strataconf)
>
> — Tamara Dull (@tamaradull) [October 23,
> 2012](https://twitter.com/tamaradull/status/260841444036734976)

> “What is BIG? What is big today is normal tomorrow.”
> @[spf13](https://twitter.com/spf13)
> [\#strataconf](https://twitter.com/search/%23strataconf)
>
> — Tamara Dull (@tamaradull) [October 23,
> 2012](https://twitter.com/tamaradull/status/260844647264432129)

https://twitter.com/markmadsen/status/260844790348918784

## Related Posts

-   [How to deliver a great conference
    tutorial](http://spf13.com/post/how-to-deliver-great-conference-tutorials/)
-   [MongoDB and Hadoop](http://spf13.com/post/mongodb-and-hadoop/)
-   [MongoDB, Hadoop and Humongous
    Data](http://spf13.com/post/mongodb-hadoop-and-humongous-data/)
-   [Building your first MongoDB app – OSCON
    2012](http://spf13.com/post/building-your-first-mongodb-app-oscon-2012/)
-   [How I gave the most viewed presentation in the history of
    OSCON](http://spf13.com/post/how-i-gave-the-most-viewed-presentation-in-the-history-of-oscon/)

 

Presentation Transcript
-----------------------

-   1. Not Just Hadoop, NoSQL in the Enterprise
-   2. Talking about What is BIG Data BIG Data & you Real world examples
    The future of Big Data
-   3. @spf13 AKA Steve Francia 16+ years building the internet Father,
    husband, skateboarder Chief Evangelist @responsible for
    drivers,integrations, web & writing
-   4. What isBIG data ?
-   5. 2000 Google Inc Today announced it has released the largest
    search engine on theInternet. Google’s new index, comprising more
    than 1 billion URLs
-   6. 2008 Our indexing system for processing links indicates that we
    now count 1 trillion unique URLs (and the number of individual
    webpages out there is growing by several billion pages per day).
-   7. An unprecedented amount of data is being created and is
    accessible
-   8. Data Growth
-   9. Truly Exponential GrowthIs hard for people to grasp. A BBC
    reporter recently: “Your current PC is more powerful than the
    computer they had on board the ﬁrst ﬂight to the moon”.
-   10. Moore’s LawApplies to more than just CPUs Boiled down it is that
    things double at regular intervals. It’s exponential growth.. and
    applies to big data
-   11. How BIG is it?
-   12. How BIG is it? 2008
-   13. How BIG is it? 20072008 2005 2006 2003 2004 2001 2002
-   14. We’ve had BIG Data needs for a long time. In 1998 Google won the
    search race through custom software & infrastructure
-   15. We’ve had BIG Data needs for a long time. In 2002 Amazon again
    wrote custom & proprietary software to handle their BIG Data needs
-   16. We’ve had BIG Data needs for a long time. In 2006 Facebook
    started with off the shelf software, but quickly turned to
    developing their own custom built solutions
-   17. Ability to handle big data is one of the largest factors in
    determining winners vs losers.
-   18. For over a decade BIG Data = custom software
-   19. Why all this talk about BIG Data now?
-   20. In the past fewyears open source software emerged enabling ‘us’
    to handle BIG Data
-   21. The Big Data Story
-   22. Is actually two stories
-   23. Doers & Tellers talking about different
    things [http://www.slideshare.net/siliconangle/trendconnect-big-data-report-september](http://www.slideshare.net/siliconangle/trendconnect-big-data-report-september)
-   24. Tellers
-   25. Doers
-   26. Doers talk a lot more about actual solutions
-   27. They know it’s a two sided story: Storage & Processing
-   28. Take aways: MongoDB and Hadoop,  MongoDB for storage &
    operations. Hadoop for processing & analytics
-   29. How MongoDB enables big data • Flexible schema• Horizontal scale
    built in & free•Operates at near speed of memory• Optimized for
    modern apps
-   30. MongoDB @ Orbitz Rob Lancaster October 23 | 2012
-   31. Use Cases • Hotel Data Collection • Hotel Rate Feed: • Supply
    hotel rates to Google for their Hotel Finder • Uses MongoDB: –
    Maintain state of data sent to Google – Identify changes in rates as
    they occur • Makes use of complex querying, secondary indexing •
    EasyLoader: • Feature allowing suppliers to easily load inventory to
    Orbitz • Uses MongoDB to persist all changes for auditing purposes
    29
-   32. Hotel Data Collection • Goals: • Better understand performance
    of our hotel path • Optimize our hotel rate cache • Methods: •
    Capture every action performed by our hotel search engine. • Persist
    this data for long periods. • Challenges: • Need high performance
    capture. • Scalable, inexpensive storage. 30
-   33. Requirements Collection Storage & Processing • High write
    throughput • High data volume • 500 servers • \~500 GB/day • \> 100
    million documents/day • 7 TB/month compressed • Flexibility •
    Scalable • Complex extendable documents • Inexpensive • No forced
    schema • Proximity with other data • Scalability • Simplicity 31
-   34. The Solution • Utilize MongoDB as a collector: • \~ 500 clients
    • Utilize unsafe writes for high throughput • Heterogeneous
    documents • New collection for each hour • HDFS for storage &
    processing: • Data moved via M/R job: – One job per collection – One
    mapper per MongoDB instance • Additional processing and analysis by
    other jobs 32
-   35. Challenges & Conclusions •Challenges? None really. •Achieved a
    robust and simple solution •MongoDB has been entirely worry free •
    Very high write throughput • Reads (well, full collection dumps
    across the wire) are slower 33
-   36. The Futureof BIG data
-   37. What is BIG? BIG today isnormal tomorrow
-   38. Data Growth 9,00090006750 4,4004500 2,1502250 1,000 500 55 120
    250 1 4 10 24 0 2000 2001 2002 2003 2004 2005 2006 2007 2008 2009
    2010 2011 Millions of URLs
-   39. Data Growth 9,00090006750 4,4004500 2,1502250 1,000 500 55 120
    250 1 4 10 24 0 2000 2001 2002 2003 2004 2005 2006 2007 2008 2009
    2010 2011 Millions of URLs
-   40. How BIG is it?
-   41. How BIG is it? 2012
-   42. How BIG is it? 20112012 2009 2010 2007 2008 2005 2006
-   43. 2012 Generating over 250 Millions of tweets per day
-   44. MongoDB enables us to scale with the redeﬁnition of BIG. Tools
    like Hadoop are enabling us to process thenew BIG.
-   45. MongoDB iscommitted to working with best data tools including
    Hadoop, Storm,Disco, Spark & more

