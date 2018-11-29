---
title: "Automatic reconnection with sshfs"
layout: default
date: 2018-11-29
tags:
- ssh
- sshfs
---

# Automatic reconnection with sshfs

    sshfs -o reconnect,ServerAliveInterval=15,ServerAliveCountMax=3 host:/path/to/mount /path/to/mntpoint
