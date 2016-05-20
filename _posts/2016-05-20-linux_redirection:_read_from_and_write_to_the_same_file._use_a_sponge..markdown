---
title: "Linux redirection: read from and write to the same file. Use a sponge!"
layout: default
date: 2016-05-20
tags:
- linux
- shell
---

# Linux redirection: read from and write to the same file. Use a sponge!

From the man page:

sponge  reads standard input and writes it out to the specified file. Unlike a
shell redirect, sponge soaks up all its input before opening the output  file.
This allows constructing pipelines that read from and write to the same file.

It also creates the output file atomically by renaming a temp file into place,
and preserves the permissions of the output file if it already exists.  If the
output file is a special file or symlink, the data will be written to it.

If no output file is specified, sponge outputs to stdout.

For example:
    sed '...' file | grep '...' | sponge file

That's it!
