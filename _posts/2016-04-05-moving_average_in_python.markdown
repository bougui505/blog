---
title: "Moving average in python"
layout: default
date: 2016-04-05
tags:
- python
---

# Moving average in python

Below is the code for computing a moving average in python:

{% highlight python %}
def movingaverage(data, window_size):
    window= numpy.ones(int(window_size))/float(window_size)
    return numpy.convolve(data, window, 'same')

plot(-logE, '-', color='gray', alpha=.25)
plot(movingaverage(-logE, 500), 'r', linewidth=3.)
{% endhighlight %}

![moving_average](/assets/moving_average.png)
