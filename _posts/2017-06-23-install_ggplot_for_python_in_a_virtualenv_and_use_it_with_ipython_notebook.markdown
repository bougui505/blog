---
title: "Install ggplot for python in a virtualenv and use it with ipython notebook"
layout: default
date: 2017-06-23
tags:
- python
- ggplot
---

# Install ggplot for python in a virtualenv and use it with ipython notebook

## Create the virtual environment:

    virtualenv --system-site-packages ggplot

## Activate the virtual environment:

    source ggplot/bin/activate

## Install ggplot in the virtual environment:

    pip install -U ggplot

## Install the ipykernel for the virtual environment:

    pip install ipykernel

## Run the kernel "self-install" script:

    python -m ipykernel install --user --name=ggplot

You should now be able to see your kernel in the IPython notebook menu: Kernel -> Change kernel and be able so switch to it (you may need to refresh the page before it appears in the list). IPython will remember which kernel to use for that notebook from then on.
