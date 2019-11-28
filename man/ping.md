# ping

well, it's not actually about ping right now but what to do when `ping` is not available

## if there's no ping, nc, telnet available

like in a container, do this (but you need bash, heh):

```
(echo >/dev/tcp/${host}/${port}) &>/dev/null && echo "open" || echo "closed"
```

example:

```
(echo >/dev/tcp/8.8.8.8/53) &>/dev/null && echo "open" || echo "closed"
```

[source](https://serverfault.com/a/923193)

