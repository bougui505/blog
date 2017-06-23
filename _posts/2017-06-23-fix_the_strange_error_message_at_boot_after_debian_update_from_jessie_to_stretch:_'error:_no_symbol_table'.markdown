---
title: "Fix the strange error message at boot after Debian update from Jessie to Stretch: 'error: no symbol table'"
layout: default
date: 2017-06-23
tags:
- debian
- linux
---

# Fix the strange error message at boot after Debian update from Jessie to Stretch: 'error: no symbol table'

I Just reinstalled grub:

    sudo grub-install /dev/sda # Just change sda by the location of your boot partition /dev/sdX, where X is the drive (letter) on which you want GRUB to write the boot information. Normally users should not include a partition number, which would produce an error message as the command would attempt to write the information to a partition.
    sudo update-grub

Then I rebooted and no more weird message.
