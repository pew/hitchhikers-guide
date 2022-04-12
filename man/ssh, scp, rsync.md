# ssh / scp / rsync

there's a lot of stuff you can do!

## ssh

### motd (message of the day) for user

create this file with whatever you want to execute when logging in as the user:

```
"$HOME/.ssh/rc"
```

the file `rc` will be *executed* during login, this means if you want to print something out you need to `echo` the contents, like this:

```
if [ ! -t 1 ]; then
    exit
fi
echo "What's up?"
```

[source](https://serverfault.com/a/653405) and [source](https://serverfault.com/a/311463).

### jumphost

this is quite new in openssh, use `-J` to connect to your target host through (multiple) jump host(s):

```
ssh -J user@first-hop user@final-destination # one hop
ssh -J user@first-hop,user@second-hop user@final-destination # two hops to get to 3rd server
ssh -J user@first-hope,user@second-hop:22022 user@final-destination -p2222 # two hops, second hop with custom port, third one as well (check for the : and -p difference... wtf ssh what am I doing wrong?)
ssh -J user@first-hope,user@second-hop:22022 user@final-destination -p2222 -L8384:localhost:8384 # same as above just with port forwarding from the last hop!
```

use a jumphost in `~/.ssh/config`

example: I want to run `ssh nibbler` on my local machine and connect through `bender` to it. *nibbler* is using autossh to connect to *bender* (I hope this makes sense, future Jonas):

```
Host bender
    User local-user
    Hostname bender.hostname.com

Host nibbler
    User root
    Hostname localhost
    Port 2222
    ProxyJump bender
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

### port forwarding in background

with `-fNT` you can do port forwarding and drop the ssh command into the background.

```
ssh user@server -fNT -8080:localhost:8080
```

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

## ssh-keygen

**convert ssh key from openssh format to RFC4716:**

```
ssh-keygen -e -f ~/.ssh/id_rsa.pub | grep -v "Comment:"
```

## scp / rsync

### scp /rsync through extra hosts (middleman)

```shell
scp -J middleman pi@target:file.txt ~/Downloads/
```

we'll connect to the *middleman* with the `-J` flag and custom port `1337` and connect to your `dest` using port `2222`

```
rsync -avxiP -n --delete -e 'ssh -J user@middleman:1337 -p2222' /mnt/ user@dest:/mnt/
```

### rsync exclude muliple folders / directories

… m( - exclude `node_modules` and `dist` folder from rsync

```shell
rsync -avxiP --delete --exclude={node_modules,dist} remote:remote-folder/ ~/awesome/local-folder
```

## poor man's ngrok or make-my-dev-machine-available-from-outside

1. enable `GatewayPorts` in your sshd config:

```
$ grep GatewayPorts /etc/ssh/sshd_config
GatewayPorts yes
```

2. use the `bind_address` feature in ssh to open up the port on the remote machine. we're just going to use `autossh` here. so log in to your *source* machine and execute `autossh` like this:

```
autossh -M 0 -q -f -N -o "ConnectTimeout 10" -o "ServerAliveCountMax 3" -o "ServerAliveInterval 60" -o "Port=22022"  -o "ExitOnForwardFailure=yes" -R2224:localhost:22 tunnel@target-server.com
```

important bit from the man page:

> An empty bind_address, or the address `*'`

3. maybe you need to open up port `2224` (my example) in your firewall on the target-server as well and then you can just connect to your target server using port 2224 like this:

```
ssh -p2224 user@target
```

enjoy!

## do not offer public keys to server

for reasons.

```shell
ssh -o PreferredAuthentications=password -o PubkeyAuthentication=no user@server
```
