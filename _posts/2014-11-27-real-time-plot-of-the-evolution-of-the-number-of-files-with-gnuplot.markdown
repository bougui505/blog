---
title: "Real time plot of the evolution of the number of files with gnuplot"
layout: default
category: linux
date: 2014-11-27 15:18:30 CET
tags:
- linux
- gnuplot
---

# Real time plot of the evolution of the number of files with gnuplot

Usage example to monitor the number of files `dms/smap_*_no_H.dms`

{% highlight bash %}
$ ./file_monitor.sh dms/smap_\*_no_H.dms
{% endhighlight %}

## `file_monitor.sh`

{% highlight bash %}
#!/bin/bash
# -*- coding: UTF8 -*-
infile="$1"
outfile=/dev/shm/nfiles.txt
t_0=$(date +"%s")
for i in $(seq 1 10)
do
t=$(date +"%s")
delta_t=$(($t-$t_0))
nfiles=$(echo $infile | wc -w)
echo $delta_t $nfiles >> $outfile
sleep 2
done
gnuplot loop.plt &
echo "$infile"
while true
    do
        t=$(date +"%s")
        delta_t=$(($t-$t_0))
        nfiles=$(echo $infile | wc -w)
        echo $delta_t $nfiles >> $outfile
        trap "echo Exited!; break" SIGINT
        sleep 2
    done
/bin/rm $outfile
{% endhighlight %}

## `loop.plt`

{% highlight bash %}
set grid
set xlabel "running time (s)"
#fitline(x) = a*x + b
#fit fitline(x) '/dev/shm/nfiles.txt' using 1:2 via a, b
plot '/dev/shm/nfiles.txt' using 1:2 with linespoints#, fitline(x)
pause 2
replot
reread
{% endhighlight %}
