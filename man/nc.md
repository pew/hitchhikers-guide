---
date created: Monday, May 18th 2020, 7:20:39 pm
date modified: Saturday, March 23rd 2024, 11:25:34 am
tags:
  - nc
  - netcat
---

# nc / netcat

there are a lot of use cases... let's start with. ~~1~~.

## file transfer

sender:

```
tar -czf - folder | nc -l 9999
```

receiver:

```
nc <senderip> 9999|tar xvf -
```

## send syslog message

see also [logger](/man/logger)

```shell
echo "<14>hello world" | nc -u -w1 hostname port
```
