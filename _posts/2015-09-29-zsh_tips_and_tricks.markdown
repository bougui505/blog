---
title: "zsh tips and tricks"
layout: default
date: 2015-09-29
tags:
- zsh
- linux
---

# zsh tips and tricks

## Create temporary file, on the fly, containing the results of a command:

{% highlight bash %}
multivalue =(awk '{print $4","$5","$6}' 4MBR.dms) 4MBO.dx 4MBO.surf
{% endhighlight %}

Will get the columns 4, 5 and 6 as input of multivalue

## Get the filename without extension

{% highlight bash %}
$ pdbfile=pdb2l0s.ent.gz
$ echo $pdbfile:r
pdb2l0s.ent
{% endhighlight %}
