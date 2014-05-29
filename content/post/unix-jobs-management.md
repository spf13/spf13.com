---
Description: ""
Keywords:
- Architecture
- Systems
- Linux
- screen
- SysAdmin
- Systems
- UNIX
Section: post
Slug: unix-jobs-management
Tags:
- Linux
- screen
- SysAdmin
- Systems
- UNIX
Thumbnail: /uploads/2010/02/300px-GNU_Screen.png
Title: Unix Jobs Management
Topics:
- Architecture
- Systems
Url: post/unix-jobs-management
date: 2010-02-02
disqus_identifier: 76 http://localhost/~sfrancia/wordpress/?p=76
disqus_title: Unix Jobs Management
disqus_url: http://spf13.com/post/unix-jobs-management/
---

{{% img src="/media/300px-GNU_Screen.png" class="right third" alt="GNU Screen" %}}

Every self respecting linux, mac os X or \*nix user should have a solid
handle on managing jobs in unix. The following will explain how to run
tasks in the background, bring tasks to the foreground, background
already running tasks and keeping a task running while logged out.

Run a task in the background
----------------------------

All you need to to is follow a command with the ‘&’ character. Pretty
simple. What this does is start the command and background it. It will
keep running and when it is finished it will present the results to the
foreground.


    $ cp -av stuff /mnt/backup &amp;

    [1] 21394

The response indicates that the job is now backgrounded and the job id
is 1 and
the [process](http://en.wikipedia.org/wiki/Process_%28computing%29 "Process (computing)")
id is 21394.

A backgrounded process is still attached to your session. This means
that if you logout it will also stop, though it will warn you that a
process is running in the background when you ‘exit’.

Listing jobs (processes running in the background)
--------------------------------------------------

In this example I ran ‘sleep 100 &’. It is also in the background. To
see backgrounded jobs, simply type jobs.


    $ jobs

    [1]-  Running                 cp -av stuff /mnt/backup &amp;amp;
    [2]+  Stopped                 sleep 100 &amp;

Bring a backgrounded app to the foreground
------------------------------------------

I want to see how my backup is going so I’ll bring it back to the
foreground to view it. To do this you need to know the job id which is
the number in the [] above.

There are couple ways to do this… The first works everywhere, where the
latter is specific to bash (though it may also exist in your preferred
shell).


    $ %1

or


    $ fg 1

Suspending a task.
------------------

Satisfied that the backup is going well, you now want to backgroud it
again. type -z to suspend it. This will temporarily stop the process
from running and bring you to a shell prompt again. From there just
‘[bg](http://en.wikipedia.org/wiki/Bg_%28Unix%29 "Bg (Unix)")‘ it.


    hit &lt;ctrl&gt;-z

    [1]+  Stopped               cp -av stuff /mnt/backup &amp;
    $

    $ bg 1
    [1]+ cp -av stuff /mnt/backup &amp;amp;

Running a process and logging out
---------------------------------

There are three different approaches to doing this.
Screen, [nohup](http://en.wikipedia.org/wiki/Nohup "Nohup") and disown.
Screen seems like the most versile, though you technically aren’t
logging out, but you can disconnect completely without worrying that it
will stop. Both nohup and screen require you to do something prior to or
during starting the process so neither can work if the process is
already going. For these circumstances their is disown.

### Screen

Screen is a versitile tool and a must use for any system admin. I could
easily devote a full blog post on screen, in fact I did. [Be more
productive using gnu
screen](http://spf13.com/content/be-more-productive-using-gnu-screen)

### nohup

nohup is a POSIX command to ignore the HUP (hangup) signal, enabling the
command to keep running after the user who issues the command has logged
out. The HUP (hangup) signal is by convention the way a terminal warns
depending processes of logout.

nohup is most often used to run commands in the background as daemons.
Output that would normally go to the terminal goes to a file called
nohup.out if it has not already been redirected. This command is very
helpful when there is a need to run numerous batch jobs which are
inter-dependent.

If you redirect the streams you can avoid filling up your filesystem
with nohup.out files as follows…


    $ nohup tar czf /backup/home.tgz . &gt; /dev/null 2&gt;&amp;1 &amp;

Some shells (bash) provide a similar function called disown which can be
run after the command is already running. If you are using bash, there
really isn’t a reason to use nohup, use disown instead.

### disown

Disown is easy enough to use, background a job (bg 1 for example) then
type disown.


        $ bg 1
        $ disown

### Alternatives

Use ‘setsid’ which will run a program in a new session.

It is also possible to use “dislocate” for this.

Under Debian, it is possible to use /sbin/start-stop-daemon to daemonise
a process.

Another way to avoid the process being bound to a terminal is to have
the at daemon run it, as for example with echo command | at now.

### Warning

Once a job is disowned (or run using nohup) you can no longer bring it
to the foreground and you no longer own it. It will not be listed in
jobs. Only do this if you won’t need to access it again. Your only
option to stop it is to kill it.

### Notes

bg defaults to the last suspended job, so it isn’t necessary to provide
the job id.

## Related articles
-   [Parallelization in
    bash](http://almirkaric.com/2010/5/2/parallelization-in-bash/)
    (almirkaric.com)
-   [Linux Guide for newbie : essential shortcuts and sanity
    commands](http://www.techmadly.com/linux-guide-for-newbie-essential-shortcuts-and-sanity-commands)
    (techmadly.com)
-   [Perfect Team: autossh and GNU
    Screen](http://noone.org/blog/English/Computer/Shell/Perfect%252520Team:%252520autossh%252520and%252520GNU%252520Screen.html)
    (noone.org)

