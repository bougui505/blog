---
title: "ZSH string manipulation: split string"
layout: default
date: 2016-02-29
tags:
- zsh
---

# ZSH string manipulation: split string

## Split string in a given word separator (`ws`)

For example `_`:

    bougui@mantrisse ~> x="foo_1"
    bougui@mantrisse ~> echo $x[(ws:_:)1]
    foo
    bougui@mantrisse ~> echo $x[(ws:_:)2]
    1
