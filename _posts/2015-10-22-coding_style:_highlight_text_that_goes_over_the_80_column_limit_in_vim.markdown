---
title: "Coding style: highlight text that goes over the 80 column limit in vim"
layout: default
date: 2015-10-22
tags:
- vim
---

# Coding style: highlight text that goes over the 80 column limit in vim

Coding style: highlights the background in a subtle red for text that goes over the 80 column limit (from: [stackoverflow](http://stackoverflow.com/a/235970/1679629)).

    highlight OverLength ctermbg=LightRed ctermfg=black guibg=#592929
    match OverLength /\%81v.\+/
