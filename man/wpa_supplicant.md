# wpa_supplicant

configure wifi on linux, it's super annoying

## configure wifi network(s)

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

you can add more `network={}` blocks for additional wifi networks
