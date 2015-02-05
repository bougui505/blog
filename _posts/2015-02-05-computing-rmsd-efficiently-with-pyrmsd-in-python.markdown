---
title: "Computing RMSD efficiently with pyRMSD in python"
layout: default
category: python
date: 2015-02-05 16:47:12 CET
tags:
- python
- science
---

# Computing RMSD efficiently with pyRMSD in python

From the [pyRMSD github page](https://github.com/victor-gil-sepulveda/pyRMSD):

> pyRMSD is a small Python package that aims to offer an integrative and
> efficient way of performing RMSD calculations of large sets of structures. It
> is specially tuned to do fast collective RMSD calculations, as pairwise RMSD
> matrices. 

A small tutorial for using it:

{% highlight python %}
import pyRMSD.RMSDCalculator
{% endhighlight %}

The trajectory is given as a numpy array.
The first dimension gives the frames, the second the atoms and the third the $$x$$, $$y$$, $$z$$ coordinates.

{% highlight python %}
fittingCoordsets = traj.copy().reshape(50001,341,3) # the numpy array containing the trajectory
                                                    # for this exemple: 50001 frames, 341 atoms
{% endhighlight %}

And now we can compute the RMSD between the first frame `0` and the following ones with optimal alignment:

{% highlight python %}
calculator = pyRMSD.RMSDCalculator.RMSDCalculator('QCP_OMP_CALCULATOR', fittingCoordsets)
out = calculator.oneVsTheOthers(0)
{% endhighlight %}
