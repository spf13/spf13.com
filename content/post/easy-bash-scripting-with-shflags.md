{
	"disqus_url" : "http://spf13.com/post/easy-bash-scripting-with-shflags/",
	"disqus_identifier" : "1480 http://spf13.com/?p=1480",
	"disqus_title" : "Easy bash scripting with shflags",
	"Title": "Easy bash scripting with shflags",
	"Description": "",
	"Keywords": [
		"Development",
		"Systems",
		"bash",
		"Shell",
		"Shell script"
	],
	"Tags": [
		"bash",
		"Shell",
		"Shell script"
	],
	"Pubdate": "2011-07-08",
	"Topics": [
		"Development",
		"Systems"
	],
	"Url": "post/easy-bash-scripting-with-shflags",
	"Slug": "easy-bash-scripting-with-shflags",
	"Section": "post",
	"Thumbnail": "http://upload.wikimedia.org/wikipedia/commons/thumb/a/aa/Command_line.png/300px-Command_line.png"
}

One of the most frustrating things about bash scripts is how challenging
it is to create unix style executables. You know, the ones where you can
pass in -h or –help and see the set of options for the program. Up until
now this has been a very manual process in bash, but no longer. Enter
the shflags project from Kate Ward where a bash library takes care of
all the nasty work and producing an elegant way to add option (or
argument) support to your scripts.

shflags is a powerful (and simple) tool for handling command line args
in bash. It works on both Gnu and Bsd systems without any tricky
handling which makes it a unique solution.

Usage
=====

Shflags syntax is easy to understand an use. It comprises three
sections, including shflags, a definition section and an initialization
section.
 As in everything with bash, this needs to be written in order, as bash
executes top down.

Including shflags
-----------------


        # source shflags
        . ./shflags 
          or
        source /path/to/shflags

The first line is a shortcut to sourcing a file in the same directory
which makes this quite portable.<br>
 If the shflags library exists in another place on the drive, but it
needs to be specified and isn’t all that portable.

Defining options
----------------

shFlags supports boolean, float, integer and string. Since shell doesn’t
natively support float, they are technically strings handled like floats
and as such regular string comparison operators ( =, != ) should be
used.

Here’s the syntax:


        DEFINE_type   'longoption' 'default value' 'description' 'one letter option'

        DEFINE_string 'name' 'world' 'name to say hello to' 'n'
        DEFINE_boolean 'force' false 'force overwriting' 'f'
        DEFINE_integer 'limit' 10 'number of items retuned' 'l'
        DEFINE_float 'time' '10.5' 'number of seconds to run' 't'

Initialization
--------------

This section is the exact same every time. Just copy the boilerplate and
enjoy.


        # parse the command-line
        FLAGS "$@" || exit 1
        eval set -- "${FLAGS_ARGV}"

Putting it all together
=======================


        #!/bin/sh

        # source shflags
        . ./shflags

        # define a 'name' command-line string flag
        DEFINE_string 'name' 'world' 'name to say hello to' 'n'

        # parse the command-line
        FLAGS "$@" || exit 1
        eval set -- "${FLAGS_ARGV}"

        # say Hello!
        echo "Hello, ${FLAGS_name}!"

Download & Resources
====================

Checkout the excellent
[Documentation](http://code.google.com/p/shflags/wiki/Documentation10x)

[Download Here](http://code.google.com/p/shflags/downloads/list)

## Related articles

-   [Bash shell-scripting libraries ” Striving for
    greatness](http://dberkholz.com/2011/04/07/bash-shell-scripting-libraries/)
    (dberkholz.com)

