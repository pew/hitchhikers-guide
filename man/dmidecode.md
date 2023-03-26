---
date created: Sunday, March 26th 2023, 3:19:44 pm
date modified: Sunday, March 26th 2023, 3:21:30 pm
tags:
  - linux
  - bios
  - dmi
  - smbios
---

# dmidecode

[dmidecode](https://linux.die.net/man/8/dmidecode) is a tool for dumping a computer's DMI (some say SMBIOS ) table contents in a human-readable format

## get memory information

manufacturer, parts, speed, type, voltage etc.

```shell
dmidecode -t memory
```
