---
Description: a completely cross platform distribution of vim plugins and resources
  for Vim, GVim and MacVim stays true to it's vim roots while adding modern features
  including a plugin management system, a curated plugin set with customized configuration,
  advanced autocomplete, tags, support for dozens of languages and much more.
Keywords:
- Development
- VIM
- .vimrc
- Distribution
- Gvim
- plugins
- spf13-vim
- Vi
- vim
- Vim (text editor)
- Vimscript
Tags:
- .vimrc
- Distribution
- Gvim
- plugins
- spf13-vim
- Vi
- vim
- Vim (text editor)
- Vimscript
Title: Why I use spf13-vim
Topics:
- Development
- VIM
date: 2014-01-17
---

[spf13-vim](http://vim.spf13.com), a completely cross platform
distribution of vim plugins and resources for Vim, GVim and MacVim stays
true to it's vim roots while adding modern features including a plugin
management system, a curated plugin set with customized configuration,
advanced autocomplete, tags, support for dozens of languages and much
more.

I recently read a thread where the author asked for feedback on whether
or not to use spf13-vim. Responses varied greatly with some people
loving it to others claiming it was bloated and overkill. Some suggested
everyone should create their own configuration from scratch. Not
surprisingly many of these criticisms were accompanied by links to
people's own vim configurations. With so many options out there, why
would anyone use spf13-vim. While I can't speak for anyone else, here
are four reasons why I use spf13-vim.

First, a bit of history... spf13-vim started as my personal vim
configuration. As long as I can remember I've obsessed with user
experience and spent an embarrassingly large amount of time customizing
each and every single action. As many others have, I put my
configuration on github, not with the intent to share it with others,
but to have a safe place to keep it for when I setup new computers.

## 1. Vanilla Vim like

In designing spf13-vim I took extreme caution with every decision I made
and made certain to not override any essential Vim functionality . I had
invested years in becoming proficient in vanilla Vim and didn't want to
throw any of those muscle memories away. I also wanted to remain
completely comfortable in vanilla Vim.  At the same time I wanted to
smooth over some of the rougher parts and provide additive features.
Virtually every one of the vanilla keystrokes and actions remain untouched.

A handful of default keystrokes have been remapped. A few of what I
consider some of the less useful behaviors have been adjusted to be more
consistent with the overall vim experience. For example, the first thing
people learn in Vim is how uses 'hjkl' for cursor movement, spf13-vim
adds ctrl+hjkl to move around windows and 'HL' (shift+hl) to move
between tabs. Since these are common actions, it felt decidedly
unvim-like to hide them behind commands or multiple keystrokes. These
tab movements override Vim's default behavior of moving to the top 'H'
and bottom 'L' of the window. Something I don't ever use.

## 2. Customizability

Continuing with the history, over time people found it and began to use
it for themselves. Recognizing this I adding more flexibility to
spf13-vim which provided the ability for people to use spf13-vim as a
foundation, but add their own customizations to configure it precisely
to fit their own needs.

Perhaps you work differently than I do and use the default 'H' &
'L' functionality. spf13-vim wraps each one of the overrides
with an conditional statement enabling users to easily customize it
exactly to their needs. Most users find spf13-vim default requires
little customization but are happy to discover how easy it is to craft
their personalized vim experience.


## 3. Power of the masses

The strength and heart of open source comes from people recognizing
together we can make something better than any of us could alone. As
more and more people began to use spf13-vim, many of them desired to
contribute back. While spf13-vim started as my personal project, it has
grown from mine to ours. I use vim to write in a few languages, and
invested time discovering and customizing the best plugins for those
languages, collectively the users of spf13-vim support far more
languages than any one person would be able to. I love when I edit a
file in a language I haven't used before and someone else has already
crafted a customized experience in spf13-vim.

spf13-vim benefits greatly from contributions from it's completely
diverse user base. This ensures regardless of your development stack or
purpose, spf13-vim likely meets your needs. With support for many
different languages, plugins and uses, vim could become weighted down.
spf13-vim makes it trivial to include only the features you would use by
defining a simple list.

One of the primary reasons I hear for people abandoning Vim is properly
configuring vim is too difficult and plugins tend to be incompatible
with each other. With many active and engaged users working together
issues and incompatibilities are discovered and fixed by the users
together quickly.

The vim plugin community is always evolving. New plugins come out daily.
With many different users exploring and experimenting with new plugins
this results in vim configuration using the latest and greatest. Without
investing countless hours exploring, each user benefits greatly from the
combined efforts of everyone. spf13-vim receives many pull requests each
week keeping our collective vim experience fresh.

## 4. The community

The primary reason I love using spf13-vim is the great community. This
goes beyond the power of the masses, the spf13-vim users are some of the
most patient and kind people I've ever encountered. The [spf13-vim
mailing list](https://groups.google.com/forum/#!forum/spf13-vim-discuss)
is full of people, sometimes naive, asking for help. I am consistently
impressed with the willingness of spf13-vim users to help. 

I remember back to when I first learned Vim. It was overwhelming at
times and frustrating. After 8 years using Vim full time I still feel
this way from time to time. Anyone who has tried to use Vim can likely
relate. How wonderful it is to have a group of helpful users available
and willing to assist.

When I [speak](http://spf13.com/presentation) at conferences I'm most
often recognized for vim configurations. People come up and tell me how
happy they are to "use me". How lucky I am to be part of this great
project that bears my name. A big thanks to the talented users (and
contributors) of the greatest vim experience.

That's why I use [spf13-vim](http://vim.spf13.com). Why do you?
