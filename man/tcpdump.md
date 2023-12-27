---
date created: Wednesday, December 27th 2023, 12:22:16 pm
date modified: Wednesday, December 27th 2023, 12:23:14 pm
tags:
  - tcpdump
  - networking
---

# tcpdump

## capture all traffic

filter for all traffic on an individual interface:

```shell
tcpdump -i eth23 -n
```

## filter for protocol

filter for gre (protocol 47) traffic on all interfaces:

```shell
tcpdump -i any -n proto 47
```

## filter specific port

filter for specific port:

```shell
tcpdump -i eth23 -n port 22
```
