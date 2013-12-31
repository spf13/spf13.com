{
	"disqus_url" : "http://spf13.com/post/getting-started-with-mongodb-and-php/",
	"disqus_identifier" : "1795 http://spf13.com/?p=1795",
	"disqus_title" : "Getting Started with MongoDB and PHP",
	"Title": "Getting Started with MongoDB and PHP",
	"Description": "The first in a series of posts on MongoDB and PHP that will both explain why you should use MongoDB and teach you how.",
	"Keywords": [
		"Development",
		"MongoDB",
		"php",
		"mongodb",
		"nosql",
		"Open source",
		"Pear",
		"PHP"
	],
	"Tags": [
		"mongodb",
		"nosql",
		"Open source",
		"Pear",
		"PHP"
	],
	"Pubdate": "2012-05-14",
	"Topics": [
		"Development",
		"MongoDB",
		"php"
	],
	"Url": "post/getting-started-with-mongodb-and-php",
	"Slug": "getting-started-with-mongodb-and-php",
	"Section": "post",
	"Thumbnail": "/images/1800_MongoPHP.png-200x200.png"
}
[![Getting Started with MongoDB and
PHP](/images/1800_MongoPHP.png-200x200.png)](/uploads/2012/05/MongoPHP.png "Getting Started with MongoDB and PHP")

Nearly 3 years ago I discovered a new database that literally changed my
life. I know, that’s a pretty bold claim, but it’s true. While leading
the engineering team at [OpenSky](http://osky.co/uGeJpa) I faced a
problem I was well familiar with. How to build a e-commerce product
that: 1. Provided performance and scale 2. Handled many verticals and 3.
Provided proper indexing on key attributes. In search for a better
solution to this problem I encountered MongoDB. I soon experienced a
realization that not only was MongoDB the solution to my e-commerce
challenge, but fundamentally would change the way all development
happens.

This is the first in a series of posts on MongoDB and PHP that will both
explain why you should use MongoDB and teach you how. In this first post
we will begin with installing the necessary servers and drivers to be
able to use MongoDB with PHP.

Introduction to MongoDB
=======================

MongoDB (from “hu**mongo**us”) is a scalable, high-performance, open
source document database written in C++. While many people hear
‘document database’ and they think of pdf and doc files, the term
document really is analogous to an array in PHP. Effectively MongoDB is
a persistent storage engine for PHP arrays and objects (as well as any
other language) with read through, write thorough memory caching, true
high availability,  an elegant interface and seamless horizontal scale.
Once you write an application with MongoDB you’ll wonder why anyone uses
anything else.

Installing MongoDB
==================

Installing MongoDB is as easy as using your package installer to install
the package. Whether you are using Linux, Mac or Windows, it’s easy to
install MongoDB.

[The MongoDB Manual](http://docs.mongodb.org/manual) has a [complete
guide on installing
MongoDB](http://docs.mongodb.org/manual/installation/) for all the
different systems it supports.

Installing PHP Driver for MongoDB
=================================

The 1st step is to install PECL. PECL is the default installer for all C
extensions to the PHP driver. Usually if you have PHP installed you
already have PECL. You may be surprised to find that Mac OS X doesn’t
include PECL, in the event you don’t have PECL already, here’s how to
install it.

### Installing PEAR & PECL

1.  cd /usr/lib/php
2.  `sudo php install-pear-nozlib.phar`
3.  Edit `/etc/php.ini` and find the line:
     `;include_path = ".:/php/includes" `change it
    to: `include_path = ".:/usr/lib/php/pear" `*make sure to remove the
    ‘;’ at the beginning of that line.*
4.  `sudo pear channel-update pear.php.net`
5.  `sudo pecl channel-update pecl.php.net`
6.  `sudo pear upgrade-all`

Once you have PECL installed the process is easy to install the Mongo DB
driver. A simple

    pecl install mongo

is all it takes. Once that’s completed you’ll need to add the extension
line to your PHP.ini file and restart Apache. For \*nix the line is

    extension=mongo.so

Once Apache is restarted you should confirm that the MongoDB extension
is installed by checking php\_info(). A shortcut for this is

$ php --re mongo

Creating your first connection to MongoDB
=========================================

Creating a connection to MongoDB is pretty easy. We create a new Mongo
object and pass in the URI of the server you’re connecting to. The
following example will show you how to connect to a Mongo DB server,
create a db and a collection and insert a single record into that
collection.

{{% highlight php %}}
<?php
// open connection to MongoDB server
$conn = new Mongo('localhost');
// access people collection inside the test database
$people = $conn->test->people;
$person = [ 'name' => 'Steve Francia', 'alias' => 'spf13'];
$people->save($person);
print_r($people->findAll());
?>
{{% /highlight %}}

Stay tuned for my next post which I will demonstrate how to perform
basic crud operations in MongoDB.

### Related Posts

-   [NoSQL databases and Managing Big
    Data](http://spf13.com/post/nosql-databases-and-managing-big-data/)
-   [MongoDB and PHP at ZendCon
    2011](http://spf13.com/post/mongodb-and-php-at-zendcon-2011/)
-   [MongoDB, PHP and the Cloud – PHP Cloud Summit
    2011](http://spf13.com/post/mongodb-php-and-the-cloud-php-cloud-summit-2011/)
-   [MongoDB and PHP, The
    Book](http://spf13.com/post/mongodb-and-php-the-book/)

