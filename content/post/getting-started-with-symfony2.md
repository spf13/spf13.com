{
	"disqus_url" : "http://spf13.com/post/getting-started-with-symfony2/",
	"disqus_identifier" : "1268 http://spf13.com/?p=1268",
	"disqus_title" : "Getting Started with Symfony2",
	"Title": "Getting Started with Symfony2",
	"Description": "",
	"Keywords": [
		"Development",
		"php",
		"development",
		"PHP",
		"Symfony2"
	],
	"Tags": [
		"development",
		"PHP",
		"Symfony2"
	],
	"Pubdate": "2011-03-07",
	"Topics": [
		"Development",
		"php"
	],
	"Url": "post/getting-started-with-symfony2",
	"Slug": "getting-started-with-symfony2",
	"Section": "post",
	"Thumbnail": "/images/1272_Symfony.png-200x200.png"
}
{{% img src="/media/symfony_ss.png" alt="symfony" %}}

In a follow up to my popular post [on
Symfony2](http://spf13.com/post/symfony2 "On Symfony2"), the open source
PHP framework we use at [OpenSky](http://shopopensky.com), I’m providing
an easy guide to getting started using [Symfony2](http://symfony.com).
This isn’t your basic “Hello World”, but a practical guide to beginning
a project with Symfony2.

Requirements
------------

To get started with Symfony2 you should have a working install of Git as
well as a well made install of PHP version 5.3+.

Symfony2 also requires internationalization support compiled into PHP.

Bootstrapping your Symfony2 application
---------------------------------------

Symfony2 uses the Phar capability included in 5.3 to package an entire
program into a single file.

You can get the Symfony2 bootstrapper from github.

    git clone git://github.com/symfony/symfony-bootstrapper.git

Before going any further, let’s make sure your version of PHP will work
with Symfony2 provided you’re still in the same directory, run this:

    php symfony-bootstrapper/symfony.phar

Did you see this options screen?<br>
 If yes, skip to Creating your application.

    Symfony Bootstrapper version 2.0.0-DEV
    Usage:
      [options] command [arguments]

    Options:
      --help           -h Display this help message.
      --quiet          -q Do not output any message.
      --verbose        -v Increase verbosity of messages.
      --version        -V Display this program version.
      --ansi           -a Force ANSI output.
      --no-interaction -n Do not ask any interactive question.

    Available commands:
      help   Displays help for a command (?)
      init
      list   Lists commands

If you didn’t see the options screen chances are you saw a series of ?s

    ???????????????

### Fixing PHP in Mac OSX

The OSX stock install of PHP doesn’t quite work right for Symfony2 due
to some critical missing dependencies.
 If you see …

    php symfony.phar
    ???????????????

You’re going to need to install a new version. My colleague and friend
Justin Hileman has the easiest method of [installing PHP on
OSX](http://justinhileman.info/articles/reinstalling-php-53-on-mac-os-x).

Once that is completed resume with Creating your Application

Creating your application.
--------------------------

Somewhere web accessible create a new directory for your application.

    cd ~/Sites/
    mkdir myApp
    cd myApp

Now you will use the phar package you just grabbed from github to create
a skeleton of sorts. Make sure to supply the path to your phar file.

    php ~/Code/symfony-bootstrapper/symfony.phar init --name="App" --format="yml"

If you want to see what other options you have just run php symfony.phar
help init

    php ~/Code/symfony-bootstrapper/symfony.phar help init Usage: init [--name="..."] [--app-path="..."] [--src-path="..."] [--web-path="..."] [--format="..."]

    Options:
     --name The application name (App) (default: App)
     --app-path The path to the application (app/) (default: app/)
     --src-path The path to the application (src/) (default: src/)
     --web-path The path to the public web root (web/) (default: web/)
     --format Use the format for configuration files (php, xml, or yml) (default: xml)

Installing Symfony
------------------

Again we will fetch this from GitHub.

    git clone git://github.com/symfony/symfony.git src/vendor/symfony

Installing Symfony’s 3rd party libraries
----------------------------------------

    sh src/vendor/symfony/vendors.sh

*Coming Soon*

 See part 2. Creating your own symfony2 bundle

 See part 3. Creating your own symfony2 console command

References
----------

[http://amalraghav.com/symfony2-creating-your-own-app/](http://amalraghav.com/symfony2-creating-your-own-app/)
