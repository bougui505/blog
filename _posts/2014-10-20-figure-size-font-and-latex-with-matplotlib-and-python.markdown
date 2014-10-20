---
title: "Figure size, font and LaTeX with matplotlib and python"
layout: default
category: python
date: 2014-10-20 15:20:21 CEST
tags:
- python
- matplotlib
- LaTeX
---

# Figure size font and LaTeX with matplotlib and python

To change the font in matplotlib and use LaTeX:

{% highlight python %}
from pylab import * # or %pylab inline in ipython notebook
fontsize=18
rc('font',**{'family':'sans-serif','sans-serif':['Helvetica'],'size':fontsize})
rc('text', usetex=True)
{% endhighlight %}

To change the default figure size:

{% highlight python %}
rcParams['figure.figsize'] = 18,14
{% endhighlight %}
