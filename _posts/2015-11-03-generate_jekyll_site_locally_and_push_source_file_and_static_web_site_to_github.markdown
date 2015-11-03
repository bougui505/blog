---
title: "Generate jekyll site locally and push source file and static web site to github"
layout: default
date: 2015-11-03
tags:
- jekyll
- github
- git
---

# Generate jekyll site locally and push source file and static web site to github

- First, set the environment variable `BLOGDIR` to the directory containing the
source file for your blog.

- Set the origin remote repositories properly for the source directory and the
generated directory in `$BLOGDIR/_site`, the default in jekyll.

Then you can use the code below from the command line:

{% highlight bash %}
./jekyll_push.sh "Message of the git commit"
{% endhighlight %}

{% gist 85ce0e40d36ed7c8442d %}
