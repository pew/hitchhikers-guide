# lvm

## reduce size of root disk/partition

**lesson learned:** don't do this when using `XFS` as a filesystem

**resize root volume:**

1. boot into resuce / recovery mode
2. activate / get all volumes:

```shell
vgchange -ay
```

resize volume **to 150GB:**

```shell
lvreduce -L 150G /dev/vg0/root
```

## extend disk / partition / volume

**resize to 100% of the remaining space:**

```shell
lvextend -l +100%FREE /dev/vg0/home
```

## resize encrypted volume luks

see also [cryptsetup](/man/cryptsetup/)

```shell
growpart /dev/sda 3 # lsblk (disk partition number)
cryptsetup resize dm_crypt-0 # 
lvextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv # lvdisplay
```