---
title: "Compute theoretical SAXS profile for each frame of a dcd format trajectory and the corresponding Chi value from experimental data"
layout: default
date: 2015-10-22
tags:
- saxs
- imp
- parallel
- catdcd
- science
---

# Compute theoretical SAXS profile for each frame of a dcd format trajectory and the corresponding Chi value from experimental data

This script compute the theoretical SAXS profile for each frame of a `dcd` format trajectory.
The corresponding chi value is computed from experimental data.

Dependencies:

- [catdcd](http://www.ks.uiuc.edu/Development/MDTools/catdcd/)
- [IMP, the Integrative Modeling Platform](https://integrativemodeling.org/)
- [GNU parallel](http://www.gnu.org/software/parallel/) [See this blog post]({% post_url 2015-09-14-gnu_parallel %})

I use two functions detailed in other blog posts:

- [`splitpdb`]({% post_url 2015-10-21-split_a_multi_model_pdb_from_shell %})
- [`mspdb`]({% post_url 2014-10-18-work-with-protein-data-bank-pdb-files-and-awk %})

Two scripts are required:

- The main shell script:

{% gist 2fa82c1d039155503416 %}

- The IMP python script:

{% gist 7d32ce504bfbff965ee4 %}
