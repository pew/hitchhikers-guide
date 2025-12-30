---
date created: Saturday, March 26th 2022, 7:07:01 am
date modified: Tuesday, December 30th 2025, 8:59:14 am
tags:
  - btrfs
  - linux
  - filesystem
---

# btrfs

- see also: [parted](/man/parted/)

## check and scrub btrfs filesystem

### scrub

this just checks checksums of the data, it does not repair a filesystem

**start the process:**

```shell
sudo btrfs scrub start /
```

**check the status:**

```shell
sudo btrfs scrub status /
```

### check

should be done on a readonly or not mounted filesystem, however it can be run on a mounted filesystem as well, with the `--readonly` and `--force` flag you can make sure that nothing will be modified:

```shell
btrfs check --readonly --force /dev/md0
```

## create btrfs filesystem and partition

```shell
parted -s /dev/nvme1n1 mklabel gpt
parted -s /dev/nvme1n1 mkpart primary 4MiB 100%
partprobe /dev/nvme1n1
sgdisk --typecode=1:8300 /dev/nvme1n1
mkfs.btrfs -L data /dev/nvme1n1p1
```

## resizing btrfs filesystems

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

### snapshot utilities

- [snapper](https://github.com/openSUSE/snapper) - automatically create snapshots based on a configuration
- [snap-sync](https://github.com/baod-rate/snap-sync) - send snapshots to a target destination, another disk locally, ssh etc.

### list snapshots

```shell
sudo btrfs subvolume list /
```

### get more information about a snapshot

```shell
btrfs subvol show /.snapshots/1236/snapshot/
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
