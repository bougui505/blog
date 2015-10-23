---
title: "Compute native contacts ratio from a dcd trajectory file with MD-Analysis"
layout: default
date: 2015-10-23
tags:
- mdanalysis
- python
- science
---

# Compute native contacts ratio from a dcd trajectory file with MD-Analysis

Usage:

    native_contacts.py file.dcd file.pdb file.psf [any valid selection string]

The selection string is optional and can be any valid selection string for
selectAtoms() that produces identical selections in mobile and reference. e.g.
`"resid 6-91"`

I don't know why but the number of native contacts for the last frame is not
computed, for the version of MDAnalyis I use (0.7.3).

{% gist cc8415df4102becceede %}
