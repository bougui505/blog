---
title: "zsh: show right prompt with date ONLY when command is executed"
layout: default
date: 2016-09-07
tags:
- zsh
---

# zsh: show right prompt with date ONLY when command is executed

{% gist ec54cca1b0517f85afbd954eb166c69c %}

NB: From the [zsh documentation on hook functions](http://zsh.sourceforge.net/Doc/Release/Functions.html#Hook-Functions):

`preexec`

Executed just after a command has been read and is about to be executed. If the
history mechanism is active (regardless of whether the line was discarded from
the history buffer), the string that the user typed is passed as the first
argument, otherwise it is an empty string. The actual command that will be
executed (including expanded aliases) is passed in two different forms: the
second argument is a single-line, size-limited version of the command (with
things like function bodies elided); the third argument contains the full text
that is being executed.
