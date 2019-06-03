---
title: "Split a file based on new line pattern"
layout: default
date: 2019-06-03
tags:
- csplit
---

# Split a file based on new line pattern

    csplit -z -f intro_ -b '%02d.tex' sectionIntroduction_.tex '/\n/' {8}

with:

`intro_`: the prefix of the output file name
`%02d.tex`: the suffix of the output file name
`sectionIntroduction_.tex` the output file name
`/\n/` the pattern to match
`{8}` the number of repeat of the pattern
