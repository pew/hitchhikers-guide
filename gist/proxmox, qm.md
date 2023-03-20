---
date created: Monday, March 20th 2023, 6:06:26 am
date modified: Monday, March 20th 2023, 6:08:08 am
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

## modify memory, cpu

set memory in megabytes

```shell
qm set <vmid> -cores <num_cores> -memory <memory_size>
```

## create a clone

- `9000` = source template
- `1337` = new id
- `--full true` might be required if you want to put it onto another storage

```shell
qm clone 9000 1337 --full true --storage storage-name --name vm-name
```
