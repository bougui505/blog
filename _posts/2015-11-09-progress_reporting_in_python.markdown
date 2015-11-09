---
title: "Progress reporting in python"
layout: default
date: 2015-11-09
tags:
- python
---

# Progress reporting in python

Can be useful in IPython notebook to monitor a progress without displaying huge
number of lines with print command.

Usage:

{% highlight python %}
import time
import basic_progress_reporting as bprogress
n = 1000
progress = bprogress.Progress(n, delta=10)
for i in range(n):
    time.sleep(0.01)
    progress.count()
{% endhighlight %}

Sample output:

    10 %
    20 %
    30 %
    40 %
    50 %
    60 %
    70 %
    80 %
    90 %

{% gist 0a1e82708a7f24c85fb4 %}
