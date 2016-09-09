---
title: "Repair a protein using Modeller and python"
layout: default
date: 2016-09-09
tags:
- modeller
- science
- python
---

# Repair a protein using Modeller and python

The python script below use modeller to repair a given `pdb` file:

- adding missing hydrogens
- adding missing side chains
- adding missing backbone atoms from CA trace
- ...

{% gist e31d472e222d693b54b7391faaef7742 %}
