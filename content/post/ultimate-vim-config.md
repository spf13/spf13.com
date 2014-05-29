---
Description: ""
Keywords:
- Development
- php
- VIM
- Editors
- Open source
- PHP
- Text editor
- Vim (text editor)
Section: post
Slug: ultimate-vim-config
Tags:
- Editors
- Open source
- PHP
- Text editor
- Vim (text editor)
Thumbnail: /images/765_Vim_gloss_128.png-200x200.png
Title: Ultimate Vim Config
Topics:
- Development
- php
- VIM
Url: post/ultimate-vim-config
date: 2010-06-25
disqus_identifier: 10 http://localhost/~sfrancia/wordpress/?p=10
disqus_title: Ultimate Vim Config
disqus_url: http://spf13.com/post/ultimate-vim-config/
---

{{% img src="/media/vim_logo.png" class="third right" alt="vim" %}}

I have spent the last few years tweaking and refining my VIM
configuration until I had the Ultimate Vim Config.  It is well organized
and documented taking full advantage of Tpope’s
[pathogen](http://www.vim.org/scripts/script.php?script_id=2332) for a
excellent clean and modular configuration. The Ultimate vim config
contains the perfect .vimrc file combined with an excellent set of
plugins all easily managed thanks to pathogen and git. It is on
[GitHub](http://github.com/spf13/spf13-vim) so you can always grab the
latest.

The Ultimate VIM Configuration
------------------------------

This is the ultimate vim configuration.

Modular configuration using power of pathogen & git
---------------------------------------------------

Far more than just a well crafted .vimrc file (though it’s got one of
those too), it  makes use of
[pathogen](http://www.vim.org/scripts/script.php?script_id=2332) to have
a well organized vim directory. It heavily uses git submodules where
possible for all plugins so each plugin can easily and independently be
kept up to date.

Fully cross platform
--------------------

It also works well on Windows, Linux and OSX without even modifying
directories. Just git clone and run.

The perfect .vimrc file
-----------------------

The vimrc file is perfectly suited programming and also works well for
general use. It is very well organized and folds in sections. Each
section is labeled and each option is commented.

It fixes many of the inconveniences of vanilla vim including:

-   One config can be used across Windows, Mac and linux
-   Eliminates swap and backup files from littering directories,
    preferring to store in a central (hidden) location.
-   Fixes common command typos like :W, :Q, etc
-   Setup a solid set of settings for formatting (change to meet your
    needs)
-   Setup the interface to take advantage of vim’s features including
    -   omnicomplete
    -   line numbers
    -   syntax highlighting
    -   a better ruler & status line
    -   tons more

-   Configuring included plugins

Includes the best Plugins
-------------------------

I compile and configure a few popular vim plugins, colors, snippets, etc

Most of the bundles are git submodules facilitating easy updating and
configuration.

-   [PIV (PHP Integration for VIM)](http://github.com/spf13/PIV)
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

It also contains a very complete set of
[snippets](https://github.com/spf13/snipmate-snippets) for use with
snipmate.

Easy Installation
-----------------

     git clone git://github.com/spf13/spf13-vim.git

     cd spf13-vim

     git submodule update --init

I setup symlinks after this so I can maintain the repo outside of my
actual config location.

Use ln -s on mac/unix or mklink on windows.

     cd ~

     ln -s /path/to/spf13-vim/vimrc .vimrc

     ln -s /path/to/spf13-vim/vim .vim


Find it on [GitHub](http://github.com/spf13/spf13-vim)

## Related Posts

-   [Vim Plugins: snipMate](http://spf13.com/post/vim-plugins-snipmate/)
-   [The 15 Best Vim
    Plugins](http://spf13.com/post/the-15-best-vim-plugins/)
-   [spf13-vim 3.0 release and new
    website](http://spf13.com/post/spf13-vim-3-0-release-and-new-website/)
-   [VIM Crash Course](http://spf13.com/post/vim-crash-course/)
-   [Vim Plugins: NERD
    Commenter](http://spf13.com/post/vim-plugins-nerd-commenter/)
-   [The perfect .vimrc vim config
    file](http://spf13.com/post/perfect-vimrc-vim-config-file/)

