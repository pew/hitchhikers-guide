# fstab

--

# mount external disk only if present

add to `/etc/fstab`

```
/dev/sda1 /mnt ext4 nofail,x-systemd.device-timeout=1 0 2
```
