---
title: "Make a pdf format slideshow from a unique svg file"
layout: default
date: 2015-11-27
tags:
- inkscape
- svg
---

# Make a pdf format slideshow from a unique svg file

This post is related to this post: [Making a slideshow for a speech from Inkscape]({% post_url 2015-08-28-svg_to_pdf %})

You simply have to design your slides in Inkscape and delineate them by a
rectangle. Once this is done, you group all the object that constitute a slide.
Then, you have to name this object `slide1`. Repeat this operation for the
other slides: `slide2`, `slide3`, ..., `slideN`, where `N` is the total number
of slides.

Then, use the script below, with this command line:

    ./sozi_to_pdf.sh file.svg out.pdf

This script is called after [sozi](http://sozi.baierouge.fr/) extension to
Inkscape. It can be used to convert a Sozi presentation to pdf, with no need to
install [this script](http://sozi.baierouge.fr/pages/tutorial-converting.html)
with PhantomJS library.

{% gist 39e33fc7f811ee6da931 %}
