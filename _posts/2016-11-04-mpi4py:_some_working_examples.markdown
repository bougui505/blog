---
title: "mpi4py: some working examples"
layout: default
date: 2016-11-04
tags:
- mpi
- mpi4py
- python
---

# mpi4py: some working examples

## Original imports:

{% highlight python %}
from mpi4py import MPI
COMM = MPI.COMM_WORLD
SIZE = COMM.Get_size() # Number of CPUS
RANK = COMM.Get_rank()
{% endhighlight %}

## Broadcasting data between nodes:

{% highlight python %}
if RANK == 0:
    a = 2
else:
    a = None
a = COMM.bcast(a, root=0)
{% endhighlight %}

## Scattering jobs to nodes

To scatter jobs to nodes when the number of jobs is not equal to the number of
process:

{% gist c67232497207a2ff16edc0775fc3c228 %}

Example output:

    bougui@mantrisse /d/shm>  mpirun -np 2 ./scatter_jobs_mpi.py
    Job array:
    [[0 1]
     [2 None]]
    rank 0: job 0
    rank 1: job 1
    rank 0: job 2
    {0: 0, 1: 1, 2: 4}
