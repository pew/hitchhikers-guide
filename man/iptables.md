# iptables

see also [ufw](/man/ufw)

## redirect port to other ip:port

redirect port 88 form server A to server B (192.168.1.128) port 88, also add the SNAT rule to get the traffic back to the source (server A, with IP 192.168.1.193)

```
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A PREROUTING -p tcp --dport 88 -j DNAT --to-destination 192.168.1.128:88
iptables -t nat -A POSTROUTING -p tcp -d 192.168.1.128 --dport 88 -j SNAT --to-source 192.168.1.193
```

**make ip forward permanent:**

```
$ vim /etc/sysctl.conf:

    net.ipv4.ip_forward = 1

$ sysctl -p /etc/sysctl.conf
```

## port redirection

80 to 8888

```
iptables -t nat -I PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8888
```
