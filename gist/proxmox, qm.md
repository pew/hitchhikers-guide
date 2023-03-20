---
date created: Monday, March 20th 2023, 6:06:26 am
date modified: Monday, March 20th 2023, 6:11:35 am
tags:
  - qemu
  - qm
  - proxmox
---

# proxmox / qm

## manage vm's

**list vm's:**

```shell
qm list
```

**start / stop qm:**

```shell
qm start 100
qm stop 100
```

## display config

```shell
qm config <id>
```

## modify memory, cpu

set memory in megabytes

```shell
qm set <vmid> -cores <num_cores> -memory <memory_size>
```

## resize disk

you might want to run `qm config <id>` to find the name of the disk controller (`scsi0` in this example)

```shell
qm resize <vmid> scsi0 +500G
```

## create a clone

- `9000` = source template
- `1337` = new id
- `--full true` might be required if you want to put it onto another storage

```shell
qm clone 9000 1337 --full true --storage storage-name --name vm-name
```
