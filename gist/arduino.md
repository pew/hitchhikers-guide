---
date created: Friday, January 6th 2023, 11:29:30 am
date modified: Friday, January 6th 2023, 11:35:44 am
tags:
  - arduino
  - esp32
---

# arduino

## arduino IDE permissions (linux)

If the Arduino IDE is unable to connect to the device, this might help:

**allow writing to the USB device:**

```shell
sudo chmod ugo+w /dev/ttyUSB0
```

**set the right groups:**

```shell
sudo usermod -a -G tty $(whoami)
sudo usermod -a -G dialout $(whoami)
```
