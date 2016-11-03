---
title: "Creating and using squashed file systems"
layout: default
date: 2016-11-03
tags:
- squashfs
---

# Creating and using squashed file systems

SquashFS is a read-only compressed file system.

From [the original documentation](http://www.tldp.org/HOWTO/html_single/SquashFS-HOWTO/#whatis)

SquashFS is a read-only file system that lets you compress whole file systems
or single directories, write them to other devices/partitions or to ordinary
files, and then mount them directly (if a device) or using a loopback device
(if it is a file). The modular, compact system design of SquashFS is bliss. For
archiving purposes, **SquashFS gives you a lot more flexibility and performance
speed than a tarball archive**.

## In order to create a squashed file system out of a single directory (say, /some/dir), and output it to a regular file (thus, producing a file system image), you need to say only one magic phrase:

    mksquashfs /some/dir dir.sqsh

## You can now use the mount command to mount it using a loopback device:

    sudo mkdir /mnt/squashfs
    sudo mount dir.sqsh /mnt/squashfs -t squashfs -o loop

## Unmounting the squashfs:

    sudo umount /mnt/squashfs

[Original and complete howto here](http://tldp.org/HOWTO/SquashFS-HOWTO/creatingandusing.html)
