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

{% gist 12537c00c8e1679577de %}
