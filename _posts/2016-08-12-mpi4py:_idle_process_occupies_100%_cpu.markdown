---
title: "mpi4py: Idle process occupies 100% CPU"
layout: default
date: 2016-08-12
tags:
- python
- mpi
---

# mpi4py: Idle process occupies 100

When only one node is computing, the IDLE process occupies 100% of the CPU. A
workaround is to replace `COMM.barrier()` by this function:

{% gist 23c57990f3ebe671bb88e15211c533fc %}

Example usage:

{% highlight python %}
import time
comm = MPI.COMM_WORLD
tic = MPI.Wtime()
if comm.rank==0:
    time.sleep(10)
barrier(comm) # Instead of comm.barrier()
toc = MPI.Wtime()
print comm.rank, toc-tic
{% endhighlight %}
