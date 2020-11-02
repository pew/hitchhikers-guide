# lvm

## reduce size of root disk/partition

to resize the root partition:

1. boot into resuce / recovery mode

**this will resize the root volume to 150GB:**

```shell
lvreduce -L 150G /dev/vg0/root
```

## extend disk / partition / volume

resize to 100% of the remaining space

```shell
lvextend -l +100%FREE /dev/vg0/home
```