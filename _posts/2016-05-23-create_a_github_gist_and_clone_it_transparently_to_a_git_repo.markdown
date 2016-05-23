---
title: "Create a Github gist and clone it transparently to a git repo"
layout: default
date: 2016-05-23
tags:
- git
- github
---

# Create a Github gist and clone it transparently to a git repo

This script depends of `gist-paste`. To install it on Debian:

    sudo apt-get install gist

The script below creates a gist and clone the resulting git repo to your
current working directory to transparently obtain a git repo:

{% gist cf4244d31e4ee4c4de1a11e985135d3b %}

Usage:

    gist-clone your_file

Then, you can directly commit and push your changes to gist using:

    git commit -a -m "Your commit message"
    git push
