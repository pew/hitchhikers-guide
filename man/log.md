---
date created: Tuesday, February 11th 2025, 5:50:40 am
date modified: Tuesday, March 18th 2025, 8:32:49 am
tags: 
---

# log / syslog

I run these commands on macOS.

## info and debug logs

you can always pass `--info` and/or `--debug` to get more detailed output

## filter logs for the last `n` seconds/minutes/hours

```shell
log show --last 10s
log show --last 1m
log show --last 1h
```

## get sleep wake reasons and times

from the past 12 hours. check the man page for more information: `man log`

you can do things like ``--last 2d` for days and so on.

```shell
log show --last 12h --style syslog | fgrep "powerd:sleepWake]"
```

## filter logs for specific subsystem

```shell
log show --predicate 'subsystem == "com.apple.HIToolbox"' --info
```

## exclude process(es) from log output

```shell
log stream --predicate 'process != "mds" AND process != "dasd"' --info
```

## stream logs

```shell
log stream --predicate 'subsystem == "com.apple.HIToolbox"' --info
```
