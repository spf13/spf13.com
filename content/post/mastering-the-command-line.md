---
Description: ""
Keywords:
- Development
- Systems
- bash
- cli
- command line
- emacs
Section: post
Slug: mastering-the-command-line
Tags:
- bash
- cli
- command line
- emacs
Thumbnail: /uploads/2009/11/300px-Keyboard-left_keys.jpg
Title: Mastering the Command Line
Topics:
- Development
- Systems
Url: post/mastering-the-command-line
date: 2009-11-05
disqus_identifier: 177 http://localhost/~sfrancia/wordpress/?p=177
disqus_title: Mastering the Command Line
disqus_url: http://spf13.com/post/mastering-the-command-line/
---

{{% img src="/media/Keyboard-left_keys.jpg" class="third right" %}}

If you use *nix, no doubt you’ve spent some time on the [command
line](http://en.wikipedia.org/wiki/Command-line_interface "Command-line interface").
Here are a few of the most helpful tricks you can use in the bash shell
to really optimize your time, impress your friends, and make everyone
else feel inferior… not to mention become more productive. People
familar with the command line can usually work considerably faster (for
most tasks) than you can through a gui. So be brave, embrace the
keyboard and master the [bash
shell](http://tiswww.case.edu/php/chet/bash/bashtop.html "Bash").

[Bash](http://tiswww.case.edu/php/chet/bash/bashtop.html "Bash") heavily
uses two
keys, [Ctrl](http://en.wikipedia.org/wiki/Control_key "Control key")
and [Meta](http://en.wikipedia.org/wiki/Meta_key). You’ll easily find
the Ctrl key on your keyboard, but the Meta, not so much (unless you’re
on a Sun system).. It’s also different for Mac vs PC. Point is commonly
called cursor.

All tips taken from the very large man file (man bash), with my
additional commentary. Please reference that file for more information.

Moving around
-------------

beginning-of-line **(Ctrl-a)**
 Move to the start of the current line.

end-of-line **(Ctrl-e)**
 Move to the end of the line.

forward-word **(Meta-f)**
 Move forward to the end of the next word.  Words are composed of
alphanumeric characters (letters and digits).
 This means that { / . _  } – are all word breaks, not just the usual
space.

backward-word **(Meta-b)**
 Move back to the start of the current or previous word. Words are
composed of alphanumeric characters (letters and digits), meaning

character-search **(Ctrl-], Character)**
 A character is read and point is moved to the next occurrence of that
character.  A negative count searches for previous occurrences.

character-search-backward **(Meta-Ctrl-], Character)**
 A character is read and point is moved to the previous occurrence of
that character.  A negative count searches for subsequent occurrences.

Manipulating text
-----------------

shell-expand-line **(Meta-Ctrl-e)**
 Expand the line as the shell does.  This performs alias and history
expansion as well as all of the shell word expansions.  See HISTORY
EXPANSION below for a  description of history expansion.

insert literal **(Ctrl-v, Character)**
 Use this to insert a tab character or a Ctrl-v, Ctrl-q or other
character.

upcase-word **(Meta-u)**
 Uppercase the current (or following) word.  With a negative argument,
uppercase the previous word, but do not move point.

lowcase-word **(Meta-l)**
 Lowercase the current (or following) word.  With a negative argument,
lowercase the previous word, but do not move point.

capitalize-word **(Meta-c)**
 Capitalize the current (or following) word.  With a negative argument,
capitalize the previous word, but do not move point.

transpose-words **(Meta-t)**
 Switch the word the point is on with the following one.

Deleting text
-------------

kill-line forward **(Ctrl-k)**
 Kill the text from point to the end of the line.

backward-kill-line **(Ctrl-x, Rubout)**
 Kill backward to the beginning of the line. Rubout is another name for
backspace.

kill-word **(Meta-d)**
 Kill from point to the end of the current word, or if between words, to
the end of the next word.  Word boundaries are the same as those used by
forward-word.

backward-kill-word **(Meta-Rubout)**
 Kill the word behind point.  Word boundaries are the same as those used
by backward-word. Rubout is another name for backspace.

unix-word-rubout **(Ctrl-w)**
 Kill the word behind point, using white space as a word boundary.  The
killed text is saved on the kill-ring.

Completion
----------

complete **(TAB)**
 Attempt  to  perform  completion on the text before point.  Bash
attempts completion treating the text as a variable (if the text begins
with **$), username (if the text begins with **~), hostname (if the text
begins with @), or command (including aliases and functions) in turn. 
If none of these produces a match, filename completion  is attempted.

complete-filename **(Meta-/)**
 Attempt filename completion on the text before point.

complete-username **(Meta-~)**
 Attempt completion on the text before point, treating it as a username.

complete-variable**(Meta-$)**
 Attempt completion on the text before point, treating it as a shell
variable.

complete-hostname **(Meta-@)**
 Attempt completion on the text before point, treating it as a hostname.

complete-command **(Meta-!)**
 Attempt completion on the text before point, treating it as a command
name.  Command completion attempts to match the text against aliases,
reserved words, shell functions, shell builtins, and finally executable
filenames, in that order.

dynamic-complete-history **(Meta-TAB)**
 Attempt completion on the text before point, comparing the text against
lines from the history list for possible completion matches.

complete-into-braces **(Meta-{)**
 Perform filename completion and insert the list of possible completions
enclosed within braces so the list is available to the shell. Remember
that “{” is shift “[".

Searching
---------

reverse-incremental-search **(Ctrl-r)**
 Press Ctrl-r and start typing, bash will search through your history
for a match.
 Press ctrl-g to abort and restore original line.

Using sets (braces)
-------------------

    cp /a/path/to/files/{this,that,some_other,more} here

Misc
----

clear-screen **(Ctrl-l)**
 Clear the screen leaving the current line at the top of the screen. 
With an argument, refresh the current line without clearing the screen.

Settings
--------

### Readline Variables

Readline has variables that can be used to further customize its
behavior.  A variable may be set in the inputrc file with a statement of
the form, defaults in parentesis

    set variable-name value
    

**editing-mode (emacs)**

Controls whether readline begins with a set of key bindings similar to
emacs or vi.  editing-mode can be set to either emacs or vi.

**keymap (emacs)**

Set the current readline keymap.  The set of valid keymap names is
emacs, emacs-standard, emacs-meta, emacs-ctlx, vi, vi-command, and
vi-insert.  vi is  equivalent  to vi-command; emacs is equivalent to
emacs-standard.  The default value is emacs; the value of editing-mode
also affects the default keymap.

**show-all-if-ambiguous (Off)**

This alters the default behavior of the completion functions.  If set
to on, words which have more than one possible completion cause the
matches to be listed  immediately instead of ringing the bell.
