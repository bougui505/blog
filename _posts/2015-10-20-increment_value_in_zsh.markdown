---
title: "Increment value in zsh"
layout: default
date: 2015-10-20
tags:
- zsh
---

# Increment value in zsh

{% highlight bash %}
$ i=0
$ echo $i
0
$ (( i+=1 ))
$ echo $i
1
{% endhighlight %}
