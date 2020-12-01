# raspbian / raspberry pi os

debian for the raspberry pi, they renamed this to **raspberry pi os**

## enable ssh on boot / headless login

* [source](https://www.raspberrypi.org/documentation/configuration/wireless/headless.md)

headless login, you know: create a file named `ssh` on the `boot` volume, ex:

```
touch /Volumes/boot/ssh
```

## configure wifi

* [source](https://www.raspberrypi.org/documentation/configuration/wireless/headless.md)

same as with ssh, create a file called `wpa_supplicant.conf` in the `boot` volume, like so:

```
/Volumes/boot/wpa_supplicant.conf
```

[then go here for the config](/man/wpa_supplicant)
