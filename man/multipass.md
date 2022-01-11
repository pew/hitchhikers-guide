# multipass

learn more about [multipass here](https://multipass.run) to run VMs easily

## instance storage location

```
/var/snap/multipass/common/data/multipassd/vault/instances/
```

## unable to start / stop multipass VM

... it might run into a timeout, just doesn't do anything and there's no real output for anyone even with the `-vvv` flag. This happened multiple times for me and I don't feel good about multipass. But hey, I also don't want to switch to anything else right now. What to do when you can't start or stop or interact with the VM.

I got most of this from this good [github issue here](https://github.com/canonical/multipass/issues/2371#issuecomment-989035709)


**disable multipass:**

```
sudo snap disable multipass
```

check for a **snapshot**, it's hopefully called *suspended*, you want to update the last bit of the path probably (`your-instance-name` and maybe the image as well)

```
sudo qemu-img snapshot -l /var/snap/multipass/common/data/multipassd/vault/instances/your-instance-name/ubuntu-20.04-server-cloudimg-amd64.img
```

delete the *suspend* snapshot:

```
sudo qemu-img snapshot -d /var/snap/multipass/common/data/multipassd/vault/instances/your-instance-name/ubuntu-20.04-server-cloudimg-amd64.img
```

**re-enable** multipass:

```
sudo snap enable multipass
```

**start** your vm:

```
sudo multipass start <name>
```