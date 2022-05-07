---
tags: 
date created: Saturday, May 7th 2022, 6:45:21 am
date modified: Saturday, May 7th 2022, 6:49:28 am
title: picocom
---

# picocom

[picocom - minimal dumb-terminal emulation program](https://linux.die.net/man/8/picocom)

You can use this to connect to an ESP32 chip and so on via USB.

## connect to a USB Device

you need to set the baud rate with `-b`, depending on your device.

```shell
picocom /dev/ttyUSB0 -b115200
```

### Cannot open /dev/ttyS0 or /dev/ttyUSB0: Permission denied

if you get that on your system, you need to add your user to the `dialout` group (at least on debian/ubuntu)

```shell
sudo usermod -a -G dialout $(whoami)
```

## exit picocom

felt like using Vim for the first time, but I just didn't read the help 🤷‍♂️

```shell
ctrl + a + x
```
