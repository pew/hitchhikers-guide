# ulimit

editing `/etc/security/limits.conf` might not result in anything you're looking for. Go ahead:

create the folder `/etc/systemd/system.conf.d/` and edit the following file:

```
sudo mkdir -p /etc/systemd/system.conf.d/
sudo vi /etc/systemd/system.conf.d/limits.conf
```

put this in here, you might want to adopt the numbers

```
[Manager]
DefaultLimitNOFILE=1048576:2097152
DefaultLimitNPROC=262144:524288
```

you need to restart the systems afterwards.

[source](https://unix.stackexchange.com/questions/366352/etc-security-limits-conf-not-applied)