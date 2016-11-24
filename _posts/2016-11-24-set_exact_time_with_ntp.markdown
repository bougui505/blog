---
title: "Set exact time with ntp"
layout: default
date: 2016-11-24
tags:
- linux
- debian
- ntp
---

# Set exact time with ntp

## Edit the configuration file to eventually add ntp servers

Edit the file `/etc/ntp.conf` and look at the server list and add eventually a server:

    server 0.europe.pool.ntp.org
    server 1.europe.pool.ntp.org
    server 2.europe.pool.ntp.org
    server 3.europe.pool.ntp.org
    server 0.debian.pool.ntp.org iburst
    server 1.debian.pool.ntp.org iburst
    server 2.debian.pool.ntp.org iburst
    server 3.debian.pool.ntp.org iburst

## Restart the ntp service

    $ sudo /etc/init.d/ntp restart

## Check if the computer is synchronized:

    $ ntpstat
    synchronised to NTP server (XXX.XX.XX.XX) at stratum 3
        time correct to within 137 ms
        polling server every 64 s

## Eventually list the status of each server with:

    $ ntpq -p

## Remark:

You can eventually check the time of your computer on [Time.is](http://time.is/).
