---
date created: Wednesday, September 2nd 2020, 6:06:26 pm
date modified: Sunday, October 2nd 2022, 6:46:05 am
tags:
  - ip
  - ipv6
  - ifconfig
  - ipv4
  - routing
title: ip
---

# ip, ipconfig, ifconfig, netplan

let's get used to `ip` instead of `ifconfig`. d'oh

## display bandwidth usage

```shell
ip -s -h link
```

just for a single device (man I get get used to this `ip` command...)

```shell
ip -s -h link show dev eth0
```

[thank you](https://askubuntu.com/a/981737)

## check ip route

```shell
ip route get 2606:4700::6812:7361
2606:4700::6812:7361 from :: via fe80::fc00:3ff:fed2:ba70 dev enp1s0 proto ra src 2001:abcd:abcd::100 metric 100 mtu 1500 pref medium
```

```shell
ip route get 2a01:4f8:c0c:bd0a::1
2a01:4f8:c0c:bd0a::1 from :: via fe80::fc00:3ff:fed2:ba70 dev enp1s0 proto ra src 2a05:abcd:abcd::ba70 metric 100 mtu 1500 pref medium
```

## set source address

first, note down the current routing table, you might want to note down the default gateway address with this command as well. It might come in handy depending on your setup.

omit the `-6` for ipv4

```shell
ip -6 route # note the default gateway down, fe80::1 in my example
```

next, see inline comments

```shell
ip -6 route del default # delete default gateway
ip -6 addr add 2001:abcd:abcd::2 dev eth0 # add your new source address
ip -6 route add default via fe80::1 src 2001:abcd:abcd::2 dev eth0 # set your new default gateway with a specific source address 
```

## get IPv6 default route

replace `enp0s3` with your network interface

```shell
rdisc6 -1 enp0s3|grep from
```

you can use the output in a netplan config then, like so. For example if you want to configure IPv6 with Oracle Cloud:

```yaml
network:
    ethernets:
        enp0s3:
            dhcp4: true
            addresses:
              - 2603:1234:1234:beef::/128
            gateway6: fe80::200:17ff:fe63:44c5
            set-name: enp0s3
    version: 2
```

## set IPv6 source address

```shell
ip -6 route add default via fe80::fc00:3ff:fed2:ba70 src 11fb:3f20:c466:5c32:0938:d2f5:ea52:aa3c dev enp1s0 metric 1
```
