---
Description: ""
Keywords:
- Ecommerce
- Scalability
- Tech Industry
Section: post
Slug: hybrid-cloud-computing
Tags: []
Thumbnail: ""
Title: Hybrid Cloud Computing
Topics:
- Ecommerce
- Scalability
- Tech Industry
Url: post/hybrid-cloud-computing
date: 2011-09-30
disqus_identifier: 1534 http://spf13.com/?p=1534
disqus_title: Hybrid Cloud Computing
disqus_url: http://spf13.com/post/hybrid-cloud-computing/
---

Traditionally ecommerce companies have had no place in the cloud. The
lack of established standards, multi-tenancy nature and need to be PCI
compliant have been three large barriers to entry for any organization
exploring this possibility. Recently many e-commerce companies
(including OpenSky) have begun to implement a hybrid approach to
infrastructure mixing traditional data centers with cloud offerings to
achieve a best of both worlds solution.

Here is how I approached this when I was at OpenSky.

# 1. Databases on Metal


For certain operations operating directly on servers in your own data
centers still makes sense. IO heavy operations such as databases
continue to see considerably better performance benefits from operating
directly on the hardware. Additionally these machines benefit from
specifically tuned hard drives and controllers built with higher IO in
mind. For all the right reasons, the virtualized and commoditized cloud
can’t and won’t compete here, it’s just not cost effective for them to
do so.

# 2. Vital in house

I’ve been a cloud customer far too long to depend on it’s reliability.
Cloud servers can and will fail. It’s been my experience that this
happens at a much higher rate than traditional servers. When uptime is
the most essential, a traditional approach will serve you better.

# 3. Appendages in the cloud

I’ve always been a big believer in using the best tool for the job. Use
the cloud for what it’s built to do. Not everything is vital. There are
many supporting pieces of your infrastructure where perfect uptime isn’t
critical. What the appendages are will depend entirely on your business.
At OpenSky we currently operate our blog and marketing servers on EC2.
We leverage S3 for archival backups. We utilize email delivery servers
on the cloud. This is a small set of what we will eventually have there,
but it provides a good insight into our approach.

# 4. Scale in the cloud

By operating a core selection of servers in house it enables us to scale
up our web nodes in the cloud. Since our ecommerce application isn’t
particularly database heavy (thanks in large part to mongoDB) our
scalability bottleneck is on our web servers. Keeping a core set of them
in house to handle things like checkout and administrative operations
permits us to scale the bulk of our traffic to the cloud.

Currently [HP](http://www.hpcloud.com/) and
[Rackspace](http://www.rackspace.com/) are two companies that are
providing turnkey hybrid cloud computing offerings.

Words and Ideas are my own. This post is sponsored by [Enterprise CIO
Forum](http://bit.ly/l2GOwA) and [HP](http://www.hp.com/go/instant-on)

## Related articles

-   [Competition for the Cloud Heats
    Up](http://spf13.com/post/competition-for-the-cloud-heats-up "Competition for the Cloud Heats Up")
    (spf13.com)
-   [CIOs not fretting about cloud
    security](http://www.enterprisecioforum.com/en/article/cios-not-fretting-about-cloud-security-0?utm_source=B5&utm_medium=USBLOG&utm_content=post&utm_campaign=ecf) (CIO
    Enterprise Forum)
-   [HP Cloud Strategy, 3 pillars to address varying
    needs](http://www.enterprisecioforum.com/en/blogs/christian/hp-cloud-strategy-3-pillars-address-varying-needs?utm_source=B5&utm_medium=USBLOG&utm_content=post&utm_campaign=ecf) (CIO
    Enterprise Forum)

