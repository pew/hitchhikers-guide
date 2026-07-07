---
date created: Monday, March 20th 2023, 6:06:26 am
date modified: Tuesday, July 7th 2026, 11:42:44 am
tags:
  - qemu
  - qm
  - proxmox
  - linux
---

# proxmox / qm

## manage virtual machines (vms)

**list vm's:**

```shell
qm list
```

**start / stop qm:**

```shell
qm start <VMID>
qm shutdown <VMID>
qm reboot <VMID>
qm stop <VMID>
```

### display / get config

```shell
qm config <id>
```

### modify memory, cpu

set memory in megabytes

```shell
qm set <vmid> -cores <num_cores> -memory <memory_size>
```

### resize disk

you might want to run `qm config <id>` to find the name of the disk controller (`scsi0` in this example)

```shell
qm resize <vmid> scsi0 +500G
```

### create a clone

- `9000` = source template
- `1337` = new id
- `--full true` might be required if you want to put it onto another storage

```shell
qm clone 9000 1337 --full true --storage storage-name --name vm-name
```

## open vm console / display

### serial console

```shell
qm terminal <VMID>
```

This only works if the guest has a serial console configured. Try:

```shell
qm set <VMID> --serial0 socket --vga serial0
```

**exit serial console**

```shell
Ctrl+O
```

then

```shell
q
```

## log in to a VM

Find the IP via guest agent:

```shell
qm guest cmd <VMID> network-get-interfaces
```

Requires QEMU guest agent installed and enabled.

Enable guest agent in Proxmox:

```shell
qm set <VMID> --agent enabled=1
```

inside Debian/Ubuntu VM:

```shell
sudo apt install qemu-guest-agent
sudo systemctl enable --now qemu-guest-agent
```
