---
title: "Create animated gif from multiple images with ImageMagick"
layout: default
date: 2016-02-23
tags:
- imagemagick
---

# Create animated gif from multiple images with ImageMagick

    convert -delay 6 -quality 95 -layers OptimizePlus montage_?????.png movie.gif

[OptimizePlus](http://www.imagemagick.org/Usage/anim_opt/#optimizeplus) reduces
the final size of the gif file by performing an optimization.
