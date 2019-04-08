---
title: "Transfer file through ssh using tar and pv"
layout: default
date: 2019-04-08
tags:
- ssh
- tar
- pv
---

# Transfer file through ssh using tar and pv

    tar -zc your_directory | pv -s 10g | ssh hostname "tar -zx -C /path/to/the/target/directory"

Notes: -s SIZE: Assume the total amount of data to be transferred is SIZE bytes when calculating percentages  and  ETAs. The same suffixes of "k", "m" etc can be used as with -L. A suffix of "k", "m", "g", or "t" can be added to denote kilobytes (*1024), megabytes, and so on.
