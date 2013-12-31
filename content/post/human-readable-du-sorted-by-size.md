{
	"disqus_url" : "http://spf13.com/post/human-readable-du-sorted-by-size/",
	"disqus_identifier" : "82 http://localhost/~sfrancia/wordpress/?p=82",
	"disqus_title" : "Human readable du sorted by size",
	"Title": "Human readable du sorted by size",
	"Description": "",
	"Keywords": [
		"Development",
		"Systems",
		"bash",
		"du",
		"Linux",
		"profile"
	],
	"Tags": [
		"bash",
		"du",
		"Linux",
		"profile"
	],
	"Pubdate": "2010-01-23",
	"Topics": [
		"Development",
		"Systems"
	],
	"Url": "post/human-readable-du-sorted-by-size",
	"Slug": "human-readable-du-sorted-by-size",
	"Section": "post",
	"Thumbnail": "/uploads/2010/01/300px-Du_unix_output.png"
}

{{% img src="/media/du.png" class="right third" alt="example output of du UNIX command" %}}

du is the \*nix command for [disk
usage](http://en.wikipedia.org/wiki/Du_%28Unix%29 "Du (Unix)"). It tells
you how much space everything in the given directory is taking
up. [GNU](http://www.gnu.org/ "GNU") du introduced a handy option -h
making it human readable, or showing sizes using K, M, G rather than
bytes. Unfortunately this makes it not sortable numerically. Here’s how
to sort du by size and keep it as human readable.

Insert the following function into your .profile or .bash\_profile file.


     function duf {
         du -k "$@" | sort -n | while read size fname; do for unit in k M G T P E Z Y; do if [ $size -lt 1024 ]; then echo -e "${size}${unit}t${fname}"; break; fi; size=$((size/1024)); done; done
     }

By writing this as a function, it enables you to pass along parameters
to the newly created **duf** command just as you would **du**.

For convenience, I also create the following aliases which you can also
place in your .profile or .bash\_profile file.


    alias du1='duf --max-depth=1'
    alias du2='duf --max-depth=2'
    alias du0='duf --max-depth=0'

Once you have added these lines, remember to 

source .profile

to use it without logging out.
