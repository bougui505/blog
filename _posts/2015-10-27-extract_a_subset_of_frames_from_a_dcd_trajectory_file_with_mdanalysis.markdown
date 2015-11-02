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

    ./extract_frames_from_dcd.py file.pdb file.dcd outfile.dcd frame_list_file.txt

The `frame_list_file.txt` is an ASCII file containing one frame id per line,
starting from 0. Repetitions of frames are allowed and will be kept in the
output file. The order of the frames will be preserved in the output DCD file.

If the list of frames is not given as a file, the standard input is read
instead. This feature is conveninant to pipe from awk, for example:

    awk '{print $3}' some_text_file.txt | ./extract_frames_from_dcd.py file.pdb file.dcd outfile.dcd

To extract all frames from a trajectory just give:

    ./extract_frames_from_dcd.py file.pdb file.dcd outfile.dcd all

{% gist 12537c00c8e1679577de %}
