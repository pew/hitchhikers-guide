# chroot

## run commands, edit files, install or remove packages

... or a kernel, why not:

### mount disk to rescue system, provide network

well, you need some kind of system to mount the other hard drive, most cloud / server provider do provide something

```
mount /dev/sda1 /mnt
rm /mnt/etc/resolv.conf  # I had to do this once
cp /etc/resolv.conf /etc/
```

### bind mount filesystems

```
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
mount --bind /dev/pts /mnt/dev/pts
mount --bind /run /mnt/run
```

### chroot into your original system

get in there!

```
chroot /mnt
```

now you can run your commands, edit files and do things like you'd do on your regular system. like removing a package:

```
apt-get purge linux-1234
```

afterwards, log out, umount the mounted things from above in *reverse order* and reboot.
