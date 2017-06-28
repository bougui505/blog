---
title: "Set the default language (english) for the fish (shell)"
layout: default
date: 2017-06-28
tags:
- fish
- linux
---

# Set the default language (english) for the fish (shell)

Just set the LC_ALL variable:

    set -U -x LC_ALL C

`-U` or `--universal` causes the specified shell variable to be given a universal scope. If this option is supplied, the variable will be shared between all the current users fish instances on the current computer, and will be preserved across restarts of the shell.
`-x` or `--export` causes the specified shell variable to be exported to child processes (making it an "environment variable")
