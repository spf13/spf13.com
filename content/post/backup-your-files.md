---
Description: This article will show you how to automatically backup your files often
  and automatically.
Keywords:
- backup
- cli
- Linux
- mysql
- Shell script
Section: post
Slug: backup-your-files
Tags:
- backup
- cli
- Linux
- mysql
- Shell script
Thumbnail: ""
Title: Backup Your Files
Topics:
- Systems
Url: post/backup-your-files
date: 2008-12-29
disqus_identifier: 264 http://localhost/~sfrancia/wordpress/?p=264
disqus_title: Backup Your Files
disqus_url: http://spf13.com/post/backup-your-files/
---

One of the worst experiences you can have as a computer operator is to
realize you (or something else) just did something and wiped out your
files. The purpose of this article is to show you how to automatically
backup your files often and automatically. I use this setup to backup my
documents every hour (I save more often then that). This gives me hourly
versions of all my files I am working on. It even protects me from
accidentally saving over an important document (at least to the last
hour).

Install Rsync-incr
==================

You could do everything you need with Rsync… but our goal here is easy
and automatic. Rsync-incr is a nice shell script that uses Rsync to do
incremental backups, surrounding it with an easy interface. Win Win..
The stability of Rsync, with an easy to use interface.

### Download

Go here to
download [Rsync-incr](http://colas.nahaboo.net/Software/RsyncIncr)

### Install

Install it by copying it to a good location. I use /usr/local/sbin/ or
/usr/local/bin depending on if I am an admin on the system, or just a
user on a shared host.

make sure to set the permissions as executable.

    # chmod +x rsync-incr

Setup Cron to run hourly (or more often)
========================================

create a new file in
/etc/cron.hourly/ and place
these contents into it..

    # vim /etc/cron.hourly/myDocuments-backup

Now it’s time to configure your backups.. I usually place my backups on
a different drive. On my system /home is one drive and / is my other
(each have multiple few partitions).

the syntax is **rsync-incr \<options\> N From To**
 N = the maximum number of copies to keep.
 N with ‘m’ after is (eg 50m) will keep the backups below that size
requirement

We use the option –snap. This will create incremental copies with the
appearance of full copies (by using hard links).

`#!/bin/bash path=/usr/local/bin myfiles=/home/sfrancia/documents backupPath=/usr/local/backup/home/sfrancia/documents $path/rsync-incr --snap 48 $myfiles $backupPath 2>&1`

Make sure it is executable.

    # chmod +x /etc/cron.hourly/myDocuments-backup

I usually test it simply run that cron file from the command line.

    # /etc/cron.hourly/myDocuments-backup

Restoring a Backup
==================

To restore a backup, use standard rsync (trailing slashes are
IMPORTANT):

    # rsync -HSax --delete --force backup / original /

Related articles<br>

-   [Backing up MySQL](http://spf13.com/feature/backing-mysql)
-   [Bidirectional filesystem syncing – DirSync Pro vs.
    Unison](http://www.linux.com/feature/154149)
-   [gzip and hard links. I don’t get
    it.](http://jeremy.zawodny.com/blog/archives/010745.html)

