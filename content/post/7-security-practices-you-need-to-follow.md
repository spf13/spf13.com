{
	"disqus_url" : "http://spf13.com/post/7-security-practices-you-need-to-follow/",
	"disqus_identifier" : "124 http://localhost/~sfrancia/wordpress/?p=124",
	"disqus_title" : "7 security practices you need to follow",
	"Title": "7 security practices you need to follow",
	"Description": "",
	"Keywords": [
		"Development",
		"Leadership",
		"Systems",
		"security"
	],
	"Tags": [
		"security"
	],
	"Pubdate": "2009-12-22",
	"Topics": [
		"Development",
		"Leadership",
		"Systems"
	],
	"Url": "post/7-security-practices-you-need-to-follow",
	"Slug": "7-security-practices-you-need-to-follow",
	"Section": "post",
	"Thumbnail": "/uploads/2009/12/300px-HK_Souvenir_Bank_of_East_Asia_MPF_USB_Flash_Drive_a.jpg"
}
{{% img src="/media/usbkey.jpg" class="half right" %}}

Some of this may seem like a broken record, yet every single time you
hear about a bank losing millions of customer data, or a company having
a [security
breach](http://en.wikipedia.org/wiki/Computer_security "Computer security")
they consistently have failed to implement and enforce the most basic
security practices. Here are 7 simple security practices that you cannot
afford to not follow.

### 1. Secure pass phrases

Throw away the notion of
a [password](http://en.wikipedia.org/wiki/Password "Password"). Pass
phrases consisting of multiple words and symbols are considerably more
secure and easy to remember. Most people use the same password for
everything and it’s almost always a word or a word+\#. A good [pass
phrase](http://en.wikipedia.org/wiki/Passphrase "Passphrase") can be
something like “Mary.had.@.little.Lamb”. It’s really easy to remember
and nearly impossible to guess or brute force. Using a password
management system like One Password for Mac is also a good idea.

### 2. Educate your users

All too often policies are put into place but lacking training necessary
to ensure that policies are understood and followed. Quarterly web casts
can go a long way to ensuring that the most critical policies are
complied with without adding unnecessary disruptions to the business.

### 3. Perform [regulatory compliance](http://en.wikipedia.org/wiki/Regulatory_compliance "Regulatory compliance") self audits

Hackers are attempting to break into your systems right now. If you
aren’t holding self audits than the only ones auditing your systems are
the hackers. It’s critical that this practice takes place routinely to
ensure that your data and systems are as safe as possible. It only takes
one small mistake to make you vulnerable. Routine system checking means
there is a chance you will find it before someone else does.

### 4. Access provided on a needs to have basis

Yes this is inconvenient. Yes you need to do it. Firewalls, ACL, fine
grained permissions. Properly setup roles. In every system you do use,
in every level. This also means that root/admin permission should always
be behind sudo and never logged in.

### 5. Encrypt all sensitive data

All sensitive data should be encrypted. Hard drives should be encrypted;
Tunnels should be encrypted using
SSH, [VPN](http://en.wikipedia.org/wiki/Virtual_private_network "Virtual private network")
or SSL; Wireless networks and even wireless keyboards. Passwords should
be stored via a one
way [encryption](http://en.wikipedia.org/wiki/Encryption "Encryption")
like md5.

### 6. Never take data off site (flash drives, laptops, etc)

It seems every time you hear about a bank or government agency losing
millions of critical identity information a portable drive or laptop is
involved. While encryption is part of the solution here, it could
entirely be avoided if sensitive data is not permitted off site. Data
should reside on servers sitting behind properly established ACL and not
be available to be copied or transferred onto a laptop or portable
drive.

### 7. Use common sense

Lastly, the most important security principle is to use common sense. If
it seems wrong, it probably is. Common sense is your best defense. Use
it wisely.

## Related articles

-   [Data Security in Simple
    Terms](http://abusiveviews.wordpress.com/2009/11/01/data-security-in-simple-terms/)
    (abusiveviews.wordpress.com)
-   [Protect Your Important and Personal
    Data](http://techie-buzz.com/tips-and-tricks/protect-your-important-and-personal-data.html?utm_source=subscriber&utm_medium=rss&utm_campaign=rss)
    (techie-buzz.com)
-   [Secure your data with encrypted USB
    drives](http://www.crunchgear.com/2009/10/08/secure-your-data-with-encrypted-usb-drives/)
    (crunchgear.com)
-   [Lawyers should leave their laptops at home when traveling
    abroad](http://www.socialmediatoday.com/SMC/122938)(socialmediatoday.com)
-   [Protect your data](http://owencutajar.com/protect-your-data/)
    (owencutajar.com)

