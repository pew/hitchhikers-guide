## dd

### copy an image to an sd card

I'm using `gdd` here, this requires the homebrew package `coreutils` on a mac. `dd` might also just work on your system.

copy a raspberry pi os image to an sd card:

```
sudo gdd if=2021-05-07-raspios-buster-armhf.img of=/dev/rdisk4 bs=32M conv=fsync status=progress
```
