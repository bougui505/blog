---
title: "Get a progress bar for a process in shell with pv -- Pipe Viewer --"
layout: default
date: 2015-10-29
tags:
- pv
- linux
- shell
---

# Get a progress bar for a process in shell with pv -- Pipe Viewer --

## Monitor the progress accordingly to the number of lines in the output file.

In the example below, the target number of line for the output is 330000:

{% highlight bash %}
./get_weights.sh | pv -s 330000 -l > frames_weight.txt
{% endhighlight %}

Sample output:

     103k 0:13:27 [ 128/s ] [=============================>                                                                     ] 31% ETA 0:29:46
