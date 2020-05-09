# locale(s)

## update locales (debian, ubuntu etc.)

2020.. nvmd

```
LANG=en_US-UTF-8 sudo sed -i -e "s/# $LANG.*/$LANG.UTF-8 UTF-8/" /etc/locale.gen
LANG=en_US-UTF-8 sudo dpkg-reconfigure --frontend=noninteractive locales
LANG=en_US-UTF-8 sudo update-locale LANG=$LANG
```