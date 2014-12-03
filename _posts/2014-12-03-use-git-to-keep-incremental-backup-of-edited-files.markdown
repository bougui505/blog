---
title: "Use git to keep incremental backup of edited files"
layout: default
category: linux
date: 2014-12-03 22:02:00 CET
tags:
- linux
- git
---

When I edit a file and I'm not sure of my modification, I used to copy the file in a new file called `myfile.ori`.
But it's not convenient to keep multiple backups of the same file.
You can use git for this versioning but it's not convenient to initialize the repository and to add stuff to `.gitignore`, to add the file you want to backup, and to commit with a message...

Below, it's a little shell script to automatize the backup process:

{% gist a572fe58168603fc3fed %}

The usage is very simple.
If you want to backup a file in the current working directory:

{% highlight bash %}
$ git_backup.sh myfile
{% endhighlight %}

And now the file is under git control.
To create a new backup of the same file just execute the command above again.
Easy !
