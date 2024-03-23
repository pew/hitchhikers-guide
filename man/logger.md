---
date created: Saturday, March 23rd 2024, 11:13:02 am
date modified: Saturday, March 23rd 2024, 11:15:15 am
tags:
  - syslog
  - logger
---

# logger

## send message to syslog server

useful for testing

**send via TCP** using the `-T` flag:

```shell
logger -n localhost -P 6514 -T -i "hello world"
```

**send via UDP** using the `-d` flag:

```shell
logger -n localhost -P 6514 -d -i "hello world"
```
