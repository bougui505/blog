---
title: "Check if there is missing CA in a pdb file"
layout: default
date: 2016-05-30
tags:
- awk
- pdb
---

# Check if there is missing CA in a pdb file

Below is a simple awk script that return the number of missing CA in a PDB file:

{% gist cc94b9c57087187eb7518060e6561a39 %}

Usage:

    ./check_pdb.awk pdbfile
