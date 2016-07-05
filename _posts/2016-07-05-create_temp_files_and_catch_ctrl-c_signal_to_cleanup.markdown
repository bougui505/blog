---
title: "Create temp files and catch ctrl-C signal to cleanup"
layout: default
date: 2016-07-05
tags:
- linux
- shell
---

# Create temp files and catch ctrl-C signal to cleanup

Sometimes temporary files are required, but it's important to cleanup when the
script is over even when `ctrl-c` is pressed to abort the running script. Below
is the sequence for creating temp files with `mktemp` and cleaning them up when
`ctrl-c` is pressed:

    # Decompress the log files in a tmp file:
    TMPFILE=$(mktemp -p /dev/shm)
    zcat -f $LOGFILE > $TMPFILE

    # cleanup function
    # see: http://goo.gl/2aUQc
    trap "rm $TMPFILE; exit" SIGHUP SIGINT SIGTERM

The example above, decompress some log files in a temp file located in ram disk
`/dev/shm`.
