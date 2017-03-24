---
title: "Recording movie with chimera"
layout: default
date: 2017-03-24
tags:
- chimera
---

# Recording movie with chimera

Save each frame as a `png` in `movie` directory with pattern `movie_*`. Turn the molecule along the x-axis from 0 to 360 degrees:

    movie record format png directory movie pattern movie_*; turn y 1 360; wait; movie stop; movie reset
