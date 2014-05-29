---
Description: Tips, Techniques and Tricks for using GNU Screen to increase your productivity.
Keywords:
- cli
- gnu
- screen
- terminal
Section: post
Slug: be-more-productive-using-gnu-screen
Tags:
- cli
- gnu
- screen
- terminal
Thumbnail: /media/300px-GNU_Screen.png
Title: Be more productive using GNU Screen
Topics:
- Systems
Url: post/be-more-productive-using-gnu-screen
date: 2008-07-03
disqus_identifier: 216 http://localhost/~sfrancia/wordpress/?p=216
disqus_title: Be more productive using GNU Screen
disqus_url: http://spf13.com/post/be-more-productive-using-gnu-screen/
---

{{% img src="/media/300px-GNU_Screen.png" caption="Image via Wikipedia" title="GNU Screen" class="half right" %}}

Despite living in the age of multicore
processors, [GUI](http://en.wikipedia.org/wiki/Graphical_user_interface "Graphical user interface")
everything and mountains of ram, I continually find myself more
productive with a terminal open. Especially when that terminal is
running [GNU Screen](http://www.gnu.org/software/screen "GNU Screen").

About [GNU Screen](http://www.gnu.org/software/screen "GNU Screen")
===================================================================

[GNU Screen](http://en.wikipedia.org/wiki/GNU_Screen "GNU Screen") is a
free terminal multiplexer developed by [the GNU
Project](http://en.wikipedia.org/wiki/GNU_Project "GNU Project"). It
allows a user to access multiple separate terminal sessions inside a
single [terminal
window](http://en.wikipedia.org/wiki/Terminal_emulator "Terminal emulator")
or remote terminal session. It is useful for dealing with multiple
programs from the [command
line](http://en.wikipedia.org/wiki/Command_line_interface "Command line interface"),
and for separating programs from the shell that started the program.<br>
 -courtesy of wikipedia

My .screenrc file
=================

~~~~ {.brush: .bash}
vbell off
escape ~~
autodetach on
altscreen on
defflow auto
defscrollback 5000
screen -t bash 1
#change the hardstatus settings to give an window list at the bottom of the
#screen, with the time and date and with the current window highlighted
hardstatus alwayslastline
hardstatus string '%{= kG}[ %{G}%H %{g}][%= %{= kw}%?%-Lw%?%{r}(%{W}%n*%f%t%?(%u)%?%{r})%{w}%?%+Lw%?%?%= %{g}][%{B} %d/%m %{W}%c %{g}]'
~~~~

Using GNU Screen
================

Launching screen creates a new window and launches a [command
shell](http://en.wikipedia.org/wiki/Shell_%28computing%29 "Shell (computing)")
in that window. In screen every window is identified by a unique number.
When screen made a new window, it numbered it 0. This all happens
somewhat invisibly, at least without knowing the right commands to type.

My .screenrc file makes screen more visible and usable. It effectively
does 3 things.

1.  Adding a visual taskbar at the bottom of the console
2.  Remap Ctrl-a to the backtick character (to the left of the ’1′
    key).. you’ll see why in a bit
3.  Launch a few programs in their own windows (please customize)

Shortcuts
---------

*Keys to be typed in succession, not simultaneously*

-   **\` c**: Create Window
-   **\` A**: Rename Window
-   **\` 0 – 9** : Switch to Window with that number
-   **\` backspace** : Previous Window
-   **\` space** : Next Window
-   **\` ”**: Bring up a list of all the windows

