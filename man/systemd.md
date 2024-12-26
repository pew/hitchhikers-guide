---
date created: Monday, April 22nd 2019, 6:51:17 pm
date modified: Thursday, December 26th 2024, 11:48:10 am
tags:
  - systemd
  - systemctl
  - linux
title: systemd
---

# systemd

🤷‍♂️

## analyze slow boot times

list how long it took for systemd units to initialize:

```shell
systemd-analyze blame
```

output example:

```
2min 158ms systemd-networkd-wait-online.service
```

## DNS

all things DNS

### change dns resolver

get current status and dns server:

```shell
resolvectl status
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

### change hostname

```shell
sudo hostnamectl set-hostname my-awesome-host
```

depending on your setup you might still need to update your `/etc/hosts` file as well

### clear dns cache

```shell
resolvectl flush-caches
```

verify:

```shell
resolvectl statistics
```

## logs: journalctl / systemd journals

### read journalctl logs / syslog

the following flags can usually be combined, so `-f -u <service>` works as well.

**follow all new logs (tail -f):**

```shell
journalctl -f
```

**display last 100 lines and follow new logs:**

```shell
journalctl -n 100 -f
```

**read logs from a specific service/unit:**

```shell
journalctl -u your-name.service
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

### log disk usage

check current disk usage of systemd journals:

```shell
journalctl --disk-usage
```

clean up some old logs:

```shell
journalctl --vacuum-size=100M
```

## timers (better cronjobs!)

todo.. write something somewhere about the use of systemd-timers instead of cronjobs.

### create your own timer / cronjob

**create your service unit:**

place it somewhere in `/etc/systemd/system/restic_backup.service` for example

```
[Unit]
Description=restic systemd service

[Service]
ExecStart=/usr/local/bin/backup.sh

[Install]
WantedBy=multi-user.target
```

**create your timer:**

place it in the same folder but name it `.timer`, like this: `/etc/systemd/system/restic_backup.timer`

```
[Unit]
Description=restic systemd timer

[Timer]
OnUnitActiveSec=24h
RandomizedDelaySec=1h

[Install]
WantedBy=multi-user.target
```

there are many different ways when the service should run, like with `OnUnitActiveSec` every 24 hours including a randomized delay of 1h.

[here's the documentation](https://www.freedesktop.org/software/systemd/man/systemd.timer.html#) for more ways when system should execute something

**reload and enable the service:**

```
systemctl daemon-reload
systemctl enable restic_backup.timer
```

### disable timer

```shell
systemctl disable name.timer
```

### list timers

```
systemctl list-timers
```

### remove / clear dead or dangling timers

I removed a service and timer through ansible and reloaded systemd, but the timer was still showing up when running `systemd list-timers`. This worked to clean it up:

```shell
systemctl reset-failed
```

## working with services

### debugging: read and follow service logs output

**read logs**:

```shell
journalctl -u your-name.service
```

**tail log**:

```shell
journalctl -f -u your-name.service
```

### disable / mask service, prevent from starting & unmask

***disabling*** a service prevents it from being started automatically on boot but it can still be interacted with, or started by other services. ***masking*** a service means it can't even be started using systemd, it'll essentially create a symlink to `/dev/null`

#### mask / unmask services

**list masked services:**

```shell
systemctl list-unit-files | grep masked
```

**mask a service / prevent service from being started at all:**

```shell
systemctl mask wpa_supplicant.service
```

the output will also tell you that the service has been linked to `/dev/null`:

```shell
Created symlink /etc/systemd/system/wpa_supplicant.service → /dev/null.
```

**unmask a service:**

```shell
systemctl unmask bluetooth.service
```

#### disable a service

**disable a service from starting automatically:**

it can be started manually, for example by NetworkManager

```shell
systemctl disable wpa_supplicant.service
```

### list active services

the service might be *active*, but exited already since it was just initializing or checking something

```shell
systemctl list-units --type=service --state=active
```

### list running services

```shell
systemctl list-units --type=service --state=running
```
