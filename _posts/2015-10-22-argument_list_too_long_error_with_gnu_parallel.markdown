---
title: " error with GNU parallel"
layout: default
date: 2015-10-22
tags:
- parallel
---

# Argument list too long error with GNU parallel

When the number of arguments is too long, GNU parallel raises a `Argument list too long` error.

A possible solution is to use the `find` command:

{% highlight bash %}
    find directory -name "*.dat" |\
    parallel -k --eta "grep Chi {} | awk -F'Chi = ' '{print $2}'" > out.txt
{% endhighlight %}

instead of the classical syntax:

{% highlight bash %}
    ls directory/*.dat |\
    parallel -k --eta "grep Chi {} | awk -F'Chi = ' '{print $2}'" > out.txt
{% endhighlight %}

or

{% highlight bash %}
    parallel -k --eta "grep Chi {} | awk -F'Chi = ' '{print $2}'" ::: directory/*.dat > out.txt
{% endhighlight %}
