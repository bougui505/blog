---
title: "lzma compression in parallel"
layout: default
date: 2016-11-03
tags:
- lzma
- compression
---

# lzma compression in parallel

pxz: parallel LZMA compressor using liblzma

Parallel XZ is a compression utility that takes advantage of running LZMA
compression of different parts of an input file on multiple cores and
processors simultaneously. Its primary goal is to utilize all resources to
speed up compression time with minimal possible influence on compression ratio.

## Installation on Debian

    sudo apt-get install pxz

## Running with tar

    tar -I pxz -cvf archive.tar.xz stuff_to_compress
