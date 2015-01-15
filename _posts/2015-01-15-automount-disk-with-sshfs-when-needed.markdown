---
title: "Automount disk with sshfs when needed, with autofs"
layout: default
category: linux
date: 2015-01-15 21:43:27 CET
tags:
- linux
---

# Automount disk with sshfs when needed, with autofs

From the [ubuntu documentation](https://help.ubuntu.com/community/Autofs)

> `autofs` is a program for automatically mounting directories on an as-needed basis.
> Auto-mounts are mounted only as they are accessed, and are unmounted after a period of inactivity.
> Because of this, automounting NFS/Samba shares conserves bandwidth and offers better overall performance compared to static mounts via fstab.

## Install the `autofs` package

In Debian:

    sudo apt-get install autofs

And edit the file `/etc/auto.master` by adding this line:

    /mnt/sshfs /etc/auto.sshfs uid=1000,gid=1000,--timeout=30,--ghost

Replace the uid and gid by your user-id and group-id respectively.
`--timeout=30` is to unmount the disk when you didn't use it for 30 seconds.

Create the file `/etc/auto.sshfs` with this content:

    mydisk -fstype=fuse,port=22,rw,allow_other :sshfs\#username@host\:/path/to/your/disk/to/mount/

- `mydisk` is the name of the local directory created
- `username` is the distant username
- `host` is the distant host
- `/path/to/your/disk/to/mount/` is the path to the directory to mount

Then, reload autofs:

    sudo /etc/init.d/autofs restart

When you will access to `/mnt/sshfs/mydisk` the disk will be automatically mount.
The ssh keys must be properly!
