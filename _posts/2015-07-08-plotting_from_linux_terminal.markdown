---
title: "Plotting from linux terminal"
layout: default
category: linux
date: 2015-07-08
tags:
- linux
---

# Plotting from linux terminal

## The plotutils package

From the [official website](http://www.gnu.org/software/plotutils/):

> The GNU plotutils package contains software for both programmers and technical users. Its centerpiece is libplot, a powerful C/C++ function library for exporting 2-D vector graphics in many file formats, both vector and bitmap. On the X Window System, it can also do 2-D vector graphics animations.

Example of usage to plot 1 column data file (`data.txt`):

    graph --auto-abscissa -T ps dat.txt | display

## ctioga2

From the [official website](http://ctioga2.sourceforge.net/index.html)

> ctioga2 is a powerful command-line based polymorphic plotting program, based on the Tioga plotting library.

> It produces publication-quality PDF files; you make yourself an opinion of those looking at the [gallery]{http://ctioga2.sourceforge.net/galleries.html}.

> It is a complete rewrite of ctioga. Compatibility was kept when it was not a problem. Most simple graphs from ctioga can be used directly with ctioga2.

> It benefits from several years of experience writing ctioga, and in particular which mistakes to avoid. It features an original polymorphic interface, which can be driven either using directly the command-line or through command-files.

Example of usage to plot 1 column data file (`data.txt`) in zsh:

    ctioga2 -X =(cat -n data.txt)

## Using matplotlib

You can use this command line interface of matplotlib (work in progress):

{% gist 8fb357f63547a757ee87}
