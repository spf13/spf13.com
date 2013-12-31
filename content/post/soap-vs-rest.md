{
	"disqus_url" : "http://spf13.com/post/soap-vs-rest/",
	"disqus_identifier" : "121 http://localhost/~sfrancia/wordpress/?p=121",
	"disqus_title" : "SOAP vs. REST",
	"disqus_url" : "http://spf13.com/post/soap-vs-rest",
	"disqus_identifier" : "121 http://localhost/~sfrancia/wordpress/?p=121",
	"disqus_title" : "SOAP vs. REST",
	"Title": "REST vs SOAP, the difference between soap and rest",
	"Description": "What's SOAP? What's REST? and what the differences are between them with recommendations of when to use REST versus SOAP",
	"Keywords": [
		"Architecture",
		"Development",
		"Systems",
		"api",
		"remote procedure call",
		"representational state transfer",
		"rest",
		"RPC",
		"soap",
		"software architecture",
		"web service",
		"web services",
		"web standards",
		"ws security"
	],
	"Tags": [
		"api",
		"remote procedure call",
		"representational state transfer",
		"rest",
		"RPC",
		"soap",
		"software architecture",
		"web service",
		"web services",
		"web standards",
		"ws security"
	],
	"Pubdate": "2010-01-15",
	"Topics": [
		"Architecture",
		"Development",
		"Systems"
	],
	"Url": "post/soap-vs-rest",
	"Slug": "soap-vs-rest",
	"Section": "post",
	"Thumbnail": "http://spf13.com/wp-content/themes/striking/cache/images/1254_20090415_soap.jpeg-200x200.jpg"
}
{{% img src="/media/soap.jpeg" class="third right" %}}

Someone asked me a question today “Why would anyone choose SOAP ([Simple
Object Access Protocol](http://en.wikipedia.org/wiki/SOAP "SOAP"))
instead of REST ([Representational State
Transfer](http://en.wikipedia.org/wiki/Representational_State_Transfer "Representational State Transfer"))?”
My response: “The general rule of thumb I’ve always heard is ‘Unless you
have a definitive reason to use SOAP use REST’”. He asked “what’s one
reason?” I thought about it for a minute and honestly answered that I
haven’t ever come across a reason. My background is building great
internet companies.

While he seemed satisfied, I wasn’t very happy with that answer, I did
some homework and here’s my summary on REST versus SOAP, the difference
between SOAP and REST and why anyone would choose SOAP. As usual, with
competing technologies both have value, the challenge is to know when to
use each one (spoiler: luckily the answer is almost always REST).

I’m clearly boiling down a somewhat so please don’t flame me for
simplifying things, but feel free to provide any corrections you feel
are necessary.

Definitions
===========

REST
----

RESTs sweet spot is when you are exposing a public API over the internet
to handle CRUD operations on data. REST is focused on accessing named
resources through a single consistent interface.

SOAP
----

SOAP brings it’s own protocol and focuses on exposing pieces of
application logic (not data) as services. SOAP exposes operations. SOAP
is focused on accessing named operations, each implement some business
logic through different interfaces.

Though SOAP is commonly referred to as “[web
services](http://en.wikipedia.org/wiki/Web_service "Web service")” this
is a misnomer. SOAP has very little if anything to do with the Web. REST
provides true “Web services” based on URIs and HTTP.

By way of illustration here are few calls and their appropriate home
with commentary.


    getUser(User);

This is a rest operation as you are accessing a resource (data).


    switchCategory(User, OldCategory, NewCategory)

This is a SOAP operation as you are performing an operation.

Yes, either could be done in either SOAP or REST. The purpose is to
illustrate the conceptual difference.

Why REST?
=========

Here are a few reasons why REST is almost always the right answer.

Since REST uses standard HTTP it is much simpler in just about ever way.
Creating clients, developing APIs, the documentation is much easier to
understand and there aren’t very many things that REST doesn’t do
easier/better than SOAP.

REST permits many different data formats where as SOAP only permits XML.
While this may seem like it adds complexity to REST because you need to
handle multiple formats, in my experience it has actually been quite
beneficial. JSON usually is a better fit for data and parses much
faster. REST allows better support for browser clients due to it’s
support for JSON.

REST has better performance and scalability. REST reads can be cached,
SOAP based reads cannot be cached.

It’s a bad argument (by authority), but it’s worth mentioning that Yahoo
uses REST for all their services including Flickr and del.ici.ous.
Amazon and Ebay provide both though Amazon’s internal usage is nearly
all REST [source](http://www.oreillynet.com/pub/wlg/3005). Google used
to provide only SOAP for all their services, but in 2006 they deprecated
in favor of REST [source](http://code.google.com/apis/soapsearch/). It’s
interesting how there has been an internal battle between rest vs soap
at amazon. For the most part REST dominates their architecture for web
services.

Why SOAP?
=========

Here are a few reasons you may want to use SOAP.

WS-Security
-----------

While SOAP supports SSL (just like REST) it also supports WS-Security
which adds some enterprise security features. Supports identity through
intermediaries, not just point to point (SSL). It also provides a
standard implementation of data integrity and data privacy. Calling it
“Enterprise” isn’t to say it’s more secure, it simply supports some
security tools that typical internet services have no need for, in fact
they are really only needed in a few “enterprise” scenarios.

WS-AtomicTransaction
--------------------

Need ACID Transactions over a service, you’re going to need SOAP. While
REST supports transactions, it isn’t as comprehensive and isn’t ACID
compliant. Fortunately ACID transactions almost never make sense over
the internet. REST is limited by HTTP itself which can’t provide
two-phase commit across distributed transactional resources, but SOAP
can. Internet apps generally don’t need this level of transactional
reliability, enterprise apps sometimes do.

WS-ReliableMessaging
--------------------

Rest doesn’t have a standard messaging system and expects clients to
deal with communication failures by retrying. SOAP has successful/retry
logic built in and provides end-to-end reliability even through SOAP
intermediaries.

Summary
=======

In Summary, SOAP is clearly useful, and important. For instance, if I
was writing an iPhone application to interface with my bank I would
definitely need to use SOAP. All three features above are required for
banking transactions. For example, if I was transferring money from one
account to the other, I would need to be certain that it completed.
Retrying it could be catastrophic if it succeed the first time, but the
response failed.

External Resources
==================

-   [Why Soap
    Sucks](http://www.somebits.com/weblog/tech/bad/whySoapSucks.html?seemore=y)
-   [SOAP or REST? it’s about your
    priorities!](http://blogs.oracle.com/SOAandEDA/2009/04/soap_or_rest_its_about_your_pr.html)
-   [Goodbye, Google SOAP search
    API](http://www.somebits.com/weblog/tech/googleSearchAPI.html)
-   [SOAP vs
    REST](http://www.ioncannon.net/web-services/117/soap-vs-rest/)

