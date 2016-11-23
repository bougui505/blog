---
title: "Configure NFS server and client"
layout: default
date: 2016-11-23
tags:
- nfs
---

# Configure NFS server and client

## On the server:

### Install the packages

    sudo apt-get install nfs-common nfs-server

### Edit the exports file:

Edit `/etc/exports`:

    /mnt/nfs_share IP_ADDRESS(rw,sync)

Where `IP_ADDRESS` must be replaced by the IP address of the client allowed to connect.
Here, `/mnt/nfs_share` is the disk to share.

If there are multiple clients:

    /mnt/nfs_share IP_ADDRESS_1(rw,sync) IP_ADDRESS_2(rw,sync) ...

Start the `rpcbind` service:

    sudo service rpcbind start

Start the nfs server service:

    sudo service nfs-kernel-server restart

Export the shared file system:

    sudo exportfs

Check the export:

    sudo showmount

## On the client:

### Install the packages

    sudo apt-get install nfs-common

### Check if the client can join the server:

    sudo showmount -e SERVER_IP

where `SERVER_IP` is the IP address of the server.

### Mount the NFS disk:

    sudo mount SERVER_IP:/mnt/nfs_share /mnt/nfs

To mount `/mnt/nfs_share` in the server on `/mnt/nfs` in the client, where,
again, `SERVER_IP` is the IP address of the server.

### Automount with fstab:

Add this line to the `/etc/fstab` file:

    SERVER_IP:/mnt/nfs_share /mnt/nfs nfs rw 0 0

To mount `/mnt/nfs_share` in the server on `/mnt/nfs` in the client.
