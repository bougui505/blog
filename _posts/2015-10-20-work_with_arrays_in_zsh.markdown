---
title: "Work with arrays in zsh"
layout: default
date: 2015-10-20
tags:
- zsh
---

# Work with arrays in zsh

{% highlight bash %}
$ a=(a b c)
$ echo $a
a b c
$ echo $a[1]
a
$ echo $a[2]
b
{% endhighlight %}

## Iterate values:

{% highlight bash %}
$ for x in $a; do echo $x; done
a
b
c
{% endhighlight %}

## Append values

{% highlight bash %}
$ a=()
$ a+=1
$ echo $a
1
$ a+=2
$ echo $a
1 2
{% endhighlight %}

## Get the length of the array

{% highlight bash %}
$ echo ${#a[@]}
3
{% endhighlight %}
