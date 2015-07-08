---
title: "The plotutils package"
layout: default
category: linux
date: 2015-07-08
tags:
- linux
---

# The plotutils package

From the [official website](http://www.gnu.org/software/plotutils/):

> The GNU plotutils package contains software for both programmers and technical users. Its centerpiece is libplot, a powerful C/C++ function library for exporting 2-D vector graphics in many file formats, both vector and bitmap. On the X Window System, it can also do 2-D vector graphics animations.

Example of usage to plot 1 column data file (`data.txt`):

    graph --auto-abscissa -T ps dat.txt | display
