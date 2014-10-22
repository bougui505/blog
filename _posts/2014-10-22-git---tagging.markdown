---
title: "Git - tagging"
layout: default
category: git
date: 2014-10-22 11:44:53 CEST
tags:
- git
---

# Git - tagging

A lightweight tag in git is just a bookmark of a specific commit.

To create a tag just run the command:

    $ git tag my_tag_name -m "Tag message"

Do not use spaces in tag name.

To list tags:

    $ git tag -ln
    my_tag_name     Tag message

You can see the tag data along with the commit that was tagged by using the git show command:

    $ git show my_tag_name
