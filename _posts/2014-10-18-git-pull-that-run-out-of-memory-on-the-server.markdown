---
title: "Git pull that run out of memory on the server"
layout: default
category: git
date: 2014-10-18 22:35:18 CEST
tags:
- git
- raspberry-pi
---

# Git pull that run out of memory on my raspberry pi server

I made a private git server with my raspberry pi.
When you try to pull a big git project with large binary files you can get out of memory on the server.
I found a quick fix in [stackoverflow](http://stackoverflow.com/questions/7362709/git-pull-fails-with-bad-pack-header-error):

{% highlight bash %}
git config --global pack.windowMemory "100m"
git config --global pack.packSizeLimit "100m"
git config --global pack.threads "1"
{% endhighlight %}

Now everything works well.
