---
title: "Mathjax in jekyll based blog"
layout: default
category: jekyll
date: 2014-10-23 22:19:00 CEST
tags:
- jekyll
- LaTeX
---

# Mathjax in jekyll based blog

To write math in your jekyll blog you can use mathjax. To enable it, just add this line in `_includes/header.html`:

{% highlight html %}
{% raw %}
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
{% endraw %}
{% endhighlight %}

just after the line:

{% highlight html %}
{% raw %}
<header class="site-header">
{% endraw %}
{% endhighlight %}

That's all, now you can use mathjax with standard LaTeX commands. For inline math use the `$$` instead of `$`.
