# mdadm / software raid

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
