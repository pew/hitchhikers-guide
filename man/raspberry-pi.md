# raspberry pi

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
