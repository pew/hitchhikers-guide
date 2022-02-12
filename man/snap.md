# snap

## update snap packages

```
sudo snap refresh
```

## manage snap packages with systemd / systemctl

... things like restart, start and stop. They're prefixed with `snap.`, so do this:

```
systemctl status snap.multipass.multipassd.service
```

