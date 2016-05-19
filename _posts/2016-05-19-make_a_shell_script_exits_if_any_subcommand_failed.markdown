---
title: "Make a shell script exits if any subcommand failed"
layout: default
date: 2016-05-19
tags:
- linux
---

# Make a shell script exits if any subcommand failed

Sometimes, it's very useful that a shell script exists when an error is
encountered (if any subcommand or pipeline returns a non-zero status).

To get this behaviour just add `set -e` in the beginning of the script.
