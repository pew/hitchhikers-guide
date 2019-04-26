# irssi

irc!

# ignore / unignore join part quit etc.

ignore `JOIN`, `PART` and quit in channel messages etc. for every channel:

```
/ignore * JOINS PARTS QUITS MODES
```

**list ignore**:

```
/ignore
```

**unignore**:

remove something/someone from your ignore list. get the number first with `/ignore`, then:

```
/unignore 1
```

# change time zone

if your server is running UTC and you want irssi in your local time zone:

```
/script exec $ENV{'TZ'}='Europe/Berlin'
```

# fish

I'm using [this fish plugin right now](https://github.com/falsovsky/FiSH-irssi)

* check requirements and install them according to docs linked above

if you're not using the irssi version provided with your distribution, you'll run into errors like:

> fish/core is ABI version 0 but Irssi is version 7, cannot load

the fix for this: use the irssi sources of the irssi version you're using, I'm on 1.2.0 at the time of this writing.

given you're in `$HOME/tmp`:

```
wget -O- https://github.com/irssi/irssi/releases/download/1.2.0/irssi-1.2.0.tar.gz | tar xzf - # download and extract source
cmake -DIRSSI_INCLUDE_PATH=$HOME/tmp/irssi-1.2.0 # configure cmake to use the new irssi sources
make # build it!
cp src/libfish.so ~/.irssi/libfish.so # copy the plugin to your local user folder
```

in irssi, load the plugin:

```
/load /home/jonas/.irssi/libfish.so
```

load at startup:

```
echo "/load /home/jonas/.irssi/libfish.so" >> $HOME/.irssi/startup
```
