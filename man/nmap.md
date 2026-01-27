---
date created: Tuesday, January 27th 2026, 8:11:56 am
date modified: Tuesday, January 27th 2026, 8:13:10 am
tags:
  - nmap
  - networking
---

# nmap

- [nmap guide](https://nmap.org/book/toc.html)

## rootless network scan

```shell
nmap -T5 -sn -PR --script broadcast-dns-service-discovery,broadcast-upnp-info 192.168.1.0/24
```

see [here](https://news.ycombinator.com/item?id=46736516)
