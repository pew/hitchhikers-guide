# wireguard

## route wireguard traffic through another interface

assume that you have multiple network interfaces on a server and want to use wireguards outgoing traffic to go such one, add the following to your interface config in `/etc/wireguard/wg0.conf`. in this case it's `gre-cf`

```
[Interface]
Address = 10.0.0.1/24
ListenPort = 51820
PostUp=iptables -A FORWARD -i %i -j ACCEPT; iptables -A FORWARD -o %i -j ACCEPT; iptables -t nat -A POSTROUTING -o gre-cf -j MASQUERADE
PostDown=iptables -D FORWARD -i %i -j ACCEPT; iptables -D FORWARD -o %i -j ACCEPT; iptables -t nat -D POSTROUTING -o gre-cf -j MASQUERADE
```
