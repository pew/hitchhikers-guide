---
date created: Sunday, April 7th 2024, 6:24:58 am
date modified: Sunday, April 7th 2024, 6:26:19 am
tags:
  - linux
---

# linux force reboot

can't run any commands but still have a shell open? and you get errors like this for every command: `Input/output error`

force a reboot like this:

```shell
echo b > /proc/sysrq-trigger
```

[source](https://gist.github.com/mspalex/262144bde795d88de2b4d2d16b9ab143) and [source](https://serverfault.com/questions/452888/difference-between-reboot-n-and-echo-b-proc-sysrq-trigger)
