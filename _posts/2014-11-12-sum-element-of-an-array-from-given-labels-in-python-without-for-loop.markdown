---
title: "Sum elements of an array from given labels, in python, without for loop"
layout: default
category: python
date: 2014-11-12 18:05:49 CET
tags:
- python
---

# Sum elements of an array from given labels, in python, without for loop

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

Now some benchmarks:


{% highlight python %}
%pylab inline
import scipy.ndimage
import timeit
{% endhighlight %}


Initialization of the arrays:

{% highlight python %}
size = 100
a = numpy.random.randint(0,10, size=size)
b = numpy.random.uniform(size=len(a))
c = numpy.zeros(max(a)+1)
{% endhighlight %}

First the code with 'for loop':

{% highlight python %}
for k,i in enumerate(a):
    c[i] += b[k]
{% endhighlight %}

And now the code without 'for loop':

{% highlight python %}
uni_a = numpy.unique(a)
c2 = numpy.zeros(max(a)+1)
c2[uni_a] = scipy.ndimage.measurements.sum(b,labels=a, index=uni_a)
{% endhighlight %}

And the result is the same:

{% highlight python %}
(c == c2).all()
{% endhighlight %}

`out: True`

Now we'll benchmark the execution time, with the loop for 10 to 100 iterations in the loop:

{% highlight python %}
def time_loop(size=100):
    elapsed = []
    for l in range(100):
        a = numpy.random.randint(0,10, size=size)
        b = numpy.random.uniform(size=len(a))
        c = numpy.zeros(max(a)+1)
        start_time = timeit.default_timer()
        for k,i in enumerate(a):
            c[i] += b[k]
        elapsed.append(timeit.default_timer() - start_time)
    elapsed.sort()
    return numpy.mean(elapsed[:3])


elapsed = []
for s in range(10,100):
    elapsed.append(time_loop(s))
{% endhighlight %}

And without the loop:

{% highlight python %}
def time_noloop(size=100):
    elapsed = []
    for l in range(100):
        a = numpy.random.randint(0,10, size=size)
        b = numpy.random.uniform(size=len(a))
        c = numpy.zeros(max(a)+1)
        start_time = timeit.default_timer()
        uni_a = numpy.unique(a)
        c[uni_a] = scipy.ndimage.measurements.sum(b,labels=a, index=uni_a)
        elapsed.append(timeit.default_timer() - start_time)
    elapsed.sort()
    return numpy.mean(elapsed[:3])


elapsed_noloop = []
for s in range(10,100):
    elapsed_noloop.append(time_noloop(s))
{% endhighlight %}

{% highlight python %}
plot(range(10,100),elapsed,label='for loop')
plot(range(10,100),elapsed_noloop, label='no for loop')
grid()
legend()
xlabel('number of loop')
ylabel('execution time (s)')
{% endhighlight %}

And the result shows an obvious advantage to use the scipy function when the number of iterations is more than 50:

![png](/assets/no_for_loop_files/no_for_loop_14_1.png)

