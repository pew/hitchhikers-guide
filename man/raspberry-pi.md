# raspberry pi

[see also raspbian](/man/raspbian : raspberry pi os)

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

## autostart application on boot

this is just another perfect example why linux on a desktop environment is just not ready yet and will never be ready.

create a script to start your application, I put mine in `/usr/local/bin/start_app.sh` with these contents:

```shell
#!/bin/bash
cd /home/pi/Desktop
sleep 10
lxterminal --working-directory='/home/pi/Desktop' --command='python3 application.py' -t 'pos'
sleep 10
exit
```

the *command* part might be the important one for you, for me also the `working-directory` thing was important. make this script executable: `chmod +x /usr/local/bin/start_app.sh`

edit the file `/etc/xdg/lxsession/LXDE-pi/autostart` as root:

```shell
sudo vi /etc/xdg/lxsession/LXDE-pi/autostart
```

and add this line:

```
@lxterminal -e /usr/local/bin/start_app.sh
```

since it's linux, things might work or might not.

[credit](https://raspberrypi.stackexchange.com/a/112365) for all this mess
