{
	"disqus_url" : "http://spf13.com/post/scaling-web-sites-lamp-top-resources-2/",
	"disqus_identifier" : "335 http://localhost/~sfrancia/wordpress/?p=335",
	"disqus_title" : "Scaling Web Sites (LAMP) : Top Resources",
	"Title": "Scaling Web Sites (LAMP) : Top Resources",
	"Description": "",
	"Keywords": [
		"Architecture",
		"Scalability",
		"Systems",
		"apache",
		"facebook",
		"Flickr",
		"Linux",
		"mysql",
		"PHP",
		"Ruby",
		"scaling",
		"SysAdmin",
		"twitter"
	],
	"Tags": [
		"apache",
		"facebook",
		"Flickr",
		"Linux",
		"mysql",
		"PHP",
		"Ruby",
		"scaling",
		"SysAdmin",
		"twitter"
	],
	"Pubdate": "2009-04-15",
	"Topics": [
		"Architecture",
		"Scalability",
		"Systems"
	],
	"Url": "post/scaling-web-sites-lamp-top-resources-2",
	"Slug": "scaling-web-sites-lamp-top-resources-2",
	"Section": "post",
	"Thumbnail": "/uploads/2009/04/300px-Failwhale2.png"
}
{{% img src="/media/failwhale.png" class="third right hid" caption="Image via Wikipedia" %}}

Luckily it’s 2009 and there have been a bunch of successful websites
that have had to deal with large
[scalability](http://en.wikipedia.org/wiki/Scalability "Scalability")
challenges. Many have been kind enough to share their knowledge with the
world. Here is a list of the best books, articles, presentations and
practices from the likes of [Twitter](http://twitter.com "Twitter"),
[Facebook](http://facebook.com "Facebook"),
[Flickr](http://www.flickr.com "Flickr") and more.

Books
=====

[**Building Scalable Web Sites**](http://www.amazon.com/Building-Scalable-Web-Sites-applications/dp/0596102356)
---------------------------------------------------------------------------------------------------------------

[**Building, scaling, and optimizing the next generation of web
applications by Cal
Henderson**](http://www.amazon.com/Building-Scalable-Web-Sites-applications/dp/0596102356)

Cal of Flickr fame has written the definitive resource on scaling web
apps.

[**High Performance MySQL**](http://www.amazon.com/High-Performance-MySQL-Optimization-Replication/dp/0596101716/)
------------------------------------------------------------------------------------------------------------------

[**Optimization, Backups, Replication, and More by Baron Schwartz, Peter
Zaitsev, Vadim Tkachenko, Jeremy Zawodny, Arjen Lentz, Derek
Balling**](http://www.amazon.com/High-Performance-MySQL-Optimization-Replication/dp/0596101716/)

Another great resource, focused heavily on the
[MySQL](http://www.mysql.com "MySQL") portion of LAMP, which is the
hardest part to scale.

Articles
========

[**Optimizing with APC**](http://c7y.phparch.com/c/entry/1/art,apc_facebook)
----------------------------------------------------------------------------

Brian Shire is Facebook’s technical lead for
[PHP](http://php.net/ "PHP") internals and a developer for the
Alternative PHP Cache (APC). Learn more at [Tekrat](http://tekrat.com)
his home on the web.

Presentations
=============

**Scaling Twitter in Ruby (slightly dated)**
--------------------------------------------

Twitter was originally architected in [Ruby on
Rails](http://rubyonrails.org/ "Ruby on Rails") and had some pretty
serious scalability issues resulting in the now (in)famous fail whale.
His presentation is insightful and the basis of many of their inital
scalability measures (now failing as twitter has reached a magnitude
larger than when this was given). Presentation given by [Blaine
Cook](http://twitter.com/Blaine "Blaine Cook").

[**Scaling
Twitter**](http://www.slideshare.net/Blaine/scaling-twitter?type=presentation "Scaling Twitter"){{%
slideshare 41197 %}}

[**Scaling PHP5 by Rasmus Lerdorf**](http://talks.php.net/show/oscon06)
-----------------------------------------------------------------------

OSCON has been a major source for scalability presentations. In 2006
Rasmus delivered this presentation. Rasmus is notable for being the
creator of the [PHP](http://en.wikipedia.org/wiki/PHP "PHP") programming
language. [Niall
Kennedy](http://www.niallkennedy.com/blog/archives/2006/07/rasmus-lerdorf-php-web20.html)
recorded the audio and provided it as an mp3
[here.](/uploads/2009/04/phpweb201.mp3)

**Scaling Web Apps**
--------------------

Cal, the author of the first book mentioned also put many of the same
principles into a talk given at WebExpo
2007.!

[Scalable Web Architectures: Common Patterns and
Approaches](http://www.slideshare.net/techdude/scalable-web-architectures-common-patterns-and-approaches?type=presentation "Scalable Web Architectures: Common Patterns and Approaches"){{%
slideshare 40959 %}}

The same talk given (and updated) about a year later.

[Scalable Web Architectures: Common Patterns and Approaches – Web 2.0
Expo
NYC](http://www.slideshare.net/iamcal/scalable-web-architectures-common-patterns-and-approaches-web-20-expo-nyc-presentation?type=powerpoint "Scalable Web Architectures: Common Patterns and Approaches - Web 2.0 Expo NYC"){{%
slideshare 603137 %}}<br>

View more [OpenOffice presentations](http://www.slideshare.net/) from
[iamcal](http://www.slideshare.net/iamcal).

**Scaling [LiveJournal](http://www.livejournal.com/ "LiveJournal")**
--------------------------------------------------------------------

LiveJournal was the first open source LAMP based Web 2.0 company to hit
massive scale problems. They developed many of the strategies and tools,
including memcache, that [flickr.com](http://www.flickr.com "Flickr"),
[digg.com](http://digg.com "Digg") and [facebook.com](http://facebook.com "Facebook") are using
today.

[Brad Fitzpatrick](http://bradfitz.com "Brad Fitzpatrick") gave a good
presentation about how they grew, both the challenges they faced, and
the solutions they came
to. !

[LiveJournal’s Backend: A history of
scaling](http://www.slideshare.net/vishnu/livejournals-backend-a-history-of-scaling?type=powerpoint "LiveJournal's Backend: A history of scaling")
{{% slideshare 11260 %}}

Caching and Performance Lessons From Facebook
---------------------------------------------

{{% scribd 4069180 %}}
