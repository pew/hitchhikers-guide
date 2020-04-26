# apt / apt-get

the tool to manage debian / ubuntu packages, I always forget some commands, so let put them here.

## version provided by repository

especially important for debian since all packages are always outdated by 10 years:

```
apt-cache policy irssi
```

## find package for filename / executable

you want to run `ping` but you have no idea which package provides `ping`:

```
apt-get install apt-file
apt-file update
```

then do something like

```
apt-file search ping
# or
apt-file search /bin/ping
```
