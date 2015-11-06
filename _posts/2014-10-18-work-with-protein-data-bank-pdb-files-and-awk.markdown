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

The `mktemp -p /dev/shm` function ensure that a unique temporary file name is
created. This feature is important to run this function in parallel on multiple
files.

A word of caution: this function overwrite the input file. Just change the `mv
$tmpfile $1` to `mv $tmpfile newfilename.pdb` to avoid this feature.

{% highlight bash %}
function stripH () {
    tmpfile=$(mktemp -p /dev/shm)
    awk '{if ($1=="ATOM" && $3 !~ /H/) {c+=1; printf("%-6s%5s %4s %3s %s%4s    %8s%8s%8s\n", $1,c,$3,$4,$5,$6,$7,$8,$9)} \
    else if ($1=="MODEL" || $1=="ENDMDL") {c=0; print $0}}' $1 > $tmpfile && mv $tmpfile $1
}
{% endhighlight %}
