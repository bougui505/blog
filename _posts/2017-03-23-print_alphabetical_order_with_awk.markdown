---
title: "Print alphabetical order with awk"
layout: default
date: 2017-03-23
tags:
- awk
---

# Print alphabetical order with awk

    $ for i in $(seq 10); do echo $i; done | awk 'BEGIN {split("ABCDEFGHIJKLMNOPQRSTUVWXYZ", A, "")}{print $0, A[$0]}'
    1 A
    2 B
    3 C
    4 D
    5 E
    6 F
    7 G
    8 H
    9 I
    10 J
