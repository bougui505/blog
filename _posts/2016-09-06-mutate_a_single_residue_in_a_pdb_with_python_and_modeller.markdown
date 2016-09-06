---
title: "Mutate a single residue in a pdb with python and Modeller"
layout: default
date: 2016-09-06
tags:
- python
- modeller
- science
---

# Mutate a single residue in a pdb with python and Modeller

From [this modeller wiki page](http://salilab.org/modeller/wiki/Mutate%20model):

The script below takes a given PDB file, and mutates a single residue. The
residue's position is then optimized, and the unoptimized and optimized
energies are reported.

Note that this script if run multiple times will produce the same model each
time, because Modeller is deterministic. If you want to build multiple models,
change the value of rand_seed (see comments in the script) each time. This may
be useful if some models, for example, cannot be optimized due to steric
clashes.

{% gist efbd203e70f9103d329404ec18778ebb %}
