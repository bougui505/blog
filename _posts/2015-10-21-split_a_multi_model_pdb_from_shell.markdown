---
title: "Split a multi model pdb from shell"
layout: default
date: 2015-10-21
tags:
- shell
- linux
- bash
- awk
- zsh
- csplit
---

# Split a multi model pdb from shell

{% highlight bash %}
awk '$0 ~ /ATOM      1/ {i++} {print >> "pdbs/out_"i".pdb"} {fflush("pdbs/out_"i".pdb")}' filename.pdb
{% endhighlight %}

It's possible to use the csplit command too. In the example below, I've a pdb file containing 50000 models delimited by `MODEL X` and `ENDMDL`:

{% highlight bash %}
csplit -z -f /dev/shm/docking_ -n 5 docking_results.pdb '/ENDMDL/1' '{49999}'
{% endhighlight %}

`-n`: number of digits

`-z`: remove empty output files

In the previous example the output files are named (in the `/dev/shm/` directory):

    docking_00000
    docking_00001
    ...
    docking_49999

If you want to add a suffix (for example `.pdb`) you have to specify the format:

{% highlight bash %}
csplit -z -f /dev/shm/docking_ -b '%05d.pdb' docking_results.pdb '/ENDMDL/1' '{49999}'
{% endhighlight %}

Below is the final function:

{% highlight bash %}
function splitpdb () {
    n_models=$(grep -c MODEL $1)
    csplit -z -f /dev/shm/model_ -b '%04d.pdb' $1 '/ENDMDL/1' "{$(expr $n_models - 1)}"
}
{% endhighlight %}

- If you want 100 structures per output file

{% highlight bash %}
awk '$0 ~ /ATOM 1/ {i++} {print >> "pdbs/smap_"int(i/100)".pdb"} {fflush("pdbs/smap_"int(i/100)".pdb")}' smap.pdb
{% endhighlight %}

