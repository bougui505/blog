---
title: "Logical Volume Manager (LVM)"
layout: default
date: 2016-02-16
tags:
- lvm
- linux
---

# Logical Volume Manager (LVM)

## Listing Physical Volumes (PV)

    bougui@mantrisse ~> sudo pvs
      PV         VG           Fmt  Attr PSize   PFree
      /dev/sda5  mantrisse-vg lvm2 a--  465,52g 247,52g

## Listing Volume Groups (VG)

    bougui@mantrisse ~> sudo vgs
      VG           #PV #LV #SN Attr   VSize   VFree
      mantrisse-vg   1   3   0 wz--n- 465,52g 247,52g

## Listing Logical Volumes (LV)

    bougui@mantrisse ~> sudo lvs
      LV     VG           Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
      home   mantrisse-vg -wi-ao---- 100,00g
      root   mantrisse-vg -wi-ao---- 100,00g
      swap_1 mantrisse-vg -wi-ao----  18,00g

## Display informations about logical volumes

    bougui@mantrisse ~> sudo lvdisplay
        [...]
      --- Logical volume ---
      LV Path                /dev/mantrisse-vg/home
      LV Name                home
      VG Name                mantrisse-vg
        [...]
      LV Write Access        read/write
      LV Creation host, time mantrisse, 2015-09-02 14:34:37 +0200
      LV Status              available
      # open                 1
      LV Size                100,00 GiB
      Current LE             25600
      Segments               1
      Allocation             inherit
      Read ahead sectors     auto
      - currently set to     256
      Block device           254:2

## Resize a given LV

- Resize `/dev/mantrisse-vg/home` by adding 50 Go:

    bougui@mantrisse ~> sudo lvresize -L+50g /dev/mantrisse-vg/home
      Size of logical volume mantrisse-vg/home changed from 100,00 GiB (25600 extents) to 150,00 GiB (38400 extents).
      Logical volume home successfully resized

- and then resize the file system to cover the full space available:

    bougui@mantrisse ~> sudo resize2fs /dev/mantrisse-vg/home
    resize2fs 1.42.12 (29-Aug-2014)
    Le système de fichiers de /dev/mantrisse-vg/home est monté sur /home ; le changement de taille doit être effectué en ligne
    old_desc_blocks = 7, new_desc_blocks = 10
    Le système de fichiers sur /dev/mantrisse-vg/home a maintenant une taille de 39321600 blocs (4k).
