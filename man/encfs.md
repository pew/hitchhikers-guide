# encfs

encrypt a directory

## installation

```
apt-get install encfs
```

## usage

**encrypt a directory:**

the data in `/media/data` will be encrypted and mounted into `/mnt`

```
encfs /media/data /mnt
```

**note if you're using sshfs:**

this sucked! mount it like so:

```
sshfs -o uid=$UID user@your-server.com:/ /data
```

after you went through the wizard, you can use the same command to mount your disk. you might want to backup the created file `/media/data/.encfs6.xml`

**umount encfs:**

```
fusermount -u /mnt
```

**let other users see the contents:**

there are use cases for it, but be careful

```
encfs encfs --public /media/data /mnt
```
