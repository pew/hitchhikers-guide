# systemd

hi.

## DNS

all things DNS

### change dns resolver

get current status and dns server:

```
sudo systemd-resolve --status
```

change to another DNS server:

edit `/etc/systemd/resolved.conf` and change the `DNS` line. for example:

```
[Resolve]
DNS=1.1.1.1 8.8.8.8
```

restart service:

```
sudo systemctl restart systemd-resolved.service
```

verify again (see above)

### clear dns cache

```
sudo systemd-resolve --flush-caches
```

verify:

```
sudo systemd-resolve --statistics
```
