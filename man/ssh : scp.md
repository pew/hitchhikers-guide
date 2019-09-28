# ssh / scp

there's a lot of stuff you can do!

## ssh

### jumphost

this is quite new in openssh, use `-J` to connect to your target host through (multiple) jump host(s):

```
ssh -J user@first-hop user@final-destination # one hop
ssh -J user@first-hop,user@second-hop user@final-destination # two hops to get to 3rd server
ssh -J user@first-hope,user@second-hop:22022 user@final-destination -p2222 # two hops, second hop with custom port, third one as well (check for the : and -p difference... wtf ssh what am I doing wrong?)
ssh -J user@first-hope,user@second-hop:22022 user@final-destination -p2222 -L8384:localhost:8384 # same as above just with port forwarding from the last hop!
```

### socks proxy

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


### add / remove passphrase from key

```
ssh-keygen -p
```

### forward credentials to host

```
ssh -A user@host
```

if you need to login through a middle man it might come in handy:

```
ssh -A -t user@middleman ssh -A -t user@target
```

### interactive ssh session

```
[ENTER]
~C
```

forward a port then, for example:

```
-L8080:localhost:8080
```

profit:

```
ssh> -L9090:localhost:9090
Forwarding port.
```

## git-shell

### limit shell (git-shell) to certain users

use-case: you have one user on a linux system and multiple applications / users ssh'ing in. I want to limit the public ssh key of my phone's git client to only be able to use `git-shell` and not be able to login with bash or zsh.

1. put git-shell in `/etc/shells` - [as described here](https://git-scm.com/book/en/v2/Git-on-the-Server-Setting-Up-the-Server)

```
cat /etc/shells   # see if `git-shell` is already in there.  If not...
which git-shell   # make sure git-shell is installed on your system.
sudo -e /etc/shells  # and add the path to git-shell from last command
```

2. limit the public ssh key in `authorized_keys` to only run git-shell

```
command="git shell -c \"$SSH_ORIGINAL_COMMAND\"" ssh-ed25519 AAAAC3NzaC1lZDI1NTE
```

this one key can only use git-shell commands now, like `git clone` but not execute bash or something like that.

## scp

### scp through extra hosts (middleman)

```
ssh -o ProxyCommand='ssh myfirsthop nc -w 10 %h %p' mydestination
scp -o ProxyCommand='ssh middleman nc -w 10 %h %p' admin@target:"~/test/*" .
rsync -avxiP -e "ssh -o ProxyCommand='ssh middleman nc -w 10 %h %p'" admin@target:~/test/ .
```

## poor man's ngrok or make-my-dev-machine-available-from-outside

1. enable `GatewayPorts` in your sshd config:

```
$ grep GatewayPorts /etc/ssh/sshd_config
GatewayPorts yes
```

2. use the `bind_address` feature in ssh to open up the port on the remote machine. we're just going to use `autossh` here. so log in to your *source* machine and execute `autossh` like this:

```
autossh -M 0 -q -f -N -o "ConnectTimeout 10" -o "ServerAliveCountMax 3" -o "ServerAliveInterval 60" -o "Port=22022"  -o "ExitOnForwardFailure=yes" -R0.0.0.0:2224:localhost:22 tunnel@target-server.com
```

see the `-R0.0.0.0` part? that's the important one and together with `GatewayPorts` enabled in `sshd_config` ssh will also allow you to do that.

3. maybe you need to open up port `2224` (my example) in your firewall on the target-server as well and then you can just connect to your target server using port 2224 like this:

```
ssh -p2224 user@target
```

enjoy!
