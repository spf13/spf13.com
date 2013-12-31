{
	"disqus_url" : "http://spf13.com/post/windows-7-launch-notes/",
	"disqus_identifier" : "160 http://localhost/~sfrancia/wordpress/?p=160",
	"disqus_title" : "Windows 7 launch notes",
	"Title": "Windows 7 launch notes",
	"Description": "",
	"Keywords": [
		"Systems",
		"Tech Industry",
		"microsoft",
		"win 7",
		"windows"
	],
	"Tags": [
		"microsoft",
		"win 7",
		"windows"
	],
	"Pubdate": "2009-10-20",
	"Topics": [
		"Systems",
		"Tech Industry"
	],
	"Url": "post/windows-7-launch-notes",
	"Slug": "windows-7-launch-notes",
	"Section": "post",
	"Thumbnail": "/uploads/2009/10/21545v2-max-250x250.png"
}
{{% img src="/media/windows-logo.png" class="third right" %}}

I was fortunate to be able to attend
the [Microsoft](http://www.microsoft.com "Microsoft") Launch Developer
Preview meeting in NYC.
[Microsoft](http://www.microsoft.com "Microsoft") is holding these all
over the country to prepare IT and developers for the upcoming launch.
Overall it was a good meeting and Microsoft is delivering a great
product. More importantly they have a really good chance of overcoming
the bad taste of vista and emerge as a innovation leader. These are my
notes taken during the meeting with some of my insights.

Windows 7
---------

windows mail, movie maker now separate downloadable install

ribbon interface now part of the os and available to all developers.

windows 7′s official version number isn’t 7, it’s 6.1. it seems like
it’s vista.1 with a reboot of the branding.

For the first time in the history of windows we have a new version that
takes less resources than the prior version.

new troubleshooting feature. powered by the power shell which is now
part of the os.

new feature.  libraries. it’s a collection of folders. don’t have to
share a physical root. really like a group of symlinks.

available to all developers. under the covers a library is just an XML
file. though it’s simple it actually seems really useful. can view
entire library in one
[window](http://www.microsoft.com/WINDOWS "Windows"). can search in a
library.

Peter lau. the presenter has [amazon
mp3](http://www.amazonmp3.com "Amazon MP3") folder in his music library.
I guess it’s better than
an [iTunes](http://www.apple.com/itunes/ "ITunes") one…nevermind, he has
an iTunes one too.

[visual
studio](http://msdn.microsoft.com/vstudio/ "Microsoft Visual Studio")
2008. need [win
7](http://windows.microsoft.com/en-US/Windows7/Home/ "Windows 7") sdk.
windows API code pack .net wrappers for the c++, c wrappers.

New windows taksbar is the biggest visual difference in 7. seems like a
blend of the windows launcher and the mac dock. actually seems much more
useful than the dock.

With snow leopard and win 7 it really seems like operating systems have
matured. look for much more iterative releases to come. more frequent
smaller releases with more refinement.

Windows 7 Interaction and Interface
-----------------------------------

win7 window manager uses 3d card consumes 50% less per window.

Windows 7 has contextual fonts through direct write. <br>
Certain fonts characters appear differently based on context. Garamond
is one of these fonts. when two “L” characters are next to each other
rendered differently. really cool stuff.

Sensor platform is really a standard unified API for all sensor devices
including motion ( think wiimote ), location ( gps, network ),
tempature, light, etc.

xna framework for .net or c++ permits you to develop for windows 7 and
xbox both using the sensor platform. demo is a racing game.also demoed a
3d pacman like game “chomp”

windowsAPIcodepack.Sensors <br>
location sensor is really important. gps, wifi, cell tower
triangulation, ip resolver,  default location.  all acceptable through
sensor location.we can really build location aware apps, just like
the[iPhone](http://www.apple.com/iphone "iPhone").

widgets are location aware. weather, places ( similar to yelp, searches
on bing )

ribbon interface

Now separating business logic from presentation for the code. Ribbon now
crafted via XML.

windows key + or – zooms in in windows 7… just like mac has with cmd and
mouse.

Big deal is the multitouch functionalty in windows 7. Called windows
touch. Multitouch great for conuning content, not so much for creating
content. given all I do with my iPhone, not sure I agree, though I do
agree that multitouch works very well when onsuming content.

Word 2010 version ( and windows 7 in general ) has gestures built in.

with supporting hardware it’s very similar to iPhone gestures. pinch to
zoom. swipe to scroll. right clck events on second click, rotate. 
definitely not as smooth as apples implementation. Though available on
laptops and tablets, so a leg up
until [apple](http://www.apple.com "Apple") releases their fabled
tablet. Basic gestures available to developers via the WM\_GESTURE
message.custom touch available also through a WM\_TOUCH message.

Basic tenants of Microsoft is every 15 years thy update the applications
bundles with the os whether they need it or not. Now demoing multitouch
aware MS paint. Paint also has the ribbon interface now.

Demos
Microsoft [surface](http://www.microsoft.com/surface/ "Microsoft Surface")
collage. This interaction is very smooth and nice. he is playing with
photos on a table as if it was real.

Bumptop
new interface reproduces a real desktop. Uses all five fingers for
input. Seems really interesting, but makes me wonder how it works with
the hundreds of thousands of files and hundreds of programs.
