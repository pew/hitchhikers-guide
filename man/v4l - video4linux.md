# v4l  - video4linux

## list video devices

```shell
v4l2-ctl --list-devices
```

## get details of a device

this will tell you the available frame rate and other things.

```shell
sudo v4l2-ctl --device=/dev/video0 --all
```

or just run:

```shell
sudo v4l2-ctl --all
```

## find capture capabilities

…so you know which resolution you can stream at:

```
sudo v4l2-ctl -d /dev/video0 --list-formats-ext
```
