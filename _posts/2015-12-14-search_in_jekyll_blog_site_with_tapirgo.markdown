---
title: "Search in Jekyll blog site with TapirGo"
layout: default
date: 2015-12-14
tags:
- jekyll
- TapirGo
---

# Search in Jekyll blog site with TapirGo

[TapirGo](http://tapirgo.com/) is free, third party service for searching RSS
feeds.

- First of all, you need to generate a full xml file of your site with the
standard `feed.xml` at the root of your blog site:

{% gist 6c3b4b36a383290d624d %}

- Subscribe to [TapirGo](http://tapirgo.com/) and give the link to the `feed.xml`
page.

- Create the file `search.html` at the root directory:

{% gist 39ba5044e902a1a0efef %}

Replace `YOUR_TOKEN` by your token given by [TapirGo](http://tapirgo.com/).

- and the file `jquery-tapir.min.js` from this
[Github](https://github.com/TapirGo/jQuery-Plugin) repository:

{% gist f597289d82e9a0090386 %}


- Add the search box in the index page (`index.html` file):

{% gist 35cd2416a5ff8ce8af92 %}
