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
# Tell PyMOL we don't want any GUI features.
import __main__
__main__.pymol_argv = [ 'pymol', '-qi' ]
# Importing the PyMOL module will create the window.
import pymol
import pymol.cmd as cmd
# Call the function below before using any PyMOL modules.
pymol.finish_launching()
{% endhighlight %}

Example usage:

{% highlight python %}
cmd.bg_color('white')
cmd.load('4ci0_A.pdb', object='native')
cmd.show_as('ribbon', 'native')
cmd.util.cbc() # Color By Chain
cmd.orient()
{% endhighlight %}
