# (socks) proxy

sometimes you just need it!

# provide a socks proxy

this is how you provide a socks proxy, or create one. below you can find some instructions how to consume or use this proxy.

## socks5 proxy ssh

```
ssh tunnel@server -NT -D 127.0.0.1:8080
```

drop it in the background:

```
ssh tunnel@server -NTf -D 127.0.0.1:8080
```

this will expose an socks proxy on your local system using port 8080. if you replace `127.0.0.1` with `*` everyone can connect to your machine using this proxy

## socks5 proxy autossh

autossh will ensure that the ssh proxy is up all the time even when the connection drops

### basic example

this will expose a socks5 proxy on port 8081.

```
autossh -M 0 -q -f -N user@server -D 8081 -o "ConnectTimeout 10" -o "ServerAliveCountMax 3" -o "ServerAliveInterval 60" -o "ExitOnForwardFailure=yes"
```

### more advanced example with reverse tunnel

this will expose a socks5 proxy on port 8081, bound to the local ip address of the device (`192.168.178.21`) so it can be used by other systems on the network. this one is running on a raspberry pi, available to all other devices at home.

it also exposes a reverse tunnel on the machine it's connecting to using port `2222`, meaning, when I'm on the host machine (`server`) I can ssh into my raspberry pi like so: `ssh -p2222 pi@localhost` to end up on my pi. this is great if you're behind some stupid carrier grade nat.

```
autossh -M 0 -q -f -N -o "ConnectTimeout 10" -o "ServerAliveCountMax 3" -o "ServerAliveInterval 60" -o "Port=22022" -o "ExitOnForwardFailure=yes" -R2222:localhost:22 -D192.168.178.21:8081 tunnel@server
```

# use a socks proxy

## system wide

usually there's a system setting on your machine to use a socks proxy, just enter the ip address (either `127.0.0.1` or the one of your proxy device like the raspberry pi `192.168.178.21`) followed by the port (`8081`) and you're good to go.

## browsers

some browsers use the system settings, some don't. firefox doesn't, so you need to go into the firefox settings to set a socks proxy. for (google) chrome there's an extension like [Proxy SwitchyOmega](https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif) to have a proxy set just for the chrome browser

## terminal / shell

if you want to use the proxy in a terminal with other tools like curl, you need to expose / set the environment variables `http_proxy` and `https_proxy`

```
export http_proxy="socks5://192.168.178.21:8081"
export https_proxy=$http_proxy
```

then you can do things like: `curl icanhazip.com` and it'll use the proxy. make sure that this is not permanent, if you need this permanent it needs to be placed into your `.zshrc` or `.bashrc` file

there are also tools like **tsocks** which I haven't used yet or **sshuttle**

there's also other software out there which could help with a somewhat *syste-mwide* proxy or a poor mans vpn:

* sshuttle
* tsocks
* proxychains
* proxychains-ng
