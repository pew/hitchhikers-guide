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
