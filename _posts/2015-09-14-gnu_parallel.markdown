---
title: "GNU parallel"
layout: default
category: linux
date: 2015-09-14
tags:
- linux
- parallel
---

# GNU parallel

[GNU parallel is a command-line driven utility for Linux or other Unix-like operating systems which allows the user to execute shell scripts in parallel. GNU parallel is free software, written by Ole Tange in Perl. It is available under the terms of GPLv3.](https://en.wikipedia.org/wiki/GNU_parallel)

For example, to process listed files in parallel:

{% highlight bash %}
    ls relax/????c2qjkM_.1_????_noH.pdb | parallel -k --eta ./rmsd.awk c2qjkM_.1.pdb {} > rmsds.txt
{% endhighlight %}

    -k             Keep same order
    --eta          Show the estimated number of seconds before finishing

`parallel` replaces `{}` by the output files of `ls` for this example.
