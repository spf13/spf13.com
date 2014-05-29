---
Description: ""
Keywords:
- Blogging
- php
- github
- PHP
- plugins
- WordPress
Section: post
Slug: wp-github-code-viewer
Tags:
- github
- PHP
- plugins
- WordPress
Thumbnail: /images/1167_github-logo.png-200x200.png
Title: WP GitHub Code Viewer
Topics:
- Blogging
- php
Url: post/wp-github-code-viewer
date: 2010-12-09
disqus_identifier: 1162 http://spf13.com/?p=1162
disqus_title: WP GitHub Code Viewer
disqus_url: http://spf13.com/post/wp-github-code-viewer/
---

{{% img src="/media/github-logo.png" class="right third" alt="github" %}}

GitHub Code Viewer 2 is a plugin for wordpress that will automatically
pull a file from github and place into any post using a shortcode
[github\_cv url='$url']. It caches the code locally (in db), so it’s
quite fast and can be even faster when combined with wp\_super\_cache or
w3c\_total\_cache. It will re-request the code from github every 24
hours (by default, but it’s configurable) so the code in your post will
always remain up to date. It is a heavily modified version of the
original GitHub Code Viewer plugin written by Matt Curry
http://www.pseudocoder.com.

**Installation**
----------------

1.  Upload \`GitHub\_Code\_Viewer.php\` to the \`/wp-content/plugins/\`
    directory (or install through the ‘add new’ functionality in
    wordpress)
2.  Activate the plugin through the ‘Plugins’ menu in WordPress
3.  Use the shortcode [github\_cv url='\<URL TO FILE ON GITHUB\>'] in
    your post.

**Usage**
---------

1.  Find a given file on github you want to include in a blog post /
    page.
2.  Grab the url to this page.
3.  Place this code in your post [github\_cv url='\<THE URL\>'] where
    you want the file to appear.
4.  *Optionally* provide a different TTL (time to live), default is ’1
    day’. This will be passed to str\_to\_time, so pass in whatever it
    would accept. This would look like:
     [github\_cv url='\<URL\>' ttl='1 week']
5.  *Optionally* surround the code with a syntax highlighter. ColorCoder
    is a good one which uses the geshi library.

**Example**
-----------

[github\_cv
url='https://github.com/spf13/wp\_GitHub\_Code\_Viewer/blob/master/GitHub\_Code\_Viewer.php']

