---
date: 2013-11-07
description: Cobra is a commander providing a simple interface to create powerful
  modern CLI interfaces similar to git & go tools. In addition to providing an iterface,
  Cobra simultaneously provides a controller to organize your application code.
tags:
- hugo
- cobra
- go
- golang
- development
title: A modern CLI Commander for go
topics:
- Development
- golang
---

While developing [Hugo](http://hugo.spf13.com) I became disappointed
with the interface limitations flags alone provide. A quick look at
virtually any command line application (ls, grep, less, etc) reveals
that most applications overuse flags to do everything and often allow
conflicting flags to be applied.

Even though hugo is relatively simple, we already had the ability to
stack flags that didn't make sense. You can set the port using --port
but this only has an effect if you also specified --server. Clearly
another mechanism is needed.

Modern applications like git, brew and go use sub commands to control
actions that the application would perform. Each action in turn has a
set of flags associated with it. It's a great pairing that works well.

I quick something search for existing libraries turned up a few. Mostly
based off of the code written for the go tool, which wasn't intended to
be a general purpose library, but people began using it nonetheless.

I was disappointed to discover than none met my needs.
Unwilling to be deterred, I decided to build Cobra, a commander for
modern CLI go applications.

## Nested Sub Commands

A core requirement for Hugo commands was the ability to nest
subcommands. A planned feature of Hugo is the ability to install themes,
shortcodes and more from a central repository. While a possible
interface could look like 'hugo get --type=shortcode --name', I prefer
the interface 'hugo get shortcode NAME'.

This preferred interface could be accomplished while using existing
libraries, it would be through manual parsing of strings following the
command. This made no sense to me. If we already have a mechanism to
parse strings on the command line, why not use what we already have.

**Cobra supports as subcommands as many levels deep as you want to nest
them.**

## Commands all the way

Existing libraries all define a top level controller object which has
builders for each of the commands (of which they only support one
level). To me this seemed unnecessary and definitively un-go-like. 

In Cobra, everything is a command or a flag. The top level of the
application is a command which optional can run an action and optionally
have subcommands (at least one of these two is required). Each of the
children commands then can in turn have an action and children and so
forth.

Additionally **creating a command is as simple as creating a struct.** No
inflexible NewCommand methods needed.

## POSIX/GNU Flags

The go standard flag library is great. I really appreciate it's
simplicity and power. For unknown reasons the authors decided to throw
out decades of flag standards and define their own. I'm not a huge fan
of the GNU/POSIX style flags, but they work well enough and it's what
most people expect. If there's ever a place to do things in a new way,
this doesn't seem like it. Cobra has full support for POSIX flag
functionality provided by the [pflag
libary](https://github.com/ogier/pflag), a fork of the flag standard
library which maintains the same interface while adding POSIX
compliance.

Cobra has tight integration with this flag library. **Flags can be defined
globally, for a sub tree or for a specific command.**

## Extensibility

In each of the existing libraries they had code that had conditional
logic to check if the first string was 'help', then they ran a different
code path. This hard coded logic meant that if you used these libraries
you either had to fork them or were stuck with their help routine.
Additionally I have a philosophical issue with using conditional logic
to handle a specific command. If you are building a commander to handle
arbitrary commands, why not use that mechanism to define help.

Cobra's help functionality is a command and provides a high degree of
customization without forking.

## Conclusion

Find Examples, Documentation & Cobra at http://github.com/spf13/cobra

Contributions and feedback welcome.
