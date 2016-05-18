---
title: "Randomly change desktop wallpaper on Gnome desktop"
layout: default
date: 2016-05-18
tags:
- gnome
- linux
---

# Randomly change desktop wallpaper on Gnome desktop

Below is the script to change the desktop wallpaper. The images are assumed to
be in `$HOME/wallpapers` directory:

{% gist e543ab6937ba31488d98ff081f9ef139 %}

Just add that entry to the user crontab to change the wallpaper every hour
(with the command `crontab -e`):

    0 * * * * sh /PATH/TO/SCRIPT/random_wallpaper.sh

If you get the following error message:

    (process:21381): dconf-WARNING **: failed to commit changes to dconf: Cannot autolaunch D-Bus without X11 $DISPLAY

Just add that line to your crontab:

    DISPLAY=:0

This line tell cron that the display it requires to run the windowed applications is found at 0. (see [http://www.codecoffee.com/tipsforlinux/articles/23.html](http://www.codecoffee.com/tipsforlinux/articles/23.html))
