---
Description: ""
Keywords:
- Architecture
- Scalability
- Systems
- amazon
- aws
- cloudfront
- s3
Section: post
Slug: benchmarking-cloudfront-and-s3
Tags:
- amazon
- aws
- cloudfront
- s3
Thumbnail: /uploads/2010/01/3898v1-max-250x250.jpg
Title: Benchmarking Cloudfront (and S3)
Topics:
- Architecture
- Scalability
- Systems
Url: post/benchmarking-cloudfront-and-s3
date: 2010-01-19
disqus_identifier: 90 http://localhost/~sfrancia/wordpress/?p=90
disqus_title: Benchmarking Cloudfront (and S3)
disqus_url: http://spf13.com/post/benchmarking-cloudfront-and-s3/
---

{{% img src="/media/amazon-logo.jpg" class="right third" %}}

[Amazon](http://amazon.com/ "Amazon") has done it again bringing another
computing service to the masses. This time it’s the Content Delivery
Network
or [CDN](http://en.wikipedia.org/wiki/Content_delivery_network "Content delivery network").
Cloudfront is a direct competitor to other popular CDNs such
as [Akamai](http://www.akamai.com "Akamai"). While Akamai requires a
fairly substantial amount of traffic to become a customer, Cloudfront
doesn’t. It follows all of Amazons, pay for what you use mentality. This
means that everyone can benefit from incorporating Cloudfront into their
blog, site, store, etc..

For purposes of experimentation, I decided to track how much of a
difference Amazons Cloudfront made over
simple [s3](http://aws.amazon.com/s3 "Amazon S3") public hosting vs
hosting locally on my webhost. I decided to
use[stevefrancia.com](http://stevefrancia.com) for this experiment since
it is a very small and simple site with a single html file a couple css
and js files and a handful of images. No server side processing or other
significant variables, perfect for benchmarking.

The next series of images shows the improvement as I moved towards all
files (except the primary html file) on cloudfront.

*Note, the scale of the following images isn’t the same from one to the
other, please note the x-axis scale for each one*

Base Case
---------

[![Base
Case](/media/4177408474_84b5bc017b.jpg)](http://www.flickr.com/photos/spf13/4177408474/ "Base Case by steve.francia, on Flickr")

Google Hosted jQuery
--------------------

[![Google Hosted
jQuery](/media/4177410024_2403c41158.jpg)](http://www.flickr.com/photos/spf13/4177410024/ "Google Hosted jQuery by steve.francia, on Flickr")

Resources on S3
---------------

[![s3
hosted](/media/4176659019_e2ef2ff41c.jpg)](http://www.flickr.com/photos/spf13/4176659019/ "s3 hosted by steve.francia, on Flickr")

Resources on Cloudfront
-----------------------

[![cloudfront](/media/4177419138_25deb10527.jpg)](http://www.flickr.com/photos/spf13/4177419138/ "cloudfront by steve.francia, on Flickr")

Summary
-------

[![cloudfront-comparison](/media/4176646691_5ffb9216b5_o.png)](http://www.flickr.com/photos/spf13/4176646691/ "cloudfront-comparison by steve.francia, on Flickr")

Conclusion
----------

Cloudfront is a significant improvement over both my web host as well as
serving files directly from s3. Each case the single HTML file was
served from my web host. When you remove that from the totals (assuming
an average of .5 s for the index.html file) it shows an even larger
improvement. From just under 4 seconds in our base case, to around .4
seconds on cloudfront. Using cloudfront is easy and
inexpensive. [CloudFront](http://aws.amazon.com/cloudfront/ "CloudFront")
integration is a no brainer. It works well, easily integrates and is
inexpensive. Most people should use it to host all of their resources.

Of course this is a very small scale test and your mileage will vary,
pingdom is a good resource for simple tests like this as it produces the
graphs seen above and is easy to use.

## Related articles
-   [Amazon CloudFront Now Supports Streaming Access
    Logs](http://aws.typepad.com/aws/2010/05/amazon-cloudfront-supports-streaming-access-logs.html)
    (aws.typepad.com)
-   [Improving Global Application
    Performance](http://aws.typepad.com/aws/2010/05/improving-global-application-performance.html)
    (aws.typepad.com)
-   [How to configure Amazon CloudFront Streaming log with CloudBerry
    Explorer](http://teabreak.pk/how-to-configure-amazon-cloudfront-streaming-log-with-cloudberry-explorer-280/36329/)
    (teabreak.pk)

