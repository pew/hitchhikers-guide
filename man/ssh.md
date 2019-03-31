# ssh

there's a lot of stuff you can do!

# jumphost

this is quite new in openssh, use `-J` to connect to your target host through (multiple) jump host(s):

```
ssh -J user@first-hop user@final-destination
ssh -J user@first-hop,user@second-hop user@final-destination
```

# socks proxy

create a socks proxy, route traffic using the proxy encrypted through your destination host:

```
ssh tunnel@server -NT -D 127.0.0.1:8080
```

now configure your browser/client to use `localhost` with port `8080` using a *socks5* proxy.

to drop the whole thing into the background:

```
ssh tunnel@server -NTf -D 127.0.0.1:8080
```

if you put it in the background you might want to consider autossh (see `autossh.md`).


# add / remove passphrase from key

```
ssh-keygen -p
```

# forward credentials to host

```
ssh -A user@host
```

if you need to login through a middle man it might come in handy:

```
ssh -A -t user@middleman ssh -A -t user@target
```

# interactive ssh session

```
[ENTER]
~C
```