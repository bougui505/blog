---
title: "Configure Freedns (afraid.org) service with Inadyn"
layout: default
category: linux
date: 2014-11-09 22:40:16 CET
tags:
- linux
---

# Configure Freedns (afraid.org) service with Inadyn

First install inadyn:
    
    sudo apt-get install inadyn

And then open [http://freedns.afraid.org/dynamic](http://freedns.afraid.org/dynamic) and copy the alphanumeric string just after '?' in the link 'Direct URL' of your corresponding domain.

Then create the inadyn configuration file `/etc/inadyn.conf` with this content:

    --username <your_username>
    --password <your_password>
    --update_period 60000
    --alias <your_host>.<your domain>,<alphanumeric string>
    --background
    --dyndns_system default@freedns.afraid.org
    --syslog

and replace `<your_host>.<your domain>,<alphanumeric string>` with the corresponding informations.

Now try to run inadyn:

    /usr/sbin/inadyn

and if it works, launch inadyn at boot with the root crontab:

    $ sudo crontab -e

and add the following line to crontab:

    @reboot /usr/sbin/inadyn
