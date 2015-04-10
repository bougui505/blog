---
title: "bundledoc: bundle together all files needed to compile your LaTeX document"
layout: default
category: LaTeX
date: 2015-04-10 16:23:05 CEST
tags:
- LaTeX
---

# bundledoc: bundle together all files needed to compile your LaTeX document

> The bundledoc package is a post-processor for the snapshot package that
> bundles together all the classes, packages and files needed to build a given
> LaTeX document. It reads the .dep file that snapshot produces, finds each of
> the files mentioned therein, and archives them into a single .tar.gz (or
> .zip, or whatever) file, suitable for moving across systems, transmitting to
> a colleague, etc.

## Usage:

- put `\RequirePackage{snapshot}` before `\documentclass` in your `.tex` file and run latex or pdflatex on it.

- run bundledoc on generated `.dep` file.

## Configuration file:

Below is the content of my configuration file `~/.bundledoc.cfg`:

    bundle: (tar -czvf $BDBASE.tar.gz $BDINPUTS)
    sink:   > /dev/null 2>&1
    find:   kpsewhich -progname=latex $BDINPUTS
