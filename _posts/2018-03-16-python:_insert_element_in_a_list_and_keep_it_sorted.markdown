---
title: "Python: Insert element in a list and keep it sorted"
layout: default
date: 2018-03-16
tags:
- python
---

# Python: Insert element in a list and keep it sorted

{% highlight python %}
import bisect
l = []
for i in range(10):
    r = random.randint(1, 100)
    bisect.insort(l, r)
    print i, r, l
{% endhighlight %}

Output:

    0 48 [48]
    1 51 [48, 51]
    2 28 [28, 48, 51]
    3 42 [28, 42, 48, 51]
    4 72 [28, 42, 48, 51, 72]
    5 47 [28, 42, 47, 48, 51, 72]
    6 82 [28, 42, 47, 48, 51, 72, 82]
    7 58 [28, 42, 47, 48, 51, 58, 72, 82]
    8 8 [8, 28, 42, 47, 48, 51, 58, 72, 82]
    9 31 [8, 28, 31, 42, 47, 48, 51, 58, 72, 82]

