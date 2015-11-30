---
title: "Smart copy of photos from external memory card"
layout: default
date: 2015-11-30
tags:
- photos
- linux
- shell
- zsh
---

# Smart copy of photos from external memory card

This script makes a directory hierarchy by date (`YYYY/MM/DD`) and do not
transfer photos already transfered.

## Usage:

    ./get_photos.sh /path/to/the/mounted/memory/card

Don't forget to change the destination directory in the script...

{% gist 0aade36ec855acd8702a %}
