---
title: "Reload library automatically in IPython notebook"
layout: default
category: python
date: 2015-03-31 17:01:31 CEST
tags:
- python
---

From [autoreload IPython documentation](https://ipython.org/ipython-doc/dev/config/extensions/autoreload.html):

> autoreload reloads modules automatically before entering the execution of code typed at the IPython prompt.

> %autoreload 2
> Reload all modules (except those excluded by %aimport) every time before executing the Python code typed.

Working example:

    %load_ext autoreload
    %autoreload 2
