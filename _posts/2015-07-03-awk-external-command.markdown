---
title: "Run external command with awk"
layout: default
category: awk
date: 2015-06-22
tags:
- awk
---

# Run external command with awk: example with cat command.

In the example below, you pass the filename `myfilename.pdb` to awk variable `x` and `cat` the content of the file each time `MODEL` is present in column 1 of the `inputfilename.pdb`:

    rec=myfilename.pdb
    awk -v x=$rec '{if ($1=="MODEL") system("cat " x); else {print $0}}' inputfilename.pdb
