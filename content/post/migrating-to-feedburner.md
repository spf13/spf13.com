{
	"disqus_url" : "http://spf13.com/post/migrating-to-feedburner/",
	"disqus_identifier" : "148 http://localhost/~sfrancia/wordpress/?p=148",
	"disqus_title" : "Migrating to Feedburner",
	"Title": "Migrating to Feedburner",
	"Description": "",
	"Keywords": [
		"Drupal",
		"feed",
		"feedburner"
	],
	"Tags": [
		"Drupal",
		"feed",
		"feedburner"
	],
	"Pubdate": "2009-10-12",
	"Topics": [
		"Blogging"
	],
	"Url": "post/migrating-to-feedburner",
	"Slug": "migrating-to-feedburner",
	"Section": "post",
	"Thumbnail": "/uploads/2009/10/3292v1-max-250x250.png"
}

{{% img src="/media/feedburner-logo.png" class="third right" %}}

I’ve made the decision to take control of my feeds. I want to know how
many users are reading my blog via syndication so I’ve decided to move to
feedburner. The migration will be seamless for all readers. Additionally
I’ll be able to provide syndication via email as well.

How to Migrate from [Drupal](http://www.drupal.org "Drupal") to [FeedBurner](http://www.feedburner.com/ "FeedBurner")
---------------------------------------------------------------------------------------------------------------------

These directions are written with Drupal in mind, though the approach
used would work for pretty much any system. All we need to do is 3
simple steps.

### 1. Move the feeds location to a hidden location for feedburner to read

In drupal this is really easy. Just create a url alias from rss.xml to
another feed name like “FeedBurnerHiddenFeed”

[![Drupal :
FeedBurnerHiddenFeed](/media/4004338853_f019ea05db.jpg)](http://www.flickr.com/photos/spf13/4004338853/ "Drupal : FeedBurnerHiddenFeed by steve.francia, on Flickr")

### 2. Tell feedburner to read this hidden location

Either create a new feed, or edit your existing one. Simply put the new
location in for the feed location.

[![FeedBurner
settings](/media/4005101754_35a6cf01e7.jpg)](http://www.flickr.com/photos/spf13/4005101754/ "FeedBurner settings by steve.francia, on Flickr")

### 3. Write an .htaccess rule to redirect requests to feed to the feedburner feed.

    <ifmodule mod_rewrite.c>
    RewriteEngine on
    RewriteCond %{HTTP_HOST} \^spf13.com\$
    RewriteRule rss.xml http://feeds.feedburner.com/spf13 [R,L]
    RewriteCond %{HTTP_HOST} \^spf13.com\$
    RewriteRule node/feed http://feeds.feedburner.com/spf13 [R,L]
    </ifmodule>


