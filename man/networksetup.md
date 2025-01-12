---
date created: Sunday, January 12th 2025, 11:06:30 am
date modified: Sunday, January 12th 2025, 11:10:41 am
tags:
  - macos
  - networking
---

# networksetup

networksetup – configuration tool for network settings in System Preferences.

## list all network services

```shell
networksetup -listallnetworkservices
```

## get current active network connection

```shell
#!/bin/sh
networksetup -listallnetworkservices | while read -r service; do
  if [ "$service" != "*" ]; then
    status=$(networksetup -getinfo "$service" | grep "IP address" | awk '{print $3}')
    if [ -n "$status" ] && [ "$status" != "none" ]; then
      echo "$service"
      break
    fi
  fi
done
```
