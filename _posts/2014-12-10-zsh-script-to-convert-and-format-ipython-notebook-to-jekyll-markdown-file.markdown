---
title: "zsh script to convert and format iPython notebook to jekyll markdown file"
layout: default
category: linux
date: 2014-12-10 11:02:46 CET
tags:
- linux
- zsh
- jekyll
- python
---

iPython notebooks are very convenient for blogging.
`nbconvert` can easily convert `ipynb` file to markdown.
However some manual operations are required to format the resulting file:

- Adding the YAML header for jekyll
- Add the liquid tags for python syntax highlighting.

Below is the script to automatically format an `ipynb` file to jekyll markdown:

{% gist ddf7a6a5ffede1d17fc9 %}

Usage: `./ipynb_to_jekyll.sh ipynbfile "Title of the post"`

