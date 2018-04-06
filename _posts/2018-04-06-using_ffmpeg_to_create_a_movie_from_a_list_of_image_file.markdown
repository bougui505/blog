---
title: "Using ffmpeg to create a movie from a list of image file"
layout: default
date: 2018-04-06
tags:
- ffmpeg
---

# Using ffmpeg to create a movie from a list of image file

    ffmpeg -framerate 10 -i image_%04d.png -acodec copy -vcodec copy movie.avi
