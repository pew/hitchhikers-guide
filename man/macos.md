# macos

let's start with some random stuff before we split this apart.

## find out why macos woke up

```
pmset -g log|egrep " Sleep | Wake | DarkWake "
pmset -g log | egrep '\b(Sleep|Wake|Start)\s{2,}'
```

that's from a comment [here](https://apple.stackexchange.com/questions/52064/how-to-find-out-the-start-time-of-last-sleep#comment259571_84162)


## import private key into keychain

```
security import cert.key -k ~/Library/Keychains/login.keychain-db
```
