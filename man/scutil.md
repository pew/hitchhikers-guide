---
date created: Friday, July 28th 2023, 6:02:15 am
date modified: Friday, July 28th 2023, 6:04:33 am
tags:
  - macos
  - scutil
  - vpn
---

# scutil

Manage system configuration parameters

## scutil --nc  (manage VPN connections)

### list profiles

display available VPN connections / profiles:

```shell
scutil --nc list
```

### start / stop vpn connection

this way things can be scripted and automated, perhaps on log in and log out.

**start:**

```shell
scutil --nc start vpn-007
```

**stop:**

```shell
scutil --nc stop vpn-007
```
