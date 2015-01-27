---
title: "Geodesic distance transform in python"
layout: default
category: python
date: 2015-01-26 17:06:11 CEST
tags:
- python
---
# Geodesic distance transform in python


{% highlight python %}
%pylab inline
from scipy.ndimage.morphology import distance_transform_edt

{% endhighlight %}

Below, I used the Euclidean distance transform implemented in python. This
function doesn't take into account the topology of the surface represented by
the mask


{% highlight python %}
l = 100
x, y = np.indices((l, l))
center1 = (50, 20)
center2 = (28, 24)
center3 = (30, 50)
center4 = (60,48)
radius1, radius2, radius3, radius4 = 15, 12, 19, 12
circle1 = (x - center1[0])**2 + (y - center1[1])**2 < radius1**2
circle2 = (x - center2[0])**2 + (y - center2[1])**2 < radius2**2
circle3 = (x - center3[0])**2 + (y - center3[1])**2 < radius3**2
circle4 = (x - center4[0])**2 + (y - center4[1])**2 < radius4**2
# 3 circles
img = circle1 + circle2 + circle3 + circle4
mask = ~img.astype(bool)
img = img.astype(float)
m = ones_like(img)
m[center1] = 0
#imshow(distance_transform_edt(m), interpolation='nearest')
m = ma.masked_array(distance_transform_edt(m), mask)
imshow(m, interpolation='nearest')

{% endhighlight %}

![png](/assets/geodesic_distance_transform_files/geodesic_distance_transform_2_1.png)

I implemented the Dijkstra algorithm to apply a geodesic distance transform to
the shape above:

{% highlight python %}
def geodesic_distance_transform(m):
    mask = m.mask
    visit_mask = mask.copy() # mask visited cells
    m = m.filled(numpy.inf)
    m[m!=0] = numpy.inf
    distance_increments = numpy.asarray([sqrt(2), 1., sqrt(2), 1., 1., sqrt(2), 1., sqrt(2)])
    
    cc = unravel_index(m.argmin(), m.shape) # current_cell
    while (~visit_mask).sum() > 0:
        neighbors = [tuple(cc - asarray([i,j])) for i in [-1, 0, 1] for j in [-1, 0, 1] if (not (i == j == 0))]
        current_mask = asarray([~visit_mask[e] for e in neighbors])
        neighbors = numpy.asarray([e for e in neighbors])[current_mask]
        neighbors = [tuple(e) for e in neighbors]
        #if len(neighbors) == 0:
            #break
        tentative_distance = distance_increments[current_mask]
        for i,e in enumerate(neighbors):
            d = tentative_distance[i] + m[cc]
            if d < m[e]:
                m[e] = d
        visit_mask[cc] = True
        m_mask = ma.masked_array(m, visit_mask)
        cc = unravel_index(m_mask.argmin(), m.shape)
    return m

{% endhighlight %}

{% highlight python %}
gdt = geodesic_distance_transform(m)
{% endhighlight %}



{% highlight python %}
imshow(gdt, interpolation='nearest')
colorbar()

{% endhighlight %}

![png](/assets/geodesic_distance_transform_files/geodesic_distance_transform_6_1.png)

If someone have a faster implementation in python, I'm interested in!
