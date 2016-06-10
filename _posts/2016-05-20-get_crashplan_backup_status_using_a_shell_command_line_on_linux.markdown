---
title: "Get CrashPlan backup status using a shell command line on Linux"
layout: default
date: 2016-05-20
tags:
- linux
- crashplan
---

# Get CrashPlan backup status using a shell command line on Linux

I use [Crashplan](http://www.code42.com/crashplan/) to backup my file on Linux.
The backup system works well, however there is no shell commands to obtain
informations about files status -- are they backuped or not and when the last
backup has been done?

I wrote this little script to obtain such informations from the log file
(`$HOME/crashplan/log/backup_files.log.0`) -- change the path if you don't
install CrashPlan in the same location -- and print them out in a formatted
way:

{% gist ba9db84a2fc6f9330f3ccf32a352a98e %}

Example usage:

    bougui@mantrisse ~/Documents> bstat bibliography.bib user_guides
    Last completed backup: 00h05m12s ago
    Next backup in 00h09m48s
    ___________________________________________
    Last backup date:      Status:    Filename:
    2016-05-09 15:58:00    NOT        bibliography.bib
    2016-05-09 15:54:00    OK         user_guides

The status field is `OK` when the last version of the file is backuped on
CrashPlan and `NOT` if the last version is not -- the modification time of the
file is posterior to the backup date.

Along with the information above, the command displays some statistics about
the last time of a complete backup occurred and the time to the next backup.
When a backup is currently running it displays the running time of the current
backup instead of the 'Next backup' information:

    Last completed backup: 00h15m10s ago
    Backup running for: 00h00m10s
    ___________________________________________
    [...]

If you want to display only the activity statistics:

    bougui@mantrisse ~> bstat -a
    Last completed backup: 00h12m53s ago
    Next backup in 00h02m07s

