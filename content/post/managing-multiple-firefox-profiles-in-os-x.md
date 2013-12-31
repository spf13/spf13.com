{
	"disqus_url" : "http://spf13.com/post/managing-multiple-firefox-profiles-in-os-x/",
	"disqus_identifier" : "155 http://localhost/~sfrancia/wordpress/?p=155",
	"disqus_title" : "Managing Multiple Firefox Profiles in OS X",
	"Title": "Managing Multiple Firefox Profiles in OS X",
	"Description": "Sometimes you need more than one profile in Firefox. This post will show you how to manage multiple profiles in Firefox.",
	"Keywords": [
		"firefox",
		"mac",
		"OS X",
		"profile",
		"script"
	],
	"Tags": [
		"firefox",
		"mac",
		"OS X",
		"profile",
		"script"
	],
	"Pubdate": "2008-08-27",
	"Topics": [
		"Personal"
	],
	"Url": "post/managing-multiple-firefox-profiles-in-os-x",
	"Slug": "managing-multiple-firefox-profiles-in-os-x",
	"Section": "post",
	"Thumbnail": "/images/858_300px-Firefox_3.5_logo.png-200x200.png"
}

{{% img src="/media/Firefox_3.5_logo.png" caption="Image via Wikipedia" class="hid third right" %}}


One of the great features of
[Firefox](http://www.mozilla.com/en-US/firefox/ "Firefox") is the
ability to manage multiple profiles. This is a very handy feature with
many different uses. Unfortunately, it isn’t easy to do on a
[mac](http://apple.com/macosx/ "Mac OS X"). I will show you how to setup
multiple profiles on a mac that appear and run like normal mac
applications so you can click on them and run them from quicksilver.

*UPDATED 10/16/09 : Now working with Snow Leopard!*

Firefox is a great browser in any operating system. One of the great
features of Firefox is the many extensions that can alter or add
functionality to the browser. If you are like me, you use quite a few
extensions. While these extensions make life easier, they also slow down
firefox. I use two different profiles, one with all my extensions
loaded, which I use for work. And one without any extensions which I use
for light browsing, watching videos and checking mail.

Setting up your profiles
------------------------

{{% img src="/media/2805197674_ea2ba50cf8_o.jpg" %}}

So we will use the Terminal, but just once here. Fire up the Terminal,
it is found in *Applications \<\< Utilities \< \< Terminal*. And run the
following:

    /Applications/Firefox.app/Contents/MacOS/firefox-bin --profilemanager

{{% img src="/media/2805184392_3e37c90c6a_o.jpg" %}}

A window will appear. Create your profiles. I created two called “Heavy”
and “Lite”. Whatever you call your pofiles, write it down and remember
the names are case sensitive.

Creating the scripts
--------------------

You will want to repeat the following for each of your profiles

1.  Open the script editor
2.  Add the following line replacing profileName with your profile name.

    do shell script "/Applications/Firefox.app/Contents/MacOS/firefox-bin -P profileName"

3.  Save the script as an Application Bundle. I called mine FFHeavy
    which seems to work well
4.  Control-click the icon \< Show Package Contents. A “Contents” window
    will appear.
5.  Edit the file *Contents \< Info.plist* with your favorite editor
6.  Look for the entry \< key\>LSRequiresCarbon\</key\> \<true/\>
7.  Add these two lines after that entry.

    <key>LSUIElement</key>
    <string>1</string>

8.  Save the Script

{{% img src="/media/2805187776_19ed9d70f8_o.jpg" %}}

Changing the Icon
-----------------

{{% img src="/media/2805178960_bf4598da72_o.jpg" %}}

By default your newly created script will have a “script” icon, not all
all representative of what it does. Let’s change that to a more relevant
icon.

You can use any image you want. I found a good one
on [gnome-look](http://www.gnome-look.org/content/show.php/Firefox+Icons?content=47617).
Unfortunately OS X requires icons to be in the icns format. There is a
handy Opensource application that can turn images into icns
files. [img2icns from
shinyfrog](http://www.shinyfrog.net/en/software/img2icns/). Png files
work well as they are already 24 bit and transparent.

Run img2icns and drag your png file(s) onto the dock icon for img2icns.
It will place the newly created icns file on the Desktop by default.
“Get Info” on the script you created and drag the icon onto the icon
towards the top of the get info window.

You now have a working icon and alias/script/shortcut to your profile
