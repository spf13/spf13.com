---
Description: How to fully automate the backup of a MySQL database system.
Keywords:
- archive
- backup
- mysql
Section: post
Slug: backing-up-mysql
Tags:
- archive
- backup
- mysql
Thumbnail: /uploads/2010/10/300px-MySQL.svg_.png
Title: Backing up MySQL
Topics:
- Systems
Url: post/backing-up-mysql
date: 2008-12-12
disqus_identifier: 232 http://localhost/~sfrancia/wordpress/?p=232
disqus_title: Backing up MySQL
disqus_url: http://spf13.com/post/backing-up-mysql/
---

{{% img src="/media/MySQL.png" class="third right hid" caption="Image via Wikipedia" %}}

I don’t know very many people that haven’t been devastated by the loss
of data… Yet I am baffled that millions of professional IT workers still
ignore backing up their data. Since computers are great at doing
repetitive things
like [backups](http://en.wikipedia.org/wiki/Backup "Backup").. why not
spend 20 minutes setting up your machine to backup your files for you.
This guide will be specific to [mysql](http://www.mysql.com "MySQL") to
create a local copy of the backup. Then read my other guide about
copying files securely to a remote backup server for the 2nd part.

Hopefully you are using \*nix. If so then you have some great utilities
already available to you.[Rsync](http://rsync.samba.org/ "Rsync"),
SSH, [Tar](http://en.wikipedia.org/wiki/Tar_%28band%29 "Tar (band)"),
Bash and Cron can produce elegant solutions.

The Setup
=========

Create Backup User
------------------

First thing to do is to create a **Read Only** mysql user to perform the
backups. Optionally a second recovery user can also be created. It isn’t
advisable to perform backups as the root user as common sense and proper
procedures dictate that a user should always have the minimum privilages
necessary to accomplish the job.

Example: Run the following command at the mysql prompt when logged in as
root to grant the minimal privilages needed.

`GRANT LOCK TABLES, SELECT, FILE, RELOAD, SUPER ON *.* TO 'db-backup'@'localhost' IDENTIFIED BY 'really-long.and Varied p@$$wrd';`{.code}

Install Your Backup Script
--------------------------

There is a fantastic mysql backup script that is really easy to use and
simply wraps the mysql backup utilities with nice features like daily,
weekly, and monthly backups. Cycling and optionally emailing a summary
of the backup.

### Download

Go here to
download [automysqlbackup](http://sourceforge.net/projects/automysqlbackup/)

### Install

Install it by copying it to a good location. I use /usr/local/sbin/ or
/usr/local/bin depending on if I am an admin on the system, or just a
user on a shared host.

make sure to set the permissions as executable.

`# chmod +x automysqlbackup`

### Configure

Simply edit the shell script with your favorite editor. If you don’t
have one, permit me to recommend VIM

    # vim /usr/local/sbin/automysqlbackup.sh

    #===================================================================== 
    # Set the following variables to your system needs 
    # (Detailed instructions below variables) 
    #=====================================================================
    # Username to access the MySQL server e.g. dbuser 
    USERNAME=db-backup
    # Username to access the MySQL server e.g. 
    password PASSWORD=that-secure password set earlier
    # Host name (or IP address) of MySQL server e.g localhost 
    DBHOST=localhost
    # List of DBNAMES for Daily/Weekly Backup e.g. "DB1 DB2 DB3" 
    DBNAMES="all" 
    # OR NAME THEM WITH SPACES SEPARATING
    # Backup directory location e.g /backups 
    BACKUPDIR="/usr/local/backup/mysql" 
    # I LIKE THIS DIRECTORY, JUST MAKE SURE PERMISSIONS ARE SET PROPERLY
    # Mail setup 
    # What would you like to be mailed to you? 
    # - log : send only log file 
    # - files : send log file and sql files as attachments (see docs) 
    # - stdout : will simply output the log to the screen if run manually. 
    # - quiet : Only send logs if an error occurs to the MAILADDR. 
    MAILCONTENT="stdout"
    # Set the maximum allowed email size in k. (4000 = approx 5MB email [see docs]) 
    MAXATTSIZE="4000"
    # Email Address to send mail to? (
    MAILADDR="email@address.com"

Setup Cron to run nightly
-------------------------

create a new file in /etc/cron.daily/ and place these contents into it..

    # vim /etc/cron.daily/mysql-backup

`#!/bin/bash /usr/local/bin/automysqlbackup 2>&1`

Make sure it is executable.

    # chmod +x /etc/cron.daily/mysql-backup

I usually test it simply run that cron file from the command line.

    # /etc/cron.daily/mysql-backup

Conclusion
----------

Remember that a backup is only as good as it's restore. What we have done here should be considered
the bare minimum and will result in some data loss if it's needed.. How much data loss? 
Up to one days worth of changes as that's how frequently we are backing up things.
If we wanted to shrink that window then run the script more often, but recognize that cost for this
is the data retained will grow in size.
