# raspberry pi

[see also raspbian](/man/raspbian)

## disable wifi / bluetooth

add the following to `/boot/config.txt`

```
dtoverlay=disable-wifi
dtoverlay=disable-bt
```

## cpu governor

change to performance, this won't reset during a reboot of the system. if you want this permanently set to `performance` or something else, you might want to edit `/etc/rc.local`

```
echo performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

## cpu temperature

```
vcgencmd measure_temp
```

## read-only sd card

when running updates, don't forget to make the filesystems read write:

```
sudo mount -o remount,rw /
sudo mount -o remount,rw /boot
```

and afterwards, read only again:

```
sudo mount -o remount,ro /
sudo mount -o remount,ro /boot
```

## disable onboarding screen for configuration

when using the desktop version of raspbian / raspberry pi os but the system has already been configured

```
sudo rm /etc/xdg/autostart/piwiz.desktop
```

## disable mouse cursor on touch screens

* open `/etc/lightdm/lightdm.conf`
* find `xserver-command` in the `[Seat` section of the file, edit like so:

```
xserver-command=X -nocursor
```

