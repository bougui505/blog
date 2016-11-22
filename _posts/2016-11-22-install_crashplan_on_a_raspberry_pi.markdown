---
title: "Install Crashplan on a Raspberry Pi"
layout: default
date: 2016-11-22
tags:
- raspberry-pi
- crashplan
---

# Install Crashplan on a Raspberry Pi

## Install the required packages

    sudo apt-get install oracle-java8-jdk
    sudo apt-get install libjna-java

## Install Crashplan

[Download Crashplan](https://www.crashplan.com/en-us/download/).

Untar the `tgz` file.

And run the installation script, to install Crashplan as root:

    ./install.sh

Crashplan will not work out of the box.

## Patch Crashplan to work on the Pi

Force Crashplan to use the RPi (Raspbian) JRE:

    sudo rm -r /usr/local/crashplan/jre
    sudo ln -s /usr/lib/jvm/jdk-8-oracle-arm32-vfp-hflt /usr/local/crashplan/jre

And change these two files:

    cd /usr/local/crashplan
    sudo rm libjtux.so
    sudo wget http://bougui505.github.io/assets/libjtux.so

    sudo rm libmd5.so
    sudo wget http://bougui505.github.io/assets/libmd5.so

## Start Crashplan

    $ sudo /usr/local/crashplan/bin/CrashPlanEngine start
    $ sudo /usr/local/crashplan/bin/CrashPlanEngine status
    CrashPlan Engine (pid 1891) is running.

## Configure Crashplan remotely using the local Crashplan user interface (UI)

### Definitions:

- The local computer is defined as your desktop computer
- The remote computer is the RPi

See the [Crashplan
support](https://support.code42.com/CrashPlan/4/Configuring/Using_CrashPlan_On_A_Headless_Computer)
for full explanations.

### Copy the token from the Rpi:

The token is located in `/var/lib/crashplan/.ui_info` if Crashplan is installed
as root or in `~/.crashplan/.ui_info` if installed as user.

The format of the `.ui_info` file is:

    PORT,Authentication_Token,IP_Address

Copy the Authentication Token from the RPi and paste it to replace the
Authentication Token in the local `.ui_info` file, after having backup the
local `.ui_info` file.

## Change the port in the local conf file

Just change the port from 4243 to 4200 in the local `.ui_info` file.

## Start port forwarding on the local computer

    ssh -L 4200:localhost:4243 pi@raspberrypi

## And start CrashPlanDesktop on local computer...

NB: This doesn't work anymore...
