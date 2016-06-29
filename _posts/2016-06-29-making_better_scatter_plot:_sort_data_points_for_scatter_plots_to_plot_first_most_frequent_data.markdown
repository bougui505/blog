---
title: "Making better scatter plot: sort data points for scatter plots to plot first most frequent data"
layout: default
date: 2016-06-29
tags:
- matplotlib
- python
---

# Making better scatter plot: sort data points for scatter plots to plot first most frequent data

When plotting scatter plot, less frequent data are hidden by the most frequent
ones, leading to very crowded scatter plot, reducing the readability of the
plot:

{% highlight python %}
%pylab inline
data = numpy.genfromtxt('test.txt')
x = data[:,0]
y = data[:,1]
z = data[:,2]
scatter(x,y,c=z)
colorbar()
{% endhighlight %}

![scatter plot not sorted](/assets/scatter_plot.png)

The function below sort scatter data from the less frequent one to the most
frequent using a 3D histogram:

{% gist 5f6b4fa24272dc0501f6052ed4654abe %}

{% highlight python %}
data_sorted = sort_scatter_data(data)
x = data_sorted[:,0]
y = data_sorted[:,1]
z = data_sorted[:,2]
scatter(x,y,c=z)
colorbar()
{% endhighlight %}

The resulting graph shows a larger range of z-values depicted by the colorbar:

![scatter plot sorted](/assets/scatter_plot_sorted.png)
