---
title: "Simple alignment of two proteins using PCA"
layout: default
date: 2017-06-26
tags:
- python
- pdb
---

# Simple alignment of two proteins using PCA

Below are the functions:

{% highlight python %}
def center(coords):
    return coords - coords.mean(axis=0)

def align(coords, target):
    targar = center(target)
    tempar = center(coords)
    tarw, tarV = numpy.linalg.eigh(targar.T.dot(targar))
    tempw, tempV = numpy.linalg.eigh(tempar.T.dot(tempar))
    V,s,tW=numpy.linalg.svd(numpy.dot(tarV,tempV.T))
    #  change sign of the last vector if needed to assure similar orientation of bases
    if numpy.linalg.det(V)*numpy.linalg.det(tW) < 0:
        V[:,2]*=-1
    rot=numpy.dot(V,tW)
    #print rot.shape
    targrot=numpy.dot(targar,rot)
    return targrot + target.mean(axis=0)
{% endhighlight %}

`coords` and `target` must be n by 3 numpy arrays.
