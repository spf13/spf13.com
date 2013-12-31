{
	"disqus_url" : "http://spf13.com/post/creating-your-own-symfony2-bundle/",
	"disqus_identifier" : "1377 http://spf13.com/?p=1377",
	"disqus_title" : "Creating your own Symfony2 Bundle",
	"Title": "Creating your own Symfony2 Bundle",
	"Description": "",
	"Keywords": [
		"Development",
		"php",
		"PHP",
		"Programming",
		"symfony",
		"Symfony2"
	],
	"Tags": [
		"PHP",
		"Programming",
		"symfony",
		"Symfony2"
	],
	"Pubdate": "2011-05-24",
	"Topics": [
		"Development",
		"php"
	],
	"Url": "post/creating-your-own-symfony2-bundle",
	"Slug": "creating-your-own-symfony2-bundle",
	"Section": "post",
	"Thumbnail": "/images/1379_symfony_black_03.png-200x200.png"
}
{{% img src="/media/symfony_ss.png" alt="symfony" %}}

[Symfony2](http://symfony.com/) is a great web framework.
[OpenSky](https://opensky.com) is built on this framework and we are one
of the largest contributors to it. The primary building block for
Symfony2 is a bundle. Through it’s bundle system Symfony 2.0 achieves a
level of modularity I haven’t seen in other web frameworks. A bundle
permits a developer to add functionality to the framework and is the
best way to develop applications with Symfony2. In this post I’ll show
you how to create your own bundle.

Start off with the sandbox
--------------------------

First install symfony sandbox…

the console can create a basic bundle for you.

    > app/console init:bundle Spf13/SteveBundle

    Initializing bundle "SteveBundle" in "Sites/sandbox/src/Spf13"

Tell Symfony2 about it
----------------------

Just having the bundle in place isn’t enough, you need to tell Symfony2
it exists (and where).

In your **app/AppKernel.php** inside the \$bundles array in
the***registerBundle function*** add the following line

        new Spf13\SteveBundle\SteveBundle(),

Routing
-------

You also need to define a route and tell Symfony2 where to find the
routing file. Of the 4 different formats available, I prefer yaml which
is the default in Symfony2.

in **app/config/routing.yml**

    steve:
        resource: @SteveBundle/Resources/config/routing.yml

Now create that **routing.yml** file with the following contents.

     steve:
         pattern:  /steve
              defaults: { _controller: SteveBundle:Default:index }

The Controller
--------------

    The init command has created a controller for you called DefaultController with a basic action (index) which renders a basic php template file.

Now visit the page in a browser to confirm everything worked.

**http://localhost/[webroot]/app\_dev.php/steve**

and be greeted by your new bundle.

### Related Posts

-   [Getting Started with
    Symfony2](http://spf13.com/post/getting-started-with-symfony2/)
-   [On Symfony2](http://spf13.com/post/symfony2/)
-   [Creating a Symfony2 Console
    Command](http://spf13.com/post/creating-a-symfony2-console-command/)
-   [Next Gen PHP
    Frameworks](http://spf13.com/post/next-gen-php-frameworks/)

