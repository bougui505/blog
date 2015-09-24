---
title: "Awk: determine if a string is numeric"
layout: default
category: linux
date: 2015-09-24
tags:
- linux
- awk
---

# Awk: determine if a string is numeric

    awk 'function isnum(x){return(x==x+0)} {if (isnum($1)) {print $1}}'

Will print `$1` only if the content is numeric.
