---
title: "Get a range of script arguments in zsh"
layout: default
date: 2015-10-21
tags:
- zsh
---

# Get a range of script arguments in zsh

## Get, for example, 3 arguments from the fourth one:

{% highlight bash %}
for x in ${@:4:3}; do
    echo $x
done
{% endhighlight %}

## Get all the arguments:

{% highlight bash %}
for x in $@; do
    echo $x
done
{% endhighlight %}

## Get all the arguments from the second one:

{% highlight bash %}
for x in ${@:2}; do
    echo $x
done
{% endhighlight %}

