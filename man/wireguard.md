# wireguard

* [awesome quick'not'dirty vpn solution](https://www.wireguard.com)

I'm using it with https://github.com/trailofbits/algo/ so it's super easy to do

## route wireguard traffic through another interface

assume that you have multiple network interfaces on a server and want to use wireguards outgoing traffic to go such one, add the following to your interface config in `/etc/wireguard/wg0.conf`. in this case it's `gre-cf`

```
[Interface]
Address = 10.0.0.1/24
ListenPort = 51820
PostUp=iptables -A FORWARD -i %i -j ACCEPT; iptables -A FORWARD -o %i -j ACCEPT; iptables -t nat -A POSTROUTING -o gre-cf -j MASQUERADE
PostDown=iptables -D FORWARD -i %i -j ACCEPT; iptables -D FORWARD -o %i -j ACCEPT; iptables -t nat -D POSTROUTING -o gre-cf -j MASQUERADE
```

# macOS installation

```
brew install wireguard-tools
mkdir /usr/local/etc/wireguard/
cp algo.conf /usr/local/etc/wireguard/wg0.conf
```

**connect**:

```
sudo wg-quick up wg0
```

**disconnect**:

```
sudo wg-quick down wg0
```
