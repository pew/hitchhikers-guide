---
tags: 
date created: Monday, April 22nd 2019, 6:51:17 pm
date modified: Tuesday, April 19th 2022, 2:33:46 pm
title: systemd
---

# systemd

hi.

## high disk usage (log files)

meh...

check current disk usage of systemd:

```
journalctl --disk-usage
```

clean up some old logs:

```
journalctl --vacuum-size=100M
```

make this stuff permanent, edit `/etc/systemd/journald.conf`

```
SystemMaxUse=50M
```

and restart things

```
systemctl restart systemd-journald.service
```

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

## change hostname

```shell
sudo hostnamectl set-hostname my-awesome-host
```

depending on your setup you might still need to update your `/etc/hosts` file as well

## timers (better cronjobs!)

todo.. write something somewhere about the use of systemd-timers instead of cronjobs.

### list timers

```
systemctl list-timers
```

### disable timer

```shell
systemctl disable name.timer
```

## tail / follow logs

```
journalctl -f -u your-name.service
```
