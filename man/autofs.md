# autofs

automatically mount remote filesystems on a as-needed basis. quite handy from time to time.

* [here are some docs with some examples](https://help.ubuntu.com/community/Autofs)

## nfs auto mount

**installing autofs:**

```shell
apt-get install autofs
```

**configure a nfs share:**

I did this for my synology nas, I created a new folder on my other linux system at `/nfs`, let's edit `/etc/auto.master` to make this work. Add the following to the end of `/etc/auto.master`

```shell
/nfs /etc/auto.nfs
```

then create or edit `/etc/auto.nfs`:

```shell
synologyName synologyHostname.local:/volume1/synologyShare
```

**restart / reload autofs:**

```shell
systemctl restart autofs
```

well, now you should be good to go if you do something like:

```shell
ls /nfs/synologyName
```

`autofs` should automatically mount the share
