---
title: "Deploy jekyll site with git"
layout: default
category: linux
date: 2014-12-06 22:20:11 CET
tags:
- linux
- jekyll
- git
---
# Deploy jekyll site with git

In the git bare repository of your server add this `post-update` file:

{% highlight bash %}
#!/usr/bin/env zsh
cd /path/to/the/server/git/repo
env -i git pull
env -i git push github master # for github backup (add github to the remote)
/path/to/jekyll build --destination /path/to/your/_site
{% endhighlight %}

Now when you push commits, the site is automaticcaly built.
