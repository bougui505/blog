---
title: "Use Jekyll with BibTeX"
layout: default
category: jekyll
date: 2014-10-20 09:56:31 CEST
tags:
- jekyll
- LaTeX
---

# Use Jekyll with BibTeX

First install jekyll-scholar:
{% highlight bash %}
gem install --no-rdoc --no-ri --user-install jekyll-scholar
{% endhighlight %}
It takes a long time (several minutes) on the raspberry pi.

Then creates the file `_plugins/ext.rb` or add the following line to the file `_plugins/ext.rb` if its already exists:
{% highlight ruby %}
jekyll inline code
{% endhighlight %}

Then create the directory `_bibliography`:
{% highlight bash %}
mkdir _bibliography
{% endhighlight %}

In this directory put your bib file under the name `references.bib`.

In the root directory of the jekyll web site create the file `bibliography.md`:

    ---
    layout: default
    title: Bibliography
    ---

    # Bibliography

    {{ "{% bibliography " }}%}

That's all.
With the default jekyll theme a link to the generated bibliography page should appear in the top navigation bar of the generated web site (`jekyll build`).

If you want to sort the bibliography by year you can add this in the `_config.yml`

    scholar:
        sort_by: year
        order: descending
