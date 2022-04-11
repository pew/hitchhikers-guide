# ethtool - wake on lan

## enable wake on lan

check if wake on lan (wol) is supported:

```shell
ethtool enp0s31f6 # or another interface name
```

if you see `pumbg` it apparently means that it is supported, but the `d` in the `Wake-on` line says it's disabled.

```shell
Supports Wake-on: pumbg
Wake-on: d
```

If it's not supported, you might want to check your bios settings.

**enable wake on lan**:

```shell
ethtool -s enp0s31f6 wol g
```

## wake a system

install `wakeonlan` on a client system, get the mac address of the environment you want to wake up and run:

```shell
wakeonlan mac-address-here
```
