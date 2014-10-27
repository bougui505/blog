---
title: "LaTeX acronym package"
layout: default
category: latex
date: 2014-10-23 09:55:21 CEST
tags:
- LaTeX
---

# LaTeX acronym package

From [CTAN](http://www.ctan.org/pkg/acronym):

This package ensures that all acronyms used in the text are spelled out in full at least once. It also provides an environment to build a list of acronyms used.

The basic usage is described below:

{% highlight latex %}
\usepackage[printonlyused, withpage]{acronym}
{% endhighlight %}

If you don't want to print the list of acronyms:

{% highlight latex %}
\usepackage[nolist]{acronym}
{% endhighlight %}

The options ensure that only used acronyms are printed out and that the page number of the first reference to the acronym is displayed.

In the text, when you want to use an acronym (here SOM) use this command:

{% highlight latex %}
\ac{SOM}
{% endhighlight %}

At the place you want to list the acronyms add this environment:

{% highlight latex %}
\begin{acronym}
\acro{SOM}{Self-Organizing Map}
\end{acronym}
{% endhighlight %}
