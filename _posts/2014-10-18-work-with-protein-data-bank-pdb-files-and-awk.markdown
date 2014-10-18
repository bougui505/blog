---
title: "Work with protein data bank (pdb) files and awk"
layout: default
category: awk
date: 2014-10-18 21:39:47 CEST
---

- Format a pdb with awk for fields: [ATOM] [Atom  serial number] [Atom name] [Residue name] [Chain identifier] [Residue sequence number] [x] [y] [z]

{% highlight bash %}
awk '{if ($1=="ATOM") printf("%-6s%5s %4s %3s %s%4s    %8s%8s%8s\n", $1,$2,$3,$4,$5,$6,$7,$8,$9); else print $0}' filename.pdb
{% endhighlight %}


- Split a pdb:

{% highlight bash %}
awk '$0 ~ /ATOM      1/ {i++} {print >> "pdbs/out_"i".pdb"} {fflush("pdbs/out_"i".pdb")}' filename.pdb
{% endhighlight %}
