---
date created: Tuesday, June 8th 2021, 5:28:23 am
date modified: Sunday, November 20th 2022, 1:17:08 pm
tags:
  - dd
title: dd
---

# dd

## copy an image to an sd card

I'm using `gdd` here, this requires the homebrew package `coreutils` on a mac. `dd` might also just work on your system.

copy a raspberry pi os image to an sd card:

```
sudo gdd if=2021-05-07-raspios-buster-armhf.img of=/dev/rdisk4 bs=32M conv=fsync status=progress
```

## backup and restore image

**get blocksize**:

```shell
tune2fs -l /dev/sdb2|grep -i 'block size'
```

**backup disk/sd-card to an image**:

```shell
dd if=/dev/sdb of=rpi_backup.img bs=4096 conv=noerror,sync status=progress
```

**restore image to disk/sd-card**:

just reverse the above:

```shell
dd if=rpi_backup.img of=/dev/sdb bs=4096 conv=noerror,sync status=progress
```

## write directly to disk from stdin (wget, curl etc.)

it's 2022, `curl|bash` is fine (👮‍♂️), so `wget | dd` is as well. Common use case: You got a rescue system with a live cd but not enough/configurable storage and want to write a linux iso directly to another disk. Also, Ubuntu doesn't provide an easy to find netboot image anymore so you need at least a 1.3gb download.

```shell
wget -O - https://cdimage.ubuntu.com/ubuntu-server/focal/daily-live/current/focal-live-server-amd64.iso | dd of=/dev/sda
```

## flash iso to usb stick on macos

```shell
diskutil list # find the thumb drive you just inserted
diskutil unmountDisk disk7 # unmount all partitions
dd if=ubuntu-22.04-desktop-amd64.iso of=/dev/rdisk7 bs=4M ## use rdisk instead of disk to make it fast
```

[rdisk vs. disk](https://superuser.com/a/631601)
