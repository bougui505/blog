---
title: "Syntax highlighting with pygments in the shell"
layout: default
category: linux
date: 2014-11-19 07:53:21 CET
tags:
- linux
---

# Syntax highlighting with pygments in the shell

First install Pygments:

{% highlight bash %}
$ apt-get install python-pygments
{% endhighlight %}

And create this function in your `.zshrc` or `.bashrc`:

{% highlight bash %}
colorize_via_pygmentize () {
    if [ ! -x $(which pygmentize) ]
    then
        echo package \'pygmentize\' is not installed!
        exit -1
    fi
    if [ $# -eq 0 ]
    then
        pygmentize -g $@
    fi
    for FNAME in $@
    do
        filename=$(basename "$FNAME") 
        lexer=`pygmentize -N \"$filename\"` 
        if [ "Z$lexer" != "Ztext" ]
        then
            pygmentize -l $lexer "$FNAME"
        else
            pygmentize -g "$FNAME"
        fi
    done
}
{% endhighlight %}

If you want a colorize display for less, you can add this function:

{% highlight bash %}
cless () {
    colorize_via_pygmentize $1 | less
}
{% endhighlight %}

Now, you should have syntax highlighting if you use:

{% highlight bash %}
$ cless yourfilename
{% endhighlight %}
