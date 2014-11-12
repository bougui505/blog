---
title: "Sum elements of an array from given labels in python without for loop"
layout: default
category: python
date: 2014-11-12 18:05:49 CET
tags:
- python
---

# Sum elements of an array from given labels in python without for loop

'For loops' are slow in python.
That's why it's better to use numpy or scipy functions.
Here a simple example on how to sum given element of `b` given the index `a` of `c`:

{% highlight python %}
import numpy
import scipy.ndimage
a = numpy.asarray([0,0,0,4,4,4,3,3])
b = numpy.random.uniform(size=len(a))
c = numpy.zeros(5)
uni_a = numpy.unique(a)
c[uni_a] = scipy.ndimage.measurements.sum(b,labels=a, index=uni_a)
{% endhighlight %}
