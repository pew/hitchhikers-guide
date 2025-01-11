---
date created: Saturday, January 11th 2025, 9:26:35 am
date modified: Saturday, January 11th 2025, 9:34:42 am
tags: 
---

# nmcli, networkmanager

NetworkManager - network management daemon

## restart NetworkManager

it's NetworkManager, not networkmanager :)

```shell
systemctl restart NetworkManager.service
```

## get general network overview

```shell
nmcli
```

## get list of network devices and status

```shell
nmcli device status
```

## get information about networkmanager connections

```shell
nmcli con
```

## change dns resolver with NetworkManager

instead of editing `/etc/resolv.conf`, do the following (with `nmcli con` you get the connection name.):

```shell
nmcli con mod "Wired connection 1" ipv4.dns "127.0.0.1"
nmcli con mod "Wired connection 1" ipv6.dns "::1"
```

### disable DHCP provided dns

if you execute the above, you'll still have the DNS servers provided by the DHCP server available as well, do disable this behavior:

```shell
nmcli con mod "Wired connection 1" ipv4.ignore-auto-dns yes
nmcli con mod "Wired connection 1" ipv6.ignore-auto-dns yes
```
