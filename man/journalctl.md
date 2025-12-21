---
date created: Saturday, December 28th 2024, 11:25:08 am
date modified: Sunday, December 21st 2025, 11:25:48 am
tags:
  - systemd
---

# journalctl

the new `/var/log/syslog`

- see also [systemd](systemd.md)

## specify unit / service

use the `-u` flag to work with a specific service, for example `journalctl -u systemd-resolved` you can also add multiple units using `-u` in one go

```shell
journalctl -u systemd-resolved
journalctl -u systemd-resolved -u systemd-networkd
```

## read journalctl logs

the following flags can usually be combined, so `-f -u <service>` works as well.

### tail / follow logs

**follow all new logs (tail -f):**

```shell
journalctl -f
```

### read last n lines

**display last 100 lines and follow new logs:**

```shell
journalctl -n 100 -f
```

### logs since last boot

```shell
journalctl -b
```

### logs since yesterday | today | 2 hours ago

```shell
journalctl -u systemd-resolved --since yesterday
journalctl -u systemd-resolved --since today
journalctl -u systemd-resolved --since "1 hour ago"
```
