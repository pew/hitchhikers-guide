---
title: utm
tags:
  - utm
  - qemu
  - qcow2
date created: 2022-11-15
---

# utm

[https://getutm.app/](https://getutm.app/)

## use qcow2 images in UTM

- Create a new VM, select *other* when picking the operating system
- Tick the *Skip ISO boot* option
- Open the VM settings, in the sidebar under *QEMU*, disable *UEFI Boot*
- Still in settings, remove the existing hard drive, add another one and select your qcow2 file
