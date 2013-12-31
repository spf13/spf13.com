{
	"disqus_url" : "http://spf13.com/post/vim-plugins-snipmate/",
	"disqus_identifier" : "119 http://localhost/~sfrancia/wordpress/?p=119",
	"disqus_title" : "Vim Plugins: snipMate",
	"Title": "Vim Plugins: snipMate",
	"Description": "",
	"Keywords": [
		"plugins",
		"snipmate",
		"Vi",
		"vim",
		"Vim (text editor)"
	],
	"Tags": [
		"plugins",
		"snipmate",
		"Vi",
		"vim",
		"Vim (text editor)"
	],
	"Pubdate": "2009-12-12",
	"Topics": [
		"VIM"
	],
	"Url": "post/vim-plugins-snipmate",
	"Slug": "vim-plugins-snipmate",
	"Section": "post",
	"Thumbnail": "/images/1013_Vim_gloss_128.png-200x200.png"
}

{{% img src="/media/vim_logo.png" class="third right" %}}

Why use it
----------

-   It’s super easy to use
-   It has tons of snippets
-   It’s pretty well compatible with TextMate snippets for easy
    portability
-   Dynamic variables, for all the times you use the same string
    multiple times
-   It’s really easy to define your own snippets
-   It’s better than anything else out there, trust me I’ve tried them
    all

Sometimes a video works better to explain things.. check out this video
{{% vimeo 3535418 %}}

[snipMate.vim Introductory Screencast](http://vimeo.com/3535418) from
[Michael Sanders](http://vimeo.com/user1404868) on
[Vimeo](http://vimeo.com).

Installing
----------

-   There are a couple of ways to obtain it either download the zip from
    the vim site:
    [snipMate](http://www.vim.org/scripts/script.php?script_id=2540) or
    grab it from the authors [git
    repo](git://github.com/msanders/snipmate.vim.git).
-   Extract the zip file or tarball to ~/.vim (on Unix/Linux) or
    ~vimfiles (on Windows).
-   As good measure, from inside vim, run :helptags ~/.vim/doc (on
    Unix/Linux) or :helptags ~/vimfiles/doc (on Windows) to rebuild the
    tags file
-   Restart Vim

Using snipMate
--------------

snippet is a piece of often-typed text that you can insert into document
using a trigger word followed by a \<tab\>. For instance, in a C file
using the default installation of snipMate.vim, if you type “for\<tab\>”
in insert mode, it will expand a typical for loop in C:

 for (i = 0; i &lt; count; i++) {     }

To go to the next item in the loop, simply over to it; if there is
repeated code, such as the “i” variable in this example, you can simply
start typing once it’s highlighted and all the matches specified in the
snippet will be updated. To go in reverse, use \<shift-tab\>.

Beyond Installation
-------------------

### Grabbing Scrooloose’s snippets repository from github

Martin Grenfell (Scrooloose) maintains a nice repository of snippets.
Though it is a bit ruby heavy, it has dozens of languages including a
nice jquery section, and frankly quite a bit more than the stock
snippets. I recommend installing his snippets and either fork it or
customize it with your own. Here’s how to install the repo (\*nix
instructions)

    cd ~/.vim
    mv snippets snippets.orig
    git clone git://github.com/scrooloose/snipmate-snippets.git snippets

[Git](http://git-scm.com/ "Git") will take care of the
installation for you. If you don’t have git, I really recommend it, and
I have a guide on how to install it locally. One thing you’ll notice
about this repository is that it’s much more structured that the stock
snippets. Rather than each language containing a snippet file, each
language contains a directory full of snippets with each snippet is in
it’s own file. For situations where you want multiple snippets under the
same keyword, create a subdirectory and place the snippets inside it. It
works quite well, though it seems either approach would be sufficient
for personal use.

### Creating your own snippets

While there are a bunch of stock snippets, it didn’t take me very long
to realize it didn’t have everything I wanted. Fortunately it’s super
easy to create your own snippets.

The following is largely lifted from the help file. I strongly recommend
reading it (:help snipMate).

Snippets are by default looked for any ‘snippets’ directory in your
‘runtimepath’. Typically, it is located at ‘~/.vim/snippets/’ on \*nix
or ‘$HOMEvimfilessnippets’ on Windows. (*To change that location or add
another one, change the g:snippets\_dir variable in your |.vimrc| to
your preferred directory.*)

Snippets can be defined in two ways. They can be in their own file,
named after their trigger in ‘snippets/[filetype]/[trigger].snippet’, or
they can be defined together in a ‘snippets/[filetype].snippets’ file.

#### Syntax

The syntax for snippets in \*.snippets files is the following:

 snippet trigger         expanded text         more expanded text

Note that the first hard tab after the snippet trigger is required, and
not expanded in the actual snippet. The syntax for \*.snippet files is
the same, only without the trigger declaration and starting indentation.

#### tabstops

By default, the cursor is placed at the end of a snippet. To specify
where the cursor is to be placed next, use “${\#}”, where the \# is the
number of the tab stop. E.g., to place the cursor first on the id of a
\<div\> tag, and then allow the user to press \<tab\> to go to the
middle of it:

 snippet div

${2}

#### placeholders

Placeholder text can be supplied using “${\#:text}”, where \# is the
number of the tab stop. This text then can be copied throughout the
snippet using “$\#”, given \# is the same number as used before. So, to
make a C for loop:

 snippet for         for (${2:i}; $2 &lt; ${1:count}; $1++) {      
          ${4}         }

This will cause “count” to first be selected and change if the user
starts typing. When \<tab\> is pressed, the “i” in ${2}’s position will
be selected; all $2 variables will default to “i” and automatically be
updated if the user starts typing. *NOTE: “$\#” syntax is used only for
variables, not for tab stops as in TextMate.*


Variables within variables are also possible. For instance:

 snippet opt       ${2:$1}

Will, as usual, cause “option” to first be selected and update all the
$1 variables if the user starts typing. Since one of these variables is
inside of ${2}, this text will then be used as a placeholder for the
next tab stop, allowing the user to change it if he wishes.

To copy a value throughout a snippet without supplying default text,
simply use the “${\#:}” construct without the text; e.g.:

 snippet foo         ${1:}bar$1

## Related articles

-   [Vim Plugins: NERD
    Commenter](http://spf13.com/feature/vim-plugins-nerd-commenter)
    (spf13.com)
-   [Use TextMate like Snippets in
    Vim](http://www.zalas.eu/how-to-use-textmate-like-snippets-in-vim)
    (zalas.eu)
-   [Inserting
    Snippets](http://vim.runpaint.org/typing/inserting-snippets/)
    (runpaint.org)
-   [Snippets in Vim with
    snipMate](http://dancingpenguinsoflight.com/2009/07/light-at-the-end-of-the-carpal-tunnel-snippets-in-vim-with-snipmate/")
    (dancingpenguinsoflight.com)

