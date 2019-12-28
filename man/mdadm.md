# mdadm / software raid

## create raid

**raid 1:**

```
mdadm --create /dev/md0 --level=1 --raid=devices=2 /dev/sda /dev/sdb
```

**create a file system:**

```
mkfs.ext4 /dev/md0
```

or whatever filesystem you want.

## check raid status

```
mdadm --detail /dev/md0
```

check also: `/proc/mdstat`

## save raid config

well, that's somewhat important, right?

```
mdadm --detail --scan --verbose | sudo tee -a /etc/mdadm/mdadm.conf
```

Run `update-initramfs -u` after updating this file.

## replace disk

**remove disk:**

```
mdadm /dev/md0 -r /dev/sdb
```

**copy partition table from backup or primary drive:**

```
sfdisk -d /dev/sda | sfdisk /dev/sdb
```

**add disk:**

```
mdadm /dev/md0 -a /dev/sdb
```

## convert single disk to raid 1

... hopefully without losing data!

1. create raid from 2nd disk with one missing disk
2. copy data from 1st disk to 2nd disk (now in raid)
3. add 1st (original) disk to raid config
4. rebuild raid
5. profit (took 5 steps, I'm sorry)

**create raid:**

notice the `missing` bit?

```
mdadm --create /dev/md0 --level=1 --raid-devices=2 missing /dev/sdb
```

now copy the data from the original disk to the newly created raid, so create and mount your filesystem on `/dev/md0`

[...]

**prepare original disk:**

let's dump (`-d` the disk layout from the raid disk to the original disk):

```
sfdisk -d /dev/sdb | sfdisk /dev/sda
```

**add original disk to raid:**

```
mdadm /dev/md0 -a /dev/sda
```

**check raid rebuild status:**

...in minutes

```
grep -oP 'finish\=\d+\.\d+' /proc/mdstat | cut -d'=' -f2
```
