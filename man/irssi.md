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