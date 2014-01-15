{
	"Title": "PIV : PHP Integration for VIM",
	"Description": "",
	"Keywords": [
		"Development",
		"PHP",
		"vim",
		"editor"
	],
	"Tags": [
		"Development",
		"PHP",
		"vim",
		"editor"
	],
	"Pubdate": "2012-02-13",
	"Topics": [
		"Development",
		"Vim"
	],
	"Slug": "piv",
    "project_url": "http://github.com/spf13/piv"
    "project_name": "PIV"
    "project_description": "Php integration for VIM"
    "official_url": "http://spf13.com/project/piv"
    "download_url": "http://github.com/spf13/piv"
    "release_date": "2013-10-18"
}

This project contains the most feature complete and up to date PHP
Integration for Vim. It began as a fork of the largely outdated VIP
(formerly PDV), but has morphed into it’s own project.

It is intended to include the best PHP specific plugins, configurations
and resources for editing PHP. Special care has been taken to include
the best, keep them up to date and make sure everything plays well
together.

**It doesn’t attempt to include the best *programming* plugins, so you
can use the plugins you prefer.**

The bottom of this readme includes a list of many great plugins that
work well with PIV. If you are looking for an excellent VIM
configuration/distribution, please checkout [spf13-vim : A better Vim
Distribution](http://spf13.com/project/spf13-vim "spf13-vim : A better Vim Distribution").

Features
--------

### Updated Syntax

*Updated for PHP 5.3*

The list of PHP constants, functions, and classes was updated to be
current with PHP 5.3. Many new classes were added in the 5.2 and 5.3
branches and the distributed version only covers up to 5.1.4.

### Better Fold Support

This plugin can fold PHP functions and/or classes, properties with their
PhpDoc, without manually adding marker style folds ({{{ and }}})
[[http://www.vim.org/scripts/script.php?script\_id=1623]]

Can be turned off by setting


    let g:DisableAutoPHPFolding = 1

in your .vimrc file.

### PHP Doc Gen

Generate phpDocumentor conforming documentation blocks for your PHP
code.

To use place cursor on line with class, function or variable definition
and type ,pd (in n mode)

### Better Completion

PHP completion script for use with omniComplete. Using Shawn Biddle’s
excellent [phpcomplete.vim
script](http://www.vim.org/scripts/script.php?script_id=3171)

Completion from current file, included files, tags and php builtin:


    * classes (after new),
    * functions
    * variables
    * constants
    * language keywords

Either use or
install [SuperTab](http://www.vim.org/scripts/script.php?script_id=1643)
to use. By default will show a preview of the function call.

Completion is done via context, for example after -\> and :: options
limited to funcs and vars.

#### Examples

Example class which has a TAGS file generated for it somewhere


    class SomeClass {
      private function _private_method() {} // never shows up in completion list
      public static function staticMethod() {} // only shows up when using completion on SomeClass::
      public function completeMe() {} // only shows up when using completion on $instance_of_someclass-&gt;
    }

#### Non-static completion


    $instance = new SomeClass;
    ...
    $instance-> to display the omnicompletion menu (see :help ins-completion)
    $instance->completeMe(); // will autoselect completeMe since it's the only public non-static method

#### Static completion


    SomeClass:: to display omnicompletion menu
    SomeClass::staticMethod(); // once again will autoselect staticMethod since it's the only public static method

#### Singleton completion


    $instance = SomeClass::getInstance();
    $instance-> complete just like non-static

#### Other features

-   Correct restriction of static or standard methods based on context (
    show only static methods with :: and only standard with -\>)
-   Real support for self:: and $this-\> with the aforementioned
    context restriction
-   Constant variable completion (not just define(VARIABLE, 1) but const
    VARIABLE = 1)

### Better indenting w/automatic formatting

Custom php indenting file for VIM

### Full (and current [5.3]) PHP Manual

Simply hit K (shift+k) on any function to see full documentation file
for that function even offline.

Recommendations
---------------

It isn’t my intention to provide php specific functionality when a good
general purpose solution exists.

The following plugins are recommended and can be found in my [spf13-vim
: A better Vim
Distribution](../project/spf13-vim "spf13-vim : A better Vim Distribution").

-   [Snipmate](http://github.com/msanders/snipmate.vim)
-   [NerdCommenter](http://github.com/scrooloose/nerdcommenter.git)
-   [NerdTree](http://github.com/scrooloose/nerdtree)
-   [SuperTab](http://www.vim.org/scripts/script.php?script_id=1643)
-   [Fugitive](http://github.com/tpope/vim-fugitive.git)
-   [DelimitMate](http://github.com/Raimondi/delimitMate)
-   [Matchit](http://www.vim.org/scripts/script.php?script_id=39)
-   [CheckSyntax](http://www.vim.org/scripts/script.php?script_id=1431)
-   [Surrounding](http://github.com/msanders/vim-files/blob/master/plugin/surrounding.vim)
-   [AutoCloseTag](http://www.vim.org/scripts/script.php?script_id=2591)
