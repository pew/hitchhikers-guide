# hdparm

configure some settings for hard drives, like hibernation/standby/idle

# set idle / standby timeout

the documentation is super confusing about this, here's a way to set it to 3 minutes:

```
sudo hdparm -S 36 /dev/disk/by-uuid/48ae93d7-b351-4d05-b177-db22a4a8g4dd
```

get the UUID beforehand (`lsblk -o NAME,UUID`)

please, please check the `man` page of `hdparm` if absolutely necessary.

# make permanent settings hdparm

so they persist during a reboot of the system, edit `/etc/hdparm.conf`:

```
/dev/sda {
        spindown_time = 36
}
```
