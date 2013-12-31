{
	"disqus_url" : "http://spf13.com/post/the-15-best-vim-plugins/",
	"disqus_identifier" : "137 http://localhost/~sfrancia/wordpress/?p=137",
	"disqus_title" : "The 15 Best Vim Plugins",
	"Title": "The 15 Best Vim Plugins",
	"Description": "The 15 most useful plugins for VIM. This post is a bit dated but kept intact to reflect the best plugins at the time",
	"Keywords": [
		"plugins",
		"vim",
		"Vim (text editor)"
	],
	"Tags": [
		"plugins",
		"vim",
		"Vim (text editor)"
	],
	"Pubdate": "2008-07-30",
	"Topics": [
		"VIM"
	],
	"Url": "post/the-15-best-vim-plugins",
	"Slug": "the-15-best-vim-plugins",
	"Section": "post",
	"Thumbnail": "/media/vim_logo.png"
}
{{% img src="/media/vim_logo.png" class="third right" alt="vim" %}}

One of the things that makes vim great is that it can be extended
through plugins. There are plugins for more than you would expect. I
have gathered together the 15 best plugins. I’ve included these plugins
as part of my [ultimate VIM
configuration](http://spf13.com/post/ultimate-vim-config) which has been
featured on many sites and is hosted on
[github](https://github.com/spf13/spf13-vim).  I’ve also begun a series
of posts on some of these plugins including
[snipmate](http://spf13.com/post/vim-plugins-snipmate) and
[NerdCommenter](http://spf13.com/post/vim-plugins-nerd-commenter).

General
-------

### Related Posts

-   [Vim Plugins: NERD
    Commenter](http://spf13.com/post/vim-plugins-nerd-commenter/)
-   [spf13-vim 3.0 release and new
    website](http://spf13.com/post/spf13-vim-3-0-release-and-new-website/)
-   [The perfect .vimrc vim config
    file](http://spf13.com/post/perfect-vimrc-vim-config-file/)
-   [VIM Crash Course](http://spf13.com/post/vim-crash-course/)
-   [Vim Plugins: snipMate](http://spf13.com/post/vim-plugins-snipmate/)
-   [Ultimate Vim Config](http://spf13.com/post/ultimate-vim-config/)

### [SuperTab](http://www.vim.org/scripts/script.php?script_id=1643)

Do all your insert-mode completion with Tab.

### [ShowMarks](http://www.vim.org/scripts/script.php?script_id=152)

Visually shows the location of marks.<br>
 Marks are useful for jumping back and forth between interesting points
in a buffer, but can be hard to keep track of without any way to see
where you have placed them.  ShowMarks hopefully makes life easier by
placing a sign in the leftmost column of the buffer.  The sign indicates
the label of the mark and its location.<br>
 It can be toggled on and off and individual marks can be
hidden(effectively removing them).

### [SearchComplete](http://www.vim.org/scripts/script.php?script_id=474)

Provides tab completion while inside the “/” search

Programmer
----------

### [Tag List](http://vim-taglist.sourceforge.net/)

taglist.vim : Source code browser (supports C/C++, java, perl, python,
tcl, sql, php, etc).<br>
 *Requires the [exuberant
ctags](http://en.wikipedia.org/wiki/Ctags "Ctags") utility.*

### [SQLComplete](http://www.vim.org/scripts/script.php?script_id=1572)

Completion for the SQL language includes statements, functions,
keywords, operators and database options which it draws from the current
SQL syntax file in use.  Vim ships with 9 different SQL syntax files
(Oracle, Informix, MySQL, SQL Anywhere, …).  You can choose different
SQL dialects using the command  (see :h sql-dialects):

### [The NERD Commenter](http://www.vim.org/scripts/script.php?script_id=1218)

A plugin that allows for easy commenting of code for many (nearly all)
filetypes.

### [VCSCommand](http://www.vim.org/scripts/script.php?script_id=90)

VIM 7 plugin useful for manipulating files controlled by CVS, SVN, SVK
and git within VIM, including committing changes and performing diffs
using the vimdiff system.

### [Surround](http://www.vim.org/scripts/script.php?script_id=1697)

All about “surroundings”: parentheses, brackets,
quotes, [XML](http://en.wikipedia.org/wiki/XML "XML") tags, and more.
The plugin provides mappings to easily delete, change and add such
surroundings in pairs.

### [MatchIT](http://www.vim.org/scripts/script.php?script_id=39)

The matchit.vim script allows you to configure % to match more than just
single characters. You can match words and even [regular
expressions](http://en.wikipedia.org/wiki/Regular_expression "Regular expression").
Also, matching treats strings and comments (as recognized by the [syntax
highlighting](http://en.wikipedia.org/wiki/Syntax_highlighting "Syntax highlighting")
mechanism) intelligently.

### [snippetsEMU](http://www.vim.org/scripts/script.php?script_id=1318)

Attempts to emulate some of the behaviour of ‘Snippets’ from the OS X
editor [TextMate](http://www.macromates.com/ "TextMate"), in particular
the variable bouncing and replacement behaviour.

[PHP](http://php.net/ "PHP")
----------------------------

### [Smarty Syntax File](http://www.vim.org/scripts/script.php?script_id=1798)

Syntax file for [Smarty](http://smarty.php.net), the template engine for
PHP.

### [PHP Syntax File](http://www.vim.org/scripts/script.php?script_id=1571)

Syntax file for  PHP.

### [PHP Folding](http://www.vim.org/scripts/script.php?script_id=1623)

This script can fold PHP functions and/or classes, properties with
their [PhpDoc](http://en.wikipedia.org/wiki/PHPDoc "PHPDoc"),<br>
 without manually adding marker style folds ({{{ and }}}).

### [CheckSyntax](http://www.vim.org/scripts/script.php?script_id=1431)

Check syntax when saving a file (PHP). Also supports ruby, tex, etc.

### [PDV- phpDocumentor for Vim](http://www.vim.org/scripts/script.php?script_id=1355)

Provides really comfortable generation of phpDocumentor doc blocks for
PHP

### External Resources

-   [A collection of .vimrc files](http://dotfiles.org/.vimrc)
-   [Text editing with
    Vim](http://newbiedoc.sourceforge.net/text_editing/vim.html.en)
-   [Vim for
    Programmers](http://www.scribd.com/doc/263139/VIM-for-PHP-Programmers)
-   [Getting Started with VIM and
    PHP](http://realm3.com/articles/getting_started_with_vim_and_php)
-   [Comfortable PHP editing with
    VIM](http://schlitt.info/applications/blog/index.php?/archives/283-Comfortable-PHP-editing-with-VIM-5.html)
-   [Technical Analysis: VIM, PowerShell and Signed
    Code](http://port25.technet.com/archive/2008/05/29/technical-analysis-vim-powershell-and-signed-code.aspx)
-   [Author of VIM](http://www.moolenaar.net/vim.html)
-   [Graphical vi-vim Cheat Sheet and
    Tutorial](http://www.viemu.com/a_vi_vim_graphical_cheat_sheet_tutorial.html)
-   [Great plain english tutorial for
    vim](http://www.vi-improved.org/tutorial.php)

