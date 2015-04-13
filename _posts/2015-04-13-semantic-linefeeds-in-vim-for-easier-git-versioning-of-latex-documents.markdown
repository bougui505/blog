---
title: "Semantic linefeeds in vim for easier git versioning of LaTeX documents"
layout: default
category: vim
date: 2015-04-13 10:10:49 CEST
tags:
- vim
- LaTeX
---

# Semantic linefeeds in vim for easier git versioning of LaTeX documents

One sentence per line is an easy way to create text file easier to edit and version control with Git for example.

![Third Way](/assets/third_way.png)

(From [XKCD](http://xkcd.com/1285/))

In Vim you can easily create a macro to format the current paragraph:

    qa
    vip
    :'<,'>s/\n/ / | '<,'>s/\. /\.^M/g
    q

and call the macro with:

    @a
