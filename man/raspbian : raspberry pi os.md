---
date created: Saturday, May 9th 2020, 11:47:02 am
date modified: Saturday, August 12th 2023, 10:58:26 am
tags:
  - raspberrypi
  - rpi
  - 'raspberry pi'
  - 'raspberry pi os'
title: raspbian / raspberry pi os
---

# raspbian / raspberry pi os

## create user for ssh on headless pi

the raspberry pi OS doesn't ship with the `pi` user anymore ([see here for more information and how to create a user](https://www.raspberrypi.com/news/raspberry-pi-bullseye-update-april-2022/)), they have outlined several ways how to create a user. so here's my own copy paste reference for the future when I need a user on a headless pi:

**generate an encrypted password**:

the openssl version which ships by default with macOS doesn't support generating sha512 passwords, so I'm using the homebrew version:

```shell
/opt/homebrew/opt/openssl/bin/openssl passwd -6
```

copy your generated password, and create a new file on the sd card:

```shell
vi /Volumes/bootfs/userconf.txt
```

the contents should look like `username:password`, for example:

```
jonas:$6$WI1IQhq59s3IayNg$h/CZGHz/hlH4ksVgW8mI5kWyZ1vURk3KCFcLajACuIfsUiITYW1zapqC8ov4AHBatpHdpM/uJ5IfSob0y2nBY.
```

## enable ssh on boot / headless login

* [source](https://www.raspberrypi.org/documentation/configuration/wireless/headless.md)

headless login, you know: create a file named `ssh` on the `boot` volume, ex:

```
touch /Volumes/bootfs/ssh
```

## configure wifi

* [source](https://www.raspberrypi.org/documentation/configuration/wireless/headless.md)

same as with ssh, create a file called `wpa_supplicant.conf` in the `boot` volume, like so:

```
/Volumes/bootfs/wpa_supplicant.conf
```

[then go here for the config](/man/wpa_supplicant)
