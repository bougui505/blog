---
title: "Process each frame of a DCD trajectory file using any script file using a standard PDB file as input"
layout: default
date: 2017-08-30
tags:
- science
- catdcd
- dcd
---

# Process each frame of a DCD trajectory file using any script file using a standard PDB file as input

Example usage:

    process_dcd traj.dcd topo.pdb "myscript {} arg2 arg3 ..."

{% gist bc327291a686a3245c39176df6bd2dd8 %}
