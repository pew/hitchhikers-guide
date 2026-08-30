---
date created: Sunday, August 30th 2026, 12:58:33 pm
date modified: Sunday, August 30th 2026, 1:00:31 pm
tags:
  - macos
  - launchctl
---

# launchctl

## managing services (load, unload, restart)

enable and load a service:

```shell
launchctl bootstrap gui/$(id -u) ~/Library/LaunchAgents/com.example.your-app
```

disable and unload a service

```shell
launchctl bootout gui/$(id -u)/com.example.your-app
```

restart a service:

```shell
launchctl kickstart -k gui/$(id -u)/com.example.your-app
```
