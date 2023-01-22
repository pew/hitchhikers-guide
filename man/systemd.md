---
date created: Monday, April 22nd 2019, 6:51:17 pm
date modified: Sunday, January 22nd 2023, 10:05:35 am
tags:
  - systemd
  - systemctl
title: systemd
---

# systemd

🤷‍♂️

## logs / systemd journals

### log disk usage

check current disk usage of systemd journals:

```shell
journalctl --disk-usage
```

clean up some old logs:

```shell
journalctl --vacuum-size=100M
```

### configure journal / log usage

it might be a good idea to limit the disk usage of your systemd journals. To do this, edit the file: `/etc/systemd/journald.conf`

**control how much disk space the journal may use up at most**:

```
SystemMaxUse=1G
```

**control how large individual journal files may grow at most**:

```
SystemMaxFileSize=100M
```

and restart things

```shell
systemctl daemon-reload # for good measure
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

if you want to use DNS over TLS:

```
[Resolve]
DNS=1.1.1.1#1dot1dot1dot1.cloudflare-dns.com
DNSOverTLS=Yes
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

## working with services

### list active services

the service might be *active*, but exited already since it was just initializing or checking something

```shell
systemctl list-units --type=service --state=active
```

### list running services

```shell
systemctl list-units --type=service --state=running
```

## tail / follow logs

```
journalctl -f -u your-name.service
```
