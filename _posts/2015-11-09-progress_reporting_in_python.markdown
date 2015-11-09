---
title: "Progress reporting in python"
layout: default
date: 2015-11-09
tags:
- python
---

# Progress reporting in python

Can be useful in IPython notebook to monitor a progress without displaying huge
number of lines with print command. The expected time for arrival (ETA) is
given.

Usage:

{% highlight python %}
import time
import progress_reporting as Progress
n = 1000
progress = Progress.Progress(n, delta=10)
for i in range(n):
    time.sleep(0.01)
    progress.count()
{% endhighlight %}

Sample output:

    10 % ETA: 0:00:08.995230
    20 % ETA: 0:00:07.999784
    30 % ETA: 0:00:06.999839
    40 % ETA: 0:00:05.999814
    50 % ETA: 0:00:04.999885
    60 % ETA: 0:00:03.999876
    70 % ETA: 0:00:02.999919
    80 % ETA: 0:00:01.999954
    90 % ETA: 0:00:00.999971

{% gist 0a1e82708a7f24c85fb4 %}
