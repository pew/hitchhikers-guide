---
date created: Tuesday, March 14th 2023, 5:11:40 am
date modified: Tuesday, March 14th 2023, 5:14:37 am
tags:
  - ipmi
  - ipmitool
---

# ipmitool

## set networking for IPMI

**display current config:**

```shell
ipmitool lan print
```

**change it:**

```shell
ipmitool lan set 1 ipaddr 192.168.1.2
ipmitool lan set 1 netmask 255.255.255.0
ipmitool lan set 1 defgw ipaddr 192.168.1.1
```

## get hardware overview

```shell
ipmitool fru
```

## list sensor status and information

```shell
ipmitool sensor list
```

## print syslog

```shell
ipmitool sel list
```
