---
title: "Run pymol interactively from IPython notebook"
layout: default
date: 2017-04-06
tags:
- pymol
- python
- ipython
---

# Run pymol interactively from IPython notebook

{% highlight python %}
import sys
import __main__
#__main__.pymol_argv = ['pymol', '-c'] # Optionnaly pass options to pymol
import pymol
stdout = sys.stdout # To get the stdout in the notebook instead of in the pymol console
import pymol.cmd as cmd
pymol.finish_launching()
sys.stdout = stdout
{% endhighlight %}

Example usage:

{% highlight python %}
cmd.bg_color('white')
cmd.load('4ci0_A.pdb', object='native')
cmd.show_as('ribbon', 'native')
cmd.util.cbc() # Color By Chain
cmd.orient()
{% endhighlight %}
