---
date created: Saturday, December 27th 2025, 5:12:49 pm
date modified: Saturday, December 27th 2025, 5:17:55 pm
tags:
  - firewall
  - linux
---

# firewalld

… managed using `firewall-cmd`

## list all firewall rules

```shell
firewall-cmd --list-all
```

## get active firewalld zone

```shell
firewall-cmd --get-active-zones
```

## set default firewalld zone

there's a list of [predefined firewall zones](https://firewalld.org/documentation/zone/predefined-zones.html):

- drop - Any **incoming network packets** are dropped, there is no reply. Only outgoing network connections are possible.
- block - Any **incoming network connections** are rejected with an icmp-host-prohibited message for IPv4 and icmp6-adm-prohibited for IPv6. Only network connections initiated within this system are possible.
- public
- external
- dmz
- work
- home
- internal
- trusted

set the default to `block`:

```shell
firewall-cmd --persistent --set-default-zone=block
```

## allow incoming connections for service

```shell
firewall-cmd --persistent --zone=block --add-service=ssh
firewall-cmd --persistent --zone=block --add-service=https
```

## allow incoming connections for a specific port

```shell
firewall-cmd --persistent --zone=block --add-port=80/tcp
firewall-cmd --persistent --zone=block --add-port=443/tcp
```

## reload firewall

```shell
firewall-cmd --reload
```
