# ip 

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

```
ip route get 2606:4700::6812:7361
2606:4700::6812:7361 from :: via fe80::fc00:3ff:fed2:ba70 dev enp1s0 proto ra src 2001:abcd:abcd::100 metric 100 mtu 1500 pref medium
```

```
ip route get 2a01:4f8:c0c:bd0a::1
2a01:4f8:c0c:bd0a::1 from :: via fe80::fc00:3ff:fed2:ba70 dev enp1s0 proto ra src 2a05:abcd:abcd::ba70 metric 100 mtu 1500 pref medium
```