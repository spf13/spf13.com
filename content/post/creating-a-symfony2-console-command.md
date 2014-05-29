---
Description: ""
Keywords:
- Development
- php
- Command-line interface
- PHP
- symfony
- Symfony2
Section: post
Slug: creating-a-symfony2-console-command
Tags:
- Command-line interface
- PHP
- symfony
- Symfony2
Thumbnail: /images/1379_symfony_black_03.png-200x200.png
Title: Creating a Symfony2 Console Command
Topics:
- Development
- php
Url: post/creating-a-symfony2-console-command
date: 2011-06-20
disqus_identifier: 1391 http://spf13.com/?p=1391
disqus_title: Creating a Symfony2 Console Command
disqus_url: http://spf13.com/post/creating-a-symfony2-console-command/
---

{{% img src="/media/symfony_ss.png" alt="symfony" %}}

One of the weaknesses of PHP as a languages has always been it’s ability
to write proper command line utilities. Yes PHP is pretty much built to
drive the web, and it does that rather well, but there are plenty of
reasons to want to be able to write a program that is callable from the
command line that interfaces with your web app. Symfony2 does a rather
good job at providing a nice toolset to build command line applications
in php.

First you need a bundle. See [creating a Symfony2
bundle](http://spf13.com/post/creating-your-own-symfony2-bundle "Creating your own Symfony2 Bundle").

Creating your command line application
--------------------------------------

Create a directory in your bundle top level called Command

    mkdir steveBundle/Command

Create a class in that directory that ends in Command.php like
yoCommand.php

Populate the file with the following contents.

{{% highlight php %}}

    <?php
    namespace Spf13\SteveBundle\Command;

    use Symfony\Bundle\FrameworkBundle\Command\ContainerAwareCommand;
    use Symfony\Component\Console\Input\InputArgument;
    use Symfony\Component\Console\Input\InputInterface;
    use Symfony\Component\Console\Output\OutputInterface;

    /**
     * basic command class
     */
    class yoCommand extends ContainerAwareCommand
    {

        protected function configure()
        {
            $this
                ->setName('yo')
                ->setDescription('Tells you how great ___ is')
                ->setDefinition(array(
                    new InputArgument(
                        'label',
                        InputArgument::REQUIRED,
                        'The name you want to say hello to'
                    ),
                ));
        }

        protected function execute(InputInterface $input, OutputInterface $output)
        {
            $label = $input->getArgument('label');

            $output->writeln(sprintf('Hello %s', $label ));
        }

    }
    ?>

{{% /highlight %}}

Symfony2 will automatically locate and include the command as part of
the console commands.

Running your program
--------------------

    $ app/console yo steve

Hello steve

 

### Related Posts

-   [Next Gen PHP
    Frameworks](http://spf13.com/post/next-gen-php-frameworks/)
-   [Creating your own Symfony2
    Bundle](http://spf13.com/post/creating-your-own-symfony2-bundle/)
-   [On Symfony2](http://spf13.com/post/symfony2/)
-   [Getting Started with
    Symfony2](http://spf13.com/post/getting-started-with-symfony2/)

Other Resources
---------------

See
also [http://blog.liip.ch/archive/2010/12/21/using-the-symfony2-console.html](http://blog.liip.ch/archive/2010/12/21/using-the-symfony2-console.html)
