---
title: "Sum over all columns with awk"
layout: default
category: awk
date: 2015-07-08
tags:
- awk
---

# Sum over all columns with awk

    awk '{for (i=1;i<=NF;i++) s[i]=$i+p[i]; p[i]=$i} END {for (i=1;i<=NF;i++) print s[i]}' your_file.txt
