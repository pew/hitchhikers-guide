---
date created: Saturday, March 26th 2022, 7:07:01 am
date modified: Wednesday, August 2nd 2023, 6:38:15 am
tags:
  - btrfs
  - linux
  - filesystem
---

# btrfs

## resize btrfs filesystem

to max:

```shell
btrfs filesystem resize max /
```

by gb:

```shell
btrfs filesystem resize +10g /
```

## managing btrfs snapshots

you should use them more often, perhaps in combination with a [a backup tool](restic.md)

### list snapshots

```shell
sudo btrfs subvolume list /
```

### create a read only snapshot

```shell
sudo btrfs subvolume snapshot / /my_snapshot # root partition
sudo btrfs subvolume snapshot /mnt /mnt/my_snapshot # partition mounted at /mnt
```

### delete btrfs snapshot

```shell
sudo btrfs subvolume delete /my_snapshot
sudo btrfs subvolume delete /mnt/my_snapshot
```

## btrfs raid configuration

- [btrfs raid calculator](https://carfax.org.uk/btrfs-usage/)

### convert raid levels, from raid0 to raid1

```shell
btrfs balance start -dconvert=raid1 -mconvert=raid1 /mnt
```

### raid1

with kernel version 5.5+ `raid1c3` can be used for the metadata (`-m`)

```shell
mkfs.btrfs -m raid1 -d raid1 /dev/sdb /dev/sdc
```
