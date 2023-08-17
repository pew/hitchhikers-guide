---
date created: Sunday, November 10th 2019, 6:18:57 am
date modified: Thursday, August 17th 2023, 5:44:22 am
tags:
  - macos
---

# macos

let's start with some random stuff before we split this apart.

## sleep issues

### find out why macos woke up

```
pmset -g log|egrep " Sleep | Wake | DarkWake "
pmset -g log | egrep '\b(Sleep|Wake|Start)\s{2,}'
pmset -g log | grep "Wake Requests"
```

that's from a comment [here](https://apple.stackexchange.com/questions/52064/how-to-find-out-the-start-time-of-last-sleep#comment259571_84162)

### prevent wakeups

```shell
sudo pmset -a powernap 0 # disable powernap
sudo pmset -a tcpkeepalive 0 # disable networking (prevents find my mac from working)
sudo pmset -a proximitywake 0 # wake from sleep based on proximity of devices using same iCloud id
```

see, verify and check your settings:

```shell
pmset -g
```

## import private key into keychain

```
security import cert.key -k ~/Library/Keychains/login.keychain-db
```
