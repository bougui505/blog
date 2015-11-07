---
title: "Formatting an external hard drive with parted"
layout: default
date: 2015-11-07
tags:
- linux
- parted
---

# Formatting an external hard drive with parted

## Identifying the external usb hard drive

Plug the usb hard drive and type `df -Th` (`T`: allow to display the file system type):

    /dev/sdb1        fuseblk    932G    121M  932G   1% /media/yourusername/Elements

Unmount the partition to format; here:

    umount /dev/sdb1

## Parted

    sudo parted /dev/sdb

- display the partition table:

    (parted) print
    Model: WD Elements 10B8 (scsi)
    Disk /dev/sdb: 1000GB
    Sector size (logical/physical): 512B/512B
    Partition Table: msdos
    Disk Flags: 

    Number  Start   End     Size    Type     File system  Flags
     1      1049kB  1000GB  1000GB  primary  ntfs

- delete partition 1:

    (parted) rm 1

- Create a new partition table

    (parted) mklabel msdos
    Warning: The existing disk label on /dev/sdb will be destroyed and all data on this disk will be lost. Do you want to continue?
    Yes/No? Yes

- make a partition

    (parted) mkpart
    Partition type?  primary/extended? primary
    File system type?  [ext2]? ext4
    Start? 0%
    End? -1s

Remark: `-1s`: last sector of the drive

    (parted) print
    Model: WD Elements 10B8 (scsi)
    Disk /dev/sdb: 1000GB
    Sector size (logical/physical): 512B/512B
    Partition Table: msdos
    Disk Flags:

    Number  Start   End     Size    Type     File system  Flags
     1      1049kB  1000GB  1000GB  primary  ext4         lba


- exit parted

    (parted) quit
    Information: You may need to update /etc/fstab.

## Formating

    sudo mkfs.ext4 /dev/sdb1

## Test

Unplug and plug again the disk and:

    $ df -hT
    /dev/sdb1                            ext4         917G     72M  871G   1% /media/yourusername/4fc9b323-ac89-444a-9483-9af84030e1a1

Try to write on it:

    cd /media/yourusername/4fc9b323-ac89-444a-9483-9af84030e1a1
    touch toto

If you get a `permission denied` just try to:

    cd ..
    sudo chown yourusername:yourgroupname 4fc9b323-ac89-444a-9483-9af84030e1a1
