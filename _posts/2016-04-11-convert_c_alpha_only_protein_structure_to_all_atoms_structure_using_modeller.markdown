---
title: "Convert C alpha only protein structure to all atoms structure using Modeller"
layout: default
date: 2016-04-11
tags:
- modeller
- python
- science
---

# Convert C alpha only protein structure to all atoms structure using Modeller

Usage:

    ./modeller_ca_to_all_atoms.py input_structure_ca.pdb

It returns modeller_out.pdb, an all atoms structure.

The script extracts distances between C alpha atoms and read the beta factor
column of the pdb to get the standard deviation from the target distance and
applies a Gaussian distance restraint along with the stereochemical restraints
(BOND, ANGLE, DIHEDRAL, IMPROPER).

{% gist 07281e1e0156193c5ef047b1e0113106 %}
