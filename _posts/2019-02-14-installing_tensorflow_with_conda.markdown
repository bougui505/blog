---
title: "Installing tensorflow with conda"
layout: default
date: 2019-02-14
tags:
- python
- tensorflow
---

# Installing tensorflow with conda

## Install miniconda2 (if required):

Download [miniconda2](https://conda.io/en/latest/miniconda.html)
and install it:
    bash Miniconda2-latest-Linux-x86_64.sh

## Create a conda environment:

    conda create --name tensorflow-gpu python=2.7

## Activate the created environment:

    cd miniconda2/bin
    source activate ../envs/tensorflow-gpu

## Install tensorflow:

    conda install tensorflow-gpu
