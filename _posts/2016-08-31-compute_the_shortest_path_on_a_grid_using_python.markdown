---
title: "Compute the shortest path on a grid using python"
layout: default
date: 2016-08-31
tags:
- python
- science
---

# Compute the shortest path on a grid using python

I have defined the following 3D surface on a grid:

{% highlight python %}
%pylab inline
{% endhighlight %}

{% highlight python %}
def muller_potential(x, y, use_numpy=False):
    """Muller potential
    Parameters
    ----------
    x : {float, np.ndarray, or theano symbolic variable}
    X coordinate. If you supply an array, x and y need to be the same shape,
    and the potential will be calculated at each (x,y pair)
    y : {float, np.ndarray, or theano symbolic variable}
    Y coordinate. If you supply an array, x and y need to be the same shape,
    and the potential will be calculated at each (x,y pair)
    Returns
    -------
    potential : {float, np.ndarray, or theano symbolic variable}
    Potential energy. Will be the same shape as the inputs, x and y.
    Reference
    ---------
    Code adapted from https://cims.nyu.edu/~eve2/ztsMueller.m
    """
    aa = [-1, -1, -6.5, 0.7]
    bb = [0, 0, 11, 0.6]
    cc = [-10, -10, -6.5, 0.7]
    AA = [-200, -100, -170, 15]
    XX = [1, 0, -0.5, -1]
    YY = [0, 0.5, 1.5, 1]
    # use symbolic algebra if you supply symbolic quantities
    exp = np.exp
    value = 0
    for j in range(0, 4):
        if use_numpy:
            value += AA[j] * numpy.exp(aa[j] * (x - XX[j])**2 + bb[j] * (x - XX[j]) * (y - YY[j]) + cc[j] * (y - YY[j])**2)
        else: # use sympy
            value += AA[j] * sympy.exp(aa[j] * (x - XX[j])**2 + bb[j] * (x - XX[j]) * (y - YY[j]) + cc[j] * (y - YY[j])**2)
    return value
{% endhighlight %}

Which gave the following plot:

{% highlight python %}
minx=-1.5
maxx=1.2
miny=-0.2
maxy=2
ax=None
grid_width = max(maxx-minx, maxy-miny) / 50.0
xx, yy = np.mgrid[minx : maxx : grid_width, miny : maxy : grid_width]
V = muller_potential(xx, yy, use_numpy=True)
V = ma.masked_array(V, V>200)
contourf(V, 40)
tmp = colorbar()
{% endhighlight %}


![png](/assets/shortest_path_files/shortest_path_2_1.png)

I wrote the following code to define the shortest path between two points on
that grid. The metric I used between two adjacent points of the meshgrid is
given by `(V[e]-V[cc])**2` with cc the current cell and e one of the neighboring
cells. The neighbors are defined with a full connectivity: all direct neighbors
with diagonal included.

{% highlight python %}
def dijkstra(V):
    mask = V.mask
    visit_mask = mask.copy() # mask visited cells
    m = numpy.ones_like(V) * numpy.inf
    connectivity = [(i,j) for i in [-1, 0, 1] for j in [-1, 0, 1] if (not (i == j == 0))]
    cc = unravel_index(V.argmin(), m.shape) # current_cell
    m[cc] = 0
    P = {}  # dictionary of predecessors 
    #while (~visit_mask).sum() > 0:
    for _ in range(V.size):
        #print cc
        neighbors = [tuple(e) for e in asarray(cc) - connectivity 
                     if e[0] > 0 and e[1] > 0 and e[0] < V.shape[0] and e[1] < V.shape[1]]
        neighbors = [ e for e in neighbors if not visit_mask[e] ]
        tentative_distance = [(V[e]-V[cc])**2 for e in neighbors]
        for i,e in enumerate(neighbors):
            d = tentative_distance[i] + m[cc]
            if d < m[e]:
                m[e] = d
                P[e] = cc
        visit_mask[cc] = True
        m_mask = ma.masked_array(m, visit_mask)
        cc = unravel_index(m_mask.argmin(), m.shape)
    return m, P

{% endhighlight %}


{% highlight python %}
D, P = dijkstra(V)
{% endhighlight %}

{% highlight python %}
def shortestPath(start, end, P):
    Path = []
    step = end
    while 1:
        Path.append(step)
        if step == start: break
        step = P[step]
    Path.reverse()
    return asarray(Path)
{% endhighlight %}

Which gave the following result:

{% highlight python %}
path = shortestPath(unravel_index(V.argmin(), V.shape), (40,4), P)
{% endhighlight %}

{% highlight python %}
contourf(V, 40)
plot(path[:,1], path[:,0], 'r.-')
{% endhighlight %}

![png](/assets/shortest_path_files/shortest_path_7_1.png)

