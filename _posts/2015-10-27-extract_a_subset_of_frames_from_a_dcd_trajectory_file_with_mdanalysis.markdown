---
title: "Extract a subset of frames from a DCD trajectory file with MDAnalysis"
layout: default
date: 2015-10-27
tags:
- python
- mdanalysis
---

# Extract a subset of frames from a DCD trajectory file with MDAnalysis

Usage:

    ./extract_frames_from_dcd.py file.pdb file.dcd outfile.dcd [frame_list_file.txt, all, -] [selection]

The `frame_list_file.txt` is an ASCII file containing one frame id per line,
starting from 0. Repetitions of frames are allowed and will be kept in the
output file. The order of the frames will be preserved in the output DCD file.

The list of frame can be specified from the standard input. Just put a `-`
instead of the `filename`. This feature is convenient to pipe from awk, for
example:

    awk '{print $3}' some_text_file.txt | ./extract_frames_from_dcd.py file.pdb file.dcd outfile.dcd -

`[selection]` is an optional argument. It's a string specifying the atom to
select (any valid selection string for `selectAtoms()`)

To extract all frames from a trajectory with a specified selection just give:

    ./extract_frames_from_dcd.py file.pdb file.dcd outfile.dcd all 'resid 6-91'

{% gist 12537c00c8e1679577de %}
