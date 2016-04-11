---
title: "Setting higher screen resolution for external monitor on Linux"
layout: default
date: 2016-04-11
tags:
- linux
---

# Setting higher screen resolution for external monitor on Linux


The `xrandr` command gives you informations about your actual displays, and the
names of the displays (e.g. `DP2`):


    bougui@mantrisse ~> xrandr
    Screen 0: minimum 320 x 200, current 3200 x 1200, maximum 8192 x 8192
    eDP1 connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
       1600x900      59.99*+  40.00  
       1440x900      59.89  
       1360x768      59.80    59.96  
       1152x864      60.00  
       1024x768      60.00  
       800x600       60.32    56.25  
       640x480       59.94  
    DP1 disconnected (normal left inverted right x axis y axis)
    HDMI1 disconnected (normal left inverted right x axis y axis)
    DP2 connected 1600x1200+1600+0 (normal left inverted right x axis y axis) 0mm x 0mm
       1024x768      60.00  
       800x600       60.32    56.25  
       848x480       60.00  
       640x480       59.94  
       1600x1200_60.00  59.87* 
    HDMI2 disconnected (normal left inverted right x axis y axis)

Typically, the command `cvt` format the parameters you want for the chosen
resolution (usually given by the constructor of the monitor you use).

After that, you add a new mode to xrandr and you add this new mode to the
chosen display (e.g. `DP2`).

Then, you choose this new mode for this `DP2` display.

The script below set the resolution of the second display `DP2` to 1600x1200:

{% gist a1817073bc5ec0cd61e69a643b091fdc %}
