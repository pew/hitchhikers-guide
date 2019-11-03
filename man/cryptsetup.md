# cryptsetup / encrypt disk luks / dm-crypt

encrypt a disk!

## installation

```
apt-get install cryptsetup
```

## encrypt the device

```
cryptsetup luksFormat <device> # e.G. /dev/sda1
```

## unlock device

```
cryptsetup luksOpen <device> <coolname> # e.G. /dev/sda1 fortknox
```

### format device

**do this only one time during setup, afterwards jump right to [mounting the device](#mount-device)**

```
mkfs.ext4 /dev/mapper/<coolname> # e.G. /dev/mapper/fortknox
```

## mount device

```
mount /dev/mapper/<coolname> /mnt
```

## resize luks encrypted disk

```
cryptsetup luksOpen /dev/sda fortknox
cryptsetup resize /dev/mapper/fortknox
resize2fs /dev/mapper/fortknox
mount /dev/mapper/fortknox /mnt
```

## backup /restore luks header

```
cryptsetup luksHeaderBackup /dev/sda --header-backup-file luks_backup_fortknox
cryptsetup luksHeaderRestore /dev/sda --header-backup-file luks_backup_fortknox
```

