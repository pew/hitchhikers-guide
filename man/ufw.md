# ufw - uncomplicated firewall

well, still too complicated from time to time for me. so let's write it down. see also [iptables](/man/iptables) - or check the [ubuntu wiki](https://help.ubuntu.com/community/UFW)

## enable / disable ufw

```
ufw enable
ufw disable
```

## manage rules

### list rules

```
ufw status # simple list
ufw status numbered # numbered list, so you can also delete rules
ufw status verbose # some more info, no numbers
```

### delete rules

```
ufw delete N # where N is the number from the list command above
```

## allow application / port

```shell
ufw allow openssh
ufw allow 22
ufw allow from 1.2.3.4 to any port 22 # allow from 1.2.3.4 port 22
ufw allow from 1.2.3.4 to any port 22 proto tcp # allow from 1.2.3.4 port 22, tcp
```

## deny application / port

```shell
ufw deny from 1.2.3.4
```
