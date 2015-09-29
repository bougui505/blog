---
title: "zsh tips and tricks"
layout: default
date: 2015-09-29
tags:
- zsh
- linux
---
{% comment %}
Syntax HELP for markdown

Code snippet highlighting:
{% highlight python %}
PYTHON CODE
{% endhighlight %}

Post URL:
If you would like to include a link to a post on your site, the post_url tag
will generate the correct permalink URL for the post you specify.
{% post_url 2010-07-21-name-of-post %}

Gist:
{%gist 5a04655ce65766f143e0 %}

Including images and resources:
![My helpful screenshot]({{ site.url }}/assets/screenshot.jpg)

{% endcomment %}

# zsh tips and tricks

- Create temporary file, on the fly, containing the results of a command:

{% highlight bash %}
multivalue =(awk '{print $4","$5","$6}' 4MBR.dms) 4MBO.dx 4MBO.surf
{% endhighlight %}

Will get the columns 4, 5 and 6 as input of multivalue
