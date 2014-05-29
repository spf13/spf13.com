---
Description: ""
Keywords:
- Development
- Systems
- cli
- ssh
- subversion
- svn
Section: post
Slug: setting-up-subversion-with-multiple-access-methods
Tags:
- cli
- ssh
- subversion
- svn
Thumbnail: ""
Title: Setting up Subversion with multiple access methods
Topics:
- Development
- Systems
Url: post/setting-up-subversion-with-multiple-access-methods
date: 2009-05-05
disqus_identifier: 244 http://localhost/~sfrancia/wordpress/?p=244
disqus_title: Setting up Subversion with multiple access methods
disqus_url: http://spf13.com/post/setting-up-subversion-with-multiple-access-methods/
---

One thing that
makes [subversion](http://subversion.tigris.org/ "Subversion")
such a powerful revision system is it’s ability to permit multiple
methods of access. Https, WebDAV, SSH and
svnserve. In spite of svn’s ability to support multiple access methods,
doing so simultaniously can be quite challenging. Typically one will run
into permission issues as the http(s) access will all be written to the
filesystem as the user running the webserver.
The SSH access will all write to the filesystem under each users given account.

Here is one approach to permit both.

1.  Place all your ssh+svn users into the webserver group (often www).
2.  Make all the desired respositories owned by that group.
3.  Change the
    group [permissions](http://en.wikipedia.org/wiki/File_system_permissions "File system permissions")
    to rw
4.  If using svnserve:
    The users need a
    sane [umask](http://en.wikipedia.org/wiki/Umask "Umask") for
    accessing the repository. Make sure the svnserve
    executible (commonly found at /usr/bin/svnserve) is a wrapper script
    that runs umask 002 and executes the real svnserve binary.

The necessary commands could look like this

    # cd /var/svn/repos
    # chown -R wwwrun:www .
    # chmod -R g+rw .

Paths and groups would need to be adjusted for your system.
