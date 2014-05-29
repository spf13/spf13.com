---
Description: ""
Keywords:
- Development
- Systems
- keychain
- rsa
- ssh
- Ssh-agent
Section: post
Slug: secure-automated-key-based-ssh
Tags:
- keychain
- rsa
- ssh
- Ssh-agent
Thumbnail: /uploads/2009/12/300px-Crypto_key.svg.png
Title: Secure Automated, Key Based SSH
Topics:
- Development
- Systems
Url: post/secure-automated-key-based-ssh
date: 2009-12-19
disqus_identifier: 165 http://localhost/~sfrancia/wordpress/?p=165
disqus_title: Secure Automated, Key Based SSH
disqus_url: http://spf13.com/post/secure-automated-key-based-ssh/
---

{{% img src="/media/key.png" class="third right" %}}

SSH is great and secure… Unless you need to automate it. Then it sucks
because your only options are to create a passwordless key, or login add
your key
to [ssh-agent](http://en.wikipedia.org/wiki/Ssh-agent "Ssh-agent"), stay
logged in forever. Here’s a quick guide to having the best of both
worlds. A Secure SSH Connection that can be used in automated scripts. (
with the single catch, that upon reboot you need to re-enter your key’s
password ) Create and Distribute your Key

First create an SSH key like so:

    ssh-keygen -t rsa

When prompted for a password use something long varied and secure

When ssh-keygen is done you should see a message like:

    Your identification has been saved in /home/yourusername/.ssh/id_rsa.
    Your public key has been saved in /home/yourusername/.ssh/id_rsa.pub.

Our public key needs to be moved to the web server. SSH is the best way
to do this, and here is a neat 1 liner that can do it all from the
machine you are currently on. ***Please substitute your username and
server***

    cat ~/.ssh/id_rsa.pub | ssh [username]@[server] 'cat >> .ssh/authorized_keys'

Make sure the following files and directories have the right settings
(assuming your username is ‘foo’)

      File or Directory          User   Group   Permissions
      -------------------------- ------ ------- -------------
      ~/.ssh                    foo    users   700
      ~/.ssh/authorized_keys   foo    users   644
      ~/.ssh/id_rsa.pub        foo    users   644
      ~/.ssh/id_rsa            foo    users   600

or just use this all purpose one liner.
It copies the key over and sets permissions correctly and symlinks
authorized\_keys2 to authorized\_keys (sometimes SSHD is configured that
way.

    cat ~/.ssh/id_rsa.pub | ssh [username]@[server] 'cat >> .ssh/authorized_keys; chmod 644 $HOME/.ssh/authorized_keys; ln -s $HOME/.ssh/authorized_keys $HOME/.ssh/authorized_keys2; chmod 700 $HOME/.ssh; chmod 644 $HOME/.ssh/id_rsa.pub; chmod 600 $HOME/.ssh/id_rsa'

Great, now we have substituted one password for another one. But at
least we are still secure.

Automating your password with KeyChain and SSH-Agent
====================================================

You likely already have SSH-Agent, since it is distributed with SSH, but
you need Keychain. Keychain was developed by the founder of the Gentoo
Linux distribution and is an elegant solution to this problem. Keychain
is a better solution than the alternatives because it only requires you
setup one ssh-agent per user, rather than one per session. This makes it
acceptable for use in automated scripts.

Installing keychain
-------------------

Keychain can be found here . There are links to may different packages,
so it should be easily installable on your distro. Since
I use [SuSE](http://www.opensuse.org/ "SUSE Linux distributions"), i
grabbed the rpm and installed it with

    # wget http://agriffis.n01se.net/keychain/keychain-2.6.8-1.noarch.rpm
    # rpm -Uvh keychain-2.6.8-1.noarch.rpm

Setting up keychain
-------------------

Now that we have keychain installed we need to add it to our
\~/.bash\_profile.<br>
 Here’s a good standard keychain-enabled \~/.bash\_profile straight from
the author himself, with a bit of an update to make it compatible with
an updated version of keychain.

    #!/bin/bash
    #on this next line, we start keychain and point it to the private keys that #we'd like it to cache
    /usr/bin/keychain ~/.ssh/id_rsa ~/.ssh/id_dsa
    source ~/.keychain/${HOSTNAME}-sh > /dev/null
    #sourcing ~/.bashrc is a good thing
    source ~/.bashrc

Now log out and log back in. Now keychain will run and will start
ssh-agent for you. It will record what it needs to in a global way (not
attached to your session but in \~/.keychain/), lastly it will prompt
you for passphrases for any of your private keys (your \~/.ssh/id\_rsa
file).

The whole process will look like this…

    KeyChain 2.6.8; http://www.gentoo.org/proj/en/keychain/
    Copyright 2002-2004 Gentoo Foundation; Distributed under the GPL

     * Found existing ssh-agent (29526)
     * Warning: can't find /root/.ssh/id_dsa; skipping
     * Adding 1 ssh key(s)...
    Enter passphrase for /root/.ssh/id_rsa:
    Identity added: /root/.ssh/id_rsa (/root/.ssh/id_rsa)

Now log out and log back in again.

    KeyChain 2.6.8; http://www.gentoo.org/proj/en/keychain/
    Copyright 2002-2004 Gentoo Foundation; Distributed under the GPL

     * Found existing ssh-agent (29526)
     * Warning: can't find /root/.ssh/id_dsa; skipping
     * Known ssh key: /root/.ssh/id_rsa

Notice how it didn’t prompt you for your password again. Pretty cool,
huh… And you can use this in scripts run by cron as well.

Using keychain from cron
========================

To use ssh or scp commands from your shell scripts and cron jobs, just
make sure that they source your ~/.ssh-agent file first:

    source ~/.keychain/${HOSTNAME}-sh

Then, any following ssh or scp commands will be able to find the
currently-running ssh-agent and establish secure passwordless
connections just like you can from the shell.

## Related articles

-   [startKeychain – bash utility to start
    ssh-agent](http://www.gubatron.com/blog/2010/06/03/startkeychain-bash-utility-to-start-ssh-agent/)
    (gubatron.com)

