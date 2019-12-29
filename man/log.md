# log / syslog

I run these commands on macOS.

## get sleep wake reasons and times:

from the past 12 hours. check the man page for more information: `man log`

you can do things like ``--last 2d` for days and so on.

```
log show --last 12h --style syslog | fgrep "[powerd:sleepWake]"
```
