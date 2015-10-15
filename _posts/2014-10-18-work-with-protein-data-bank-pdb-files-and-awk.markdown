---
title: "Work with protein data bank (pdb) files and awk"
layout: default
category: awk
date: 2014-10-18 21:39:47 CEST
tags:
- awk
- pdb
- csplit
---

# Work with protein data bank (pdb) files and awk

## Format a pdb with awk for fields: [ATOM] [Atom  serial number] [Atom name] [Residue name] [Chain identifier] [Residue sequence number] [x] [y] [z]

{% highlight bash %}
awk '{if ($1=="ATOM") printf("%-6s%5s %4s %3s %s%4s    %8s%8s%8s\n", $1,$2,$3,$4,$5,$6,$7,$8,$9); else print $0}' filename.pdb
{% endhighlight %}


## Split a pdb:

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

- If you want 100 structures per output file

{% highlight bash %}
awk '$0 ~ /ATOM 1/ {i++} {print >> "pdbs/smap_"int(i/100)".pdb"} {fflush("pdbs/smap_"int(i/100)".pdb")}' smap.pdb
{% endhighlight %}

## Add MODEL \# for multiple models pdb files

{% highlight bash %}
function mspdb () {
    grep -v 'CRYST1' $1 | awk '{if ($2==1){c+=1;print "MODEL "c}{print $0}}' | sed 's/END/ENDMDL/' > /dev/shm/tmp.pdb && mv -f /dev/shm/tmp.pdb $1
    }
{% endhighlight %}

## Compute the geometric center from a `pdb` file

{% highlight bash %}
awk '{if ($1 == "ATOM") {sx+=$6;sy+=$7;sz+=$8;n+=1}} END {print sx/n,sy/n,sz/n}' model1.pdb
{% endhighlight %}

Just adapt the column numbers for `x`, `y` and `z` depending of the presence of a chain id.

## Strip hydrogens from a `pdb` file

{% highlight bash %}
function stripH () {
    awk '{if ($1=="ATOM" && $3 !~ /H/) {c+=1; printf("%-6s%5s %4s %3s %s%4s    %8s%8s%8s\n", $1,c,$3,$4,$5,$6,$7,$8,$9)} \
    else if ($1=="MODEL" || $1=="ENDMDL") {c=0; print $0}}' $1 > /dev/shm/tmp.pdb && mv /dev/shm/tmp.pdb $1
}
{% endhighlight %}
