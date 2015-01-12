---
title: "Vim: find exactly n starting spaces"
layout: default
category: vim
date: 2015-01-12 10:43:28 CET
tags: 
- vim
---

# Vim: find exactly $$n$$ starting spaces

For example if $$n=3$$:

    /^\s\{3\}\(\s\)\@!

The basic idea is to find 3 starting space:

    ^\s\{3\}

Not followed by space:

    \(\s\)\@!
