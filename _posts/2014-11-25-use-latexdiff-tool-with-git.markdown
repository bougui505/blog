---
title: "Use latexdiff tool with git"
layout: default
category: git
date: 2014-11-25 09:41:11 CET
tags:
- git
- LaTeX
---

# Use latexdiff tool with git

What is `latexdiff` ?
Below the description of the debian package:

> Package: latexdiff
> 
> Version: 0.5-4
> 
> Maintainer: Debian Perl Group <pkg-perl-maintainers@lists.alioth.debian.org>
> 
> Architecture: all
> 
> Depends: perl
> 
> Recommends: texlive-latex-base, texlive-latex-extra
> 
> Suggests: subversion | cvs | rcs
> 
> Description-en: utility to mark up significant differences between LaTeX files
> latexdiff compares two LaTeX files and marks up significant differences
> between them (i.e. a diff for LaTeX files). It generates a new LaTeX file
> containing the annotated differences.
> 
> Various options are available for visual markup using standard LaTeX packages
> such as 'color.sty'. Changes not directly affecting visible text, for example
> in formatting commands, are still marked in the LaTeX source.
> 
> A rudimentary revision facilility is provided by another Perl script,
> 'latexrevise', which accepts or rejects all changes. Manual editing of the
> difference file can be used to override this default behaviour and accept or
> reject selected changes only.
> 
> Homepage: http://bullard.esc.cam.ac.uk/~tilmann/soft.html

First install `latexdiff`

{% highlight bash %}
$ sudo apt-get install latexdiff
{% endhighlight %}

To use it with git, just add this line to your `~/.gitconfig`:

    [difftool.latexdiff]
        cmd = latexdiff "$LOCAL" "$REMOTE"

For example to generate a diff file `diff.tex` between the current version of the file `document.tex` and the commit `83533d8` just type:

{% highlight bash %}
$ git difftool -t latexdiff 83533d8 -- document.tex > diff.tex
{% endhighlight %}

And now you can compile the `diff.tex` to highlight the difference easily.
