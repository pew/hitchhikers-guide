---
date created: Saturday, December 28th 2024, 11:25:08 am
date modified: Saturday, December 28th 2024, 11:28:03 am
tags:
  - systemd
---

# journalctl

the new `/var/log/syslog`

- see also [systemd](systemd.md)

## read journalctl logs

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

**read logs since last boot:**

```shell
journalctl -b
```
