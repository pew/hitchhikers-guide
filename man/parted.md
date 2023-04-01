---
date created: Saturday, April 1st 2023, 9:14:21 am
date modified: Saturday, April 1st 2023, 9:18:03 am
tags:
  - parted
  - filesystem
---

# parted

Assistant: Parted is a Linux utility used for partitioning hard drives. It allows users to create, delete, resize, and move partitions on their hard drives.

## resize partition to 100%

for all the commands, replace `sda`, `sda1` with your actual disk and partition

if you just resized the disk, you might need to rescan the device:

```shell
echo 1 > /sys/block/sda/device/rescan
```

display available space on `/dev/sda`:

```shell
parted -s -a opt /dev/sda "print free"
```

**resize disk:**

it uses the `/dev/sda` disk, partition `1` and just resizes the partition to the maximum amount available

```shell
parted /dev/sda resizepart 1 100%
resize2fs /dev/sda1
```
