---
title: "Select a subset of atoms from a trajectory file with MDanalysis"
layout: default
date: 2015-11-04
tags:
- mdanalysis
- python
---

# Select a subset of atoms from a trajectory file with MDanalysis

Usage:

    ./select_atoms_from_dcd.py topology.[pdb,psf,crd,gro] trajectory.[dcd,xtc,trr,xyz] outfile.[dcd,npy] 'selection string'

See [MDAnalysis documentation](https://pythonhosted.org/MDAnalysis/documentation_pages/overview.html)
for accepted input files for topology and trajectory.

If the output file name is with `npy` extension a numpy file is outputted with
an array containing the atomic coordinates of the selected atoms. This file
format can be convenient to perform analysis on coordinates with python.

See [MDAnalysis documentation](https://pythonhosted.org/MDAnalysis/documentation_pages/selections.html)
for selection syntax.

{% gist 0411d863a2c6d2df4bcc %}
