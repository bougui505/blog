---
title: "Do not display long line with awk"
layout: default
category: awk
date: 2014-11-06 14:07:18 CET
tags:
- awk
---

# Do not display long line with awk: usage with IPython notebooks

IPython notebook embeds image in the `.ipynb` file which produces huge lines.
It's not convenient to display the raw text in a terminal.
Awk can be used to filter the display:

    awk 'length($0)<1000' myfile.ipynb | less

With this command you won't display line with more than 999 characters.
