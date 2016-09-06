---
title: "Modeller: generate an extended protein conformation from an initial PDB file"
layout: default
date: 2016-07-28
tags:
- modeller
- python
- science
---

# Modeller: generate an extended protein conformation from an initial PDB file

The script below takes a pdb file as argument and reads its sequence and
topology to generate an extended conformation of the protein. The output file
is a pdb file named `modeller_out.pdb`.

Usage:

    ./generate_model.py protein.pdb

EDIT: The default behaviour is to generate an extended conformation via the
keyword `initialize_xyz=True`. However, it can be useful to build a native like
conformation using the coordinates of the input pdb, for example to repair a
buggy pdb file. In that case just call the script as below:

    ./generate_model.py protein.pdb native

{% gist e30a41e06c50eb8863cf43a4fa5d5743 %}
