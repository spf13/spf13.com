---
Description: ""
Keywords:
- wordpress
- blogging
- github
- development
- coding
Slug: github code viewer
Tags:
- wordpress
- blog
- github
Title: GitHub Code Viewer 2 for WordPress
Topics:
- Development
date: 2012-02-13
---

GitHub Code Viewer 2 automatically  pulls a file from github and places into any post using a shortcode [github_cv url='$url']
Caches locally (in db), so there isn't a performance hit.
Heavily Modified from original plugin by Matt Curry http://www.pseudocoder.com

## Installation 

1. Upload `GitHub_Code_Viewer.php` to the `/wp-content/plugins/` directory
2. Activate the plugin through the 'Plugins' menu in WordPress
3. Use the shortcode [github_cv url='<URL TO FILE ON GITHUB>'] in your post.

## Changelog 

#### 2.0

* Rewrote as a static class as only one instance is needed. 
* Rewrote to use short codes rather than a filter. 
* Cleaned up code and organized a bit better. 
* Allowed ttl as a configurable setting. 
