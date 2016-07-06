---
title: "Making a bluetooth speaker working with Debian 8.5"
layout: default
date: 2016-07-06
tags:
- bluetooth
- pulseaudio
---

# Making a bluetooth speaker working with Debian 8.5

This solution works for me with the Bose SoundLink Mini.

## Install the required packages:

    sudo apt-get install pulseaudio pulseaudio-module-bluetooth pavucontrol bluez-firmware pulseaudio-module-gconf

## Edit and check /etc/pulse/default.pa

Be sure that the lines below are present in `/etc/pulse/default.pa`:

    .ifexists module-bluetooth-discover.so
    load-module module-bluetooth-discover
    .endif

And add the line below (or check if presents):

    load-module module-switch-on-connect

Then restart the computer and it should work!
