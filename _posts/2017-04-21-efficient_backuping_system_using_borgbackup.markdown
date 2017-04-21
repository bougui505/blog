---
title: "Efficient backuping system using Borgbackup"
layout: default
date: 2017-04-21
tags:
- borg
- backup
---

# Efficient backuping system using Borgbackup

[BorgBackup](http://borgbackup.readthedocs.io/en/latest/index.html) (short: Borg) is a deduplicating backup program. Optionally, it supports compression and authenticated encryption.

Below, I present some trick for automatic backup using cron.

First, the main script:

{% gist f9d9d772ea4e065dffcbc204cfd2b042 %}

And the cron line to insert to crontab:

    */15 * * * * ionice -c 3 nice -n 19 sh /home/bougui/bin/borgbackup.sh > /dev/null 2>&1

Bonus: some convenient aliases:

    alias borg-list="borg list --remote-path /home/pi/bin/borg pi@82.231.223.163:/mnt/usb1/mantrisse_backup"

    borg-info () {
        borg info --remote-path /home/pi/bin/borg pi@82.231.223.163:/mnt/usb1/mantrisse_backup::$1
        }
