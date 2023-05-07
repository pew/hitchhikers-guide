---
date created: Sunday, May 7th 2023, 3:37:32 pm
date modified: Sunday, May 7th 2023, 3:43:11 pm
tags:
  - linux
  - sgdisk
  - sfdisk
---

# sfdisk, sgdisk

check with `fdisk -l` for the `type` of your disk and move on with sfdisk or sgdisk

## sfdisk for MBR disks

**dump / backup table:**

```shell
sfdisk -d /dev/sda > sda.sfdisk
```

**copy from sda to sdb:**

```shell
sfdisk -d /dev/sda | sfdisk /dev/sdb
```

## sgdisk for GPT disks

**dump / backup table:**

```shell
sgdisk --backup=nvme0n1.sgdisk /dev/nvme0n1
```

**copy from a to b:**

```shell
sgdisk --replicate=/dev/nvme1n1 /dev/nvme0n1 # nvme1n1 is the DESTINATION
```

you can optionally change the uuids as well of the new disk:

```shell
sgdisk -G /dev/nvme1n1
```
