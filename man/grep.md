---
date created: Thursday, December 26th 2024, 11:41:09 am
date modified: Friday, December 27th 2024, 10:56:02 am
tags: 
---

# grep

## grep for multiple patterns

*grep* for bluetooth and dbus

```shell
systemctl list-unit-files | grep -E "bluetooth|dbus"
```

## find only lines which do not start with `#`

useful to only see configured settings in config files etc., it'll also omit empty lines:

```shell
grep -vE '^#|^$' filename
```
