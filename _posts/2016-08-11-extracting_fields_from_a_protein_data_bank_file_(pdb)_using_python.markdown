---
title: "Extracting fields from a Protein Data Bank file (PDB) using python"
layout: default
date: 2016-08-11
tags:
- python
- pdb
---

# Extracting fields from a Protein Data Bank file (PDB) using python

Sometime, for large `pdb` files, one cannot use the `split` command from python.
Below is the python line to extract fields from a `pdb` file:

{% highlight python %}
with open('min.pdb') as pdbfile:
    for line in pdbfile:
        print line
        splitted_line = [line[:6], line[6:11], line[12:16], line[17:20], line[21], line[22:26], line[30:38], line[38:46], line[46:54]]
        print splitted_line
        print "%-6s%5s %4s %3s %s%4s    %8s%8s%8s\n"%tuple(splitted_line)
{% endhighlight %}

Sample output:

    # Original line
    HETATM10000  O   HOH B3257       2.509  40.006  -4.097  1.00  0.00           O
    # Splitted line
    ['HETATM', '10000', ' O  ', 'HOH', 'B', '3257', '   2.509', '  40.006', '  -4.097']
    # Go back to pdb formatted line
    HETATM10000  O   HOH B3257       2.509  40.006  -4.097
