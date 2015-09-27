---
title: "Backup raspberry pi SD card"
layout: default
category: linux
date: 2015-09-26
tags:
- linux
- raspberry-pi
---

# Backup raspberry pi SD card

To backup the SD card:

- First read the SD card on a linux computer and identify it:

```
$ sudo fdisk -l
Disque /dev/sda : 232,9 GiB, 250059350016 octets, 488397168 secteurs
Unités : secteur de 1 × 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Type d'étiquette de disque : dos
Identifiant de disque : 0x0008d6d7

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1  *        2048  19531775  19529728   9,3G 83 Linux
/dev/sda2       19533822 488396799 468862978 223,6G  5 Extended
/dev/sda5       19533824  23384063   3850240   1,9G 82 Linux swap / Solaris
/dev/sda6       23386112 488396799 465010688 221,8G 83 Linux

Disque /dev/mmcblk0 : 14,9 GiB, 15931539456 octets, 31116288 secteurs
Unités : secteur de 1 × 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Type d'étiquette de disque : dos
Identifiant de disque : 0x000b5098

Device         Boot  Start      End  Sectors  Size Id Type
/dev/mmcblk0p1        8192   122879   114688   56M  c W95 FAT32 (LBA)
/dev/mmcblk0p2      122880 31116287 30993408 14,8G 83 Linux
```

- Backup and compress the image:

```
sudo dd if=/dev/mmcblk0 | gzip -9 > ./raspberrypi_20150926.img.gz
```

- To restore the image:

```
gunzip ./raspberrypi_20150926.img.gz | sudo dd of=/dev/mmcblk0
```
