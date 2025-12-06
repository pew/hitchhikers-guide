---
date created: Saturday, December 6th 2025, 11:46:29 am
date modified: Saturday, December 6th 2025, 11:50:46 am
tags:
  - grub
  - linux
---

# grub

## reset (root) password in grub

in the grub shell:

```shell
search --no-floppy --label boot --set=bootp
ls ($bootp)/
```

non-UEFI:

```shell
linux ($bootp)/vmlinuz-<TAB-TAB-TAB> root=LABEL=root rootfstype=btrfs rootflags=subvol=@ ro init=/bin/bash
initrd ($bootp)/initrd.img-<TAB-TAB-TAB>
boot
```

UEFI:

```shell
linuxefi ($bootp)/vmlinuz-<TAB_COMPLETE> root=LABEL=root rootfstype=btrfs rootflags=subvol=@ ro init=/bin/bash
initrdefi ($bootp)/initrd.img-<TAB_COMPLETE>
boot
```

ideally you are in your root shell now:

```shell
mount -o remount,rw /
passwd
sync
exec /sbin/reboot -f
```
