---
title: "Align dcd trajectory with MDAnalysis"
layout: default
date: 2015-10-22
tags:
- mdanalysis
- python
- science
---

# Align dcd trajectory with MDAnalysis

Usage:

    align_dcd.py file.dcd file.pdb file.psf [any valid selection string]

The selection string is optional and can be any valid selection string for
selectAtoms() that produces identical selections in mobile and reference. e.g.
`"resid 6-91"`

{% gist b5fbdb2de5b9c1ff106e %}
