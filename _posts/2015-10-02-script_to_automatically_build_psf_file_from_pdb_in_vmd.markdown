---
title: "Script to automatically build psf file from pdb in VMD"
layout: default
date: 2015-10-02
tags:
- vmd
- zsh
- pdb
---

# Script to automatically build psf file from pdb in VMD

Here is the script:

{% gist f0fa80ae9f0abc42e2d9 %}

Just replace `PDB` with your pdb file name and launch the script with:

{% highlight bash %}
vmd -dispdev text -e autopsf.tcl
{% endhighlight %}

In zsh shell you can automatize this script for multiple pdb with:

{% highlight bash %}
for x in models/out_??.pdb; do
    echo $x
    vmd -dispdev text -e =(sed "s,PDB,$x," autopsf.tcl)
done
{% endhighlight %}

Where: `models/out_??.pdb` are your input pdb files.
