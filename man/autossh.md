# autossh

use autossh to create ssh tunnel/proxy services permanently, autossh will automatically reconnect if the connection drops. good to get into remote systems when they're not available from the outside and might shut down at any time (as everything can and does!)

# reverse tunnel

```
autossh -M 0 -q -f -N -o "ConnectTimeout 10" -o "ServerAliveCountMax 3" -o "ServerAliveInterval 60" -o "Port=22022" -o "ExitOnForwardFailure=yes" -R2222:localhost:22 tunnel@target
```

this will connect to `target` using port `22022` (remove this for default 22) and creates a reverse tunnel (`-R`) on port `2222` on `target` to `22` on `localhost`. 

meaning when you connect to `target` you can `ssh` to localhost on port `2222` to end up on the device executing autossh.

how to connect:

1. connect to `target`
2. `ssh -p2222 user@localhost`
3. profit

# permanent socks proxy

```
autossh -M 0 -q -f -N -o "ConnectTimeout 10" -o "ServerAliveCountMax 3" -o "ServerAliveInterval 60" -o "Port=22022" -o "ExitOnForwardFailure=yes" -D192.168.178.22:8081 tunnel@target
```

this will connect to `target` and by using `-D192.168.178.22:8081` will provide a socks proxy on the whole interface running on `192.168.178.22` port `8081` (so everyone can use it, otherwise replace this with `127.0.0.1` for local usage only.

you can now configure your cliencts in your (home) network to use `192.168.178.22` with port `8081` as a socks5 proxy to route traffic through `target`