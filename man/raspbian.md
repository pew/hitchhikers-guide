# raspbian

debian for the raspberry pi

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

and edit it with your own wifi credentials and ssid:

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=<Insert 2 letter ISO 3166-1 country code here>

network={
 ssid="<Name of your wireless LAN>"
 psk="<Password for your wireless LAN>"
}
```

