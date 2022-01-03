# qemu-img

had to use this for ubuntu's multipass, since they don't support resizing yet and default to 5GB disks. Of course, you just figure this out after everything's set up and configured and don't want to be bothered doing everything again.

check out [multipass](/man/multipass/)

## resize a disk

adding 50GB to a disk:

```
sudo apt-get install --no-install-recommends qemu-utils
sudo qemu-img resize ubuntu-20.04-server-cloudimg-amd64.img +50G
```
