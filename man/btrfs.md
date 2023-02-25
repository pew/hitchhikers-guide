---
date created: Saturday, March 26th 2022, 7:07:01 am
date modified: Saturday, February 25th 2023, 11:20:46 am
tags:
  - btrfs
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
