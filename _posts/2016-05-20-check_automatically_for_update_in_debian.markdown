---
title: "Check automatically for update in Debian"
layout: default
date: 2016-05-20
tags:
- debian
- linux
---

# Check automatically for update in Debian

The package `cron-apt` is designed to automatically update the package list and
download upgraded packages. Therefore it basically calls the command
[[1]][cron-apt]:

    apt-get update

To install `cron-apt`:

    sudo apt-get install cron-apt

By default, `cron-apt` uses `cron` to run regularly (each day at 4am). This
method is not convenient for a personal desktop computer which is often turned
off at that time.

You can use `anacron` instead of cron to execute `cron-apt` regularly. For
doing this, just link the executable in the `/etc/cron.daily/` directory:

    sudo ln -s /usr/sbin/cron-apt /etc/cron.d/

However `anacron` is automatically launched each day at 7:30 am by `cron`. The
command that launch `anacron` by `cron` is found in this file:
`/etc/cron.d/anacron`. Once again, this could be not optimal for a desktop
computer. Furthermore when you start your laptop without power supply anacron
won't be launched. You can then add another, more convenient, entry in the
`/etc/cron.d/anacron` file to launch `anacron` at 12:30 pm for example. The
full `/etc/cron.d/anacron` file then looks like:

    # /etc/cron.d/anacron: crontab entries for the anacron package

    SHELL=/bin/sh
    PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

    30 7    * * *   root    test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null
    30 12    * * *   root   test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null


I always use the command line, then it can be very convenient to display a
message with the number of updates available for my system when I log in to my
favourite shell. To do so I added this line to the anacrontab
(`/etc/anacrontab`):

    1   10  check_update echo "$(date +'%Y%m%d %T') $(aptitude search '~U' | wc -l) packages can be updated." > /home/USER/.motd # message of the day

And I use the following script to print the message of the day when I start a
new shell:

{% gist 1aa8d4d97c913e15cfc50a291b3d1753 %}

Then I added the following command to my shell configuration script (`.bashrc`,
`.zshrc`, ...):

    ~/PATH/TO/THE/SCRIPT/print_motd.sh # Message of the day

[cron-apt]: https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo
