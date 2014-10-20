---
title: "Truncate header in fancyhdr"
layout: default
category: LaTeX
date: 2014-10-20 10:51:10 CEST
tags:
- LaTeX
---

# Truncate header in fancyhdr

Sometime header overlaps with fancyhdr when section titles are too long.
Here it's a possible fix from [stackoverflow](http://tex.stackexchange.com/questions/41277/how-to-cut-a-section-title-in-the-header):

{% highlight latex %}
{% raw %}
\usepackage{fancyhdr}
\usepackage[hyphenate]{truncate} % hyphenate words. Other options are: breakwords, breakall

\fancypagestyle{truncatehdr}{%
\fancyhf{} % remove everything
\lhead{\truncate{15em}{\leftmark}}
\rhead{\truncate{15em}{\rightmark}}}

\pagestyle{truncatehdr}
{% endraw %}
{% endhighlight %}

In this way you truncate the header to fit in.
