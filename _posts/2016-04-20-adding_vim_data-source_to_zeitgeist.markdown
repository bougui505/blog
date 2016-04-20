---
title: "Adding vim data-source to Zeitgeist"
layout: default
date: 2016-04-20
tags:
- vim
- zeitgeist
- linux
---

# Adding vim data-source to Zeitgeist

Zeitgeist is a software service which logs the users's activities and events,
like files opened. However, Zeitgeist detects mainly files opened using Gnome
applications like Gedit for text files. However, using Vim, Zeitgeist doesn't
detect file opening.

Below is a nice Vim plugin that I found
[here](https://github.com/jeffwheeler/vimfiles/blob/master/plugin/zeitgeist.vim)
to add Vim as a data-source for Zeitgeist:

{% gist a0cbacb2eb9dad685aff6b24c2ab8792 %}
