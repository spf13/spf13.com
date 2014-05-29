---
Description: After subversion but before Git there was SVK. If you are stuck using
  subversion do yourself a favor and use svk.
Keywords:
- Development
- Systems
- git
- subversion
- svk
- svn
Section: post
Slug: using-svk-to-increase-productivity
Tags:
- git
- subversion
- svk
- svn
Thumbnail: ""
Title: Using SVK to Increase Productivity
Topics:
- Development
- Systems
Url: post/using-svk-to-increase-productivity
date: 2008-08-23
disqus_identifier: 219 http://localhost/~sfrancia/wordpress/?p=219
disqus_title: Using SVK to Increase Productivity
disqus_url: http://spf13.com/post/using-svk-to-increase-productivity/
---

SVK is a client for SVN built using perl. It makes a number of
improvements over the standard svn client, while retaining much of the
same feel. It works with the standard Subversion server and works
perfectly in an environment with some users using svn and some using svk
on the client side. It provides a number of sizable advantages over the
standard svn client and is a must have for any development project.

*UPDATE: It’s been a while since this article was written and while
still accurate, do yourself a favor and go use
[Git](http://git-scm.com).*

There are three things [SVK](http://en.wikipedia.org/wiki/SVK "SVK")
provides that are particularly noteworthy.

1.  Tracks all branching making the process of pulling and pushing
    changes between trunk and branch very easy.
2.  Optionally adds another layer to the mix.
    While [Subversion](http://subversion.tigris.org/ "Subversion software")
    has Repo and Working Copy, SVK has Repo (svn server) Depot (local
    mirror) and Working Copy (where you work). This provides two main
    features.
    1.  Works offline
    2.  You can commit changes to the depot without committing them to
        the repo.

3.  The working copy doesn’t have dot files, rather they are stored in
    ~/.svk (by default). Makes for much cleaner working copies. This
    also makes it so that you can use svk as a quick and dirty
    deployment tool as the working copies are clean.

The 2.5 different ways of using SVK.
------------------------------------

For practical use the terms depot and mirror are often the same. While
they aren’t completely synonymous they are somewhat used
interchangeably. A depot can contain many mirrors.

#### Standard Subversion Approach

You can use it like Subversion with the additional benefit of tracking
all branching and merges. In this case the mirror becomes transparent.

#### Distributed Approach

You can use it as a [distributed version
control](http://en.wikipedia.org/wiki/Distributed_revision_control "Distributed revision control").
Using this approach the mirror is the key. It can be a bit hard to get
used to, especially if you are used to SVN
or [CVS](http://www.nongnu.org/cvs "Concurrent Versions System").
However stick with it, it has a lot of benefits. Not only does it
provide offline functionality, but it also provides local versioning.

#### Distributed with local branch approach.

When using SVK in mirror mode you can also optionally branch locally
without branching on the server (this is the 1/2). This is especially
useful when you are working on a project where you don’t have write
access to
the [repository](http://en.wikipedia.org/wiki/Repository "Repository").
This way you can manage your versions (and keep up with the repository)
and submit a patch when you have a change ready.

Subversion Mode
---------------

When using this approach the typical routine is “pull” (optionally when
in branch), “update”, “modify”, “commit” repeat until ready to “push”
(optionally when in branch).

#### Checkout directly from the repository.

    svk co [repository] [local wc path]
    svk co http://host/svn/project ./code

svk ci , svk add, svk up just like subversion. See the common operations
for branching, pulling and pushing.

Mirror Mode.
------------

When using this approach the typical routine is “pull” (optionally when
in branch), “sync”, “update”, “modify”, “commit” repeat until ready to
“push” (optionally when in branch).

#### Create Depot

Start by creating your Depot.

        svk depotmap --init

#### Mirror Existing Repository

Next Mirror your existing repository. It is a good practice to mirror
the entire repo as it makes things easier down the road and disk space
is cheap. Since every operation under this directory is automatically
(vs manually) synchronized with the remote SVN repository it is usually
a good practice to either work on a branch, either a branch on the
server, or a local branch) and not directly on the mirror.

        svk mirror [repository url] [local depot url]

        example:
        svk mirror svn://HOST/var/svn/repos/Zoop //projects/Zoop

#### Sync local mirror with the repository

This will sync every commit since you last performed it. If it is the
first time you are running the command it may take a while depending on
how many revisions are in your project.

        svk sync //projects/friends

#### Check out working copy from local mirror

        svk co //projects/friends

#### Update Working Copy

To get changes from the mirror into your working copy.

        svk up

#### Alt: Update Mirror & Working Copy

To get changes from the repo through your mirror into your working copy.
Effectively performs a svk sync and then and svk up in one step.

        svk up -s

Mirror mode + local branch
--------------------------

When using this approach the typical routine is “sync”, “merge”,
“update”, “modify”, “commit” repeat until ready to “submit”.

Your local branch will live in the depot alongside the mirror.

#### Create your local branch

(Assumes you have already followed the mirror steps above through the
sync).

[Branching](http://en.wikipedia.org/wiki/Branching_%28software%29 "Branching software")
in SVK is the same as in SVN:

        svk cp //projects/project-mirror //projects/project-local

#### Check out working copy from your local branch

Now you can check out code from your local working branch into your
working directory. For this, follow a similar procedure as that of SVN:

        mkdir project
        svk co //projects/project-local project
        or you can checkout just one branch
        svk co //projects/project-local/trunk project/trunk

#### Syncing

You will want to keep your mirror in sync with the repo. The operation
is automatic, but requires you to pull the trigger.

        svk sync //projects/project-mirror/

#### Merging

If there are any changes you will likely want to merge them into your
local branch.

        svk smerge //projects/project-mirror/ //projects/project-local/

#### Updating

Lastly update to pull the changes from the depot into your wc.

        svk up

Common operations.
------------------

#### Branching

        svk cp [existing_location] [new_location]

        example:
        svk cp http://host/svn/trunk http://host/svn/branches/steve
        or
        svk cp http://host/svn/branches/steve http://host/svn/branches/steve-branches/cleanup-templates

#### Push and Pull

Pull will import changes from the branch you branched from.<br>
 Push will send your changes to the branch your branched from.<br>
 This will happen directly on the repo, unlike smerge which operates
similarly, but on the depot only.

        svk push
        svk pull

These are meant to be run from within the wc.<br>
 Following the example above.

    $ cd branches/steve-branches/cleanup-templates

**svk push** would merge all changes made in the cleanup-templates
branch to the steve branch.

**svk pull** would take all the changes made in the steve branch and
merge them into the cleanup-templates branch.

*Directory structure isn’t important here, except to keep things sane.*

    $ cd branches/steve

**svk push** would merge all changes made in the steve branch to trunk.

**svk pull** would take all the changes made in trunk and merge them
into the steve branch.

    $ cd trunk

can’t push or pull. This is the top level.

#### Many of the standard svn commands are also available.

    svk add     svk rm     svk mv     svk mkdir     svk status     svk diff

Good Practices
--------------

You should NEVER just ‘svk add \*’ and ‘svk commit’ without checking
what you are committing. It shouldn’t be a surprise which files go to
the<br>
 repository.

The process when ready to commit should be:

       close out all of your open files

       svk up -s # pulls from the repo, not just the mirror
       svk diff  # carefully review your changes

Then either

       svk commit [ file1 ] [ file2 ]  ... [ filen ]
        or
       svk commit

without “-m” so you can remove unnecessary files in the commit message
screen.

See also:
---------

-   [http://goldenspud.com/rotr/index.php/2006/11/29/svk-in-a-nutshell/](http://goldenspud.com/rotr/index.php/2006/11/29/svk-in-a-nutshell/ "http://goldenspud.com/rotr/index.php/2006/11/29/svk-in-a-nutshell/")
-   [http://www.opensync.org/wiki/SVK](http://www.opensync.org/wiki/SVK "http://www.opensync.org/wiki/SVK")

