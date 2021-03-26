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

## pin version

sometimes you want or need to *pin* a package to a specific version since it'll break everything. looking at you, docker. this happened twice already.

```
vi /etc/apt/preferences.d/docker
Package: docker-ce
Pin: version 5:20.10.4~3-0~ubuntu-focal
Pin-Priority: 900
```

this will pin the package `docker-ce` to version `5:20.10.4~3-0~ubuntu-focal` by using a high priority of 900, the default is usually 500.

You can check the package priority with the `apt-cache policy` command ([see above](#version%20provided%20by%20repository)) to adjust the priority, but why not stick to 900. or over 9000.