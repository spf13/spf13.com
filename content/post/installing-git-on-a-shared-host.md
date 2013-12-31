{
	"disqus_url" : "http://spf13.com/post/installing-git-on-a-shared-host/",
	"disqus_identifier" : "186 http://localhost/~sfrancia/wordpress/?p=186",
	"disqus_title" : "Installing Git on a Shared Host",
	"Title": "Installing Git on a Shared Host",
	"Description": "",
	"Keywords": [
		"Development",
		"Systems",
		"1and1",
		"git",
		"godaddy"
	],
	"Tags": [
		"1and1",
		"git",
		"godaddy"
	],
	"Pubdate": "2009-11-24",
	"Topics": [
		"Development",
		"Systems"
	],
	"Url": "post/installing-git-on-a-shared-host",
	"Slug": "installing-git-on-a-shared-host",
	"Section": "post",
	"Thumbnail": "/uploads/2009/11/256px-Git_icon.svg.png"
}

{{% img src="/media/git-logo.png" class="third right" %}}


[Git](http://git-scm.com/ "Git") is a fantastic tool and is
very useful for deployment. If you can’t install git system wide or
don’t want to mess with installing it on the entire system here is an
easy way to install it for a single user. This also works well on [Mac
OS X](http://apple.com/macosx/ "Mac OS X") where installing git is more
challenging than necessary. Script included

I used this script to install git on 1and1. The same script should work
anywhere with no or little modification.

### Preparation

Goto [http://git-scm.com/download](http://git-scm.com/download) and get
the link to the latest git release.

### Script

You should be able to just copy and paste this (replacing the link with
the one from git-scm.com)

~~~~ {.brush: .bash}
mkdir git-download mkdir -p $HOME/bin/git
cd git-download
wget http://kernel.org/pub/software/scm/git/git-1.6.5.tar.gz # replace with your link
tar -xzf git-1.*.tar.gz
cd git*
./configure --prefix=$HOME/bin/gitlib
make
make install
echo 'PATH=$PATH:$HOME/bin/gitlib/bin/'  > ~/.bash_profile
echo 'export PATH=$PATH:$HOME/bin/gitlib/bin:$HOME/bin/gitlib/libexec/git-core'  > ~/.bashrc
PATH=$PATH:$HOME/bin/gitlib/bin
~~~~

## Related articles

-   [Beginner’s Guide to
    Git](http://maketecheasier.com/beginners-guide-to-git/2010/03/11)
    (maketecheasier.com)
-   [Git Machine](http://www.slideshare.net/err/git-machine)
    (slideshare.net)
-   [Version Control
    Systems](http://wknight8111.blogspot.com/2009/09/version-control-systems.html)
    (wknight8111.blogspot.com)
-   [The Five Commandments of Version
    Control](http://www.basilv.com/psd/blog/2009/the-five-commandments-of-version-control)
    (basilv.com)

