---
date created: Monday, September 2nd 2024, 2:03:46 pm
date modified: Monday, September 2nd 2024, 2:05:05 pm
tags:
  - linux
---

# netplan

see also [ip, ipconfig, ifconfig, netplan](ip,%20ipconfig,%20ifconfig,%20netplan.md)

## configure virtual interface with vlan

the most basic example, create a virtual network interface with a tagged vlan and use dhcp to acquire an IP address:

edit `/etc/netplan/00-installer-config.yaml`

```yaml
network:
  version: 2
  ethernets:
    enp2s0:
      dhcp4: true
  vlans:
    vlan2:
      id: 2
      link: enp2s0
      dhcp4: true
```

apply the config with

```shell
netplan apply
```
