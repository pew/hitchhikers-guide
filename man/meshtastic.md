# meshtastic

this is a work in progress, probably forever.

## get info

```
meshtastic --info
```

## basic configuration

**set region, modem config and id + channel**

```
meshtastic --set region EU433
meshtastic --ch-set modem_config Bw125Cr48Sf4096 --ch-index 0
meshtastic --ch-set id 4422 --ch-index 0
meshtastic --ch-set name h0mer --ch-index 0
```

**encrypt communication with random key**

```
meshtastic --ch-set psk random --ch-index 0
```

## set transmission (speed? and range?)

```
meshtastic --ch-longfast
```

## send message

```
meshtastic --sendtext hello1
```

## export / import config

that's what I did to put the same config on multiple devices, chats did work afterwards. not sure about any implications...

```
meshtastic --export-config > config.yml # export
meshtastic --configuration config.yml	# import
```
