---
title: "Modeller: generate an extended protein conformation from an initial PDB file"
layout: default
date: 2016-07-28
tags:
- modeller
- python
---

# Modeller: generate an extended protein conformation from an initial PDB file

The script below takes a pdb file as argument and reads its sequence and
topology to generate an extended conformation of the protein. The output file
is a pdb file named `modeller_out.pdb`.

Usage:

    ./generate_extended.py protein.pdb

{% gist e30a41e06c50eb8863cf43a4fa5d5743 %}
