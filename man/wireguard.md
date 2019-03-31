# wireguard

* [awesome quick'not'dirty vpn solution](https://www.wireguard.com)

I'm using it with https://github.com/trailofbits/algo/ so it's super easy to do

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
