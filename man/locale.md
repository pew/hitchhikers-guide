# locale(s)

## update locales (debian, ubuntu etc.)

2020.. nvmd. I'm sure this will never ever work for all the systems.

```
LANG=en_US.UTF-8 sudo sed -i -e "s/# $LANG.*/$LANG.UTF-8 UTF-8/" /etc/locale.gen
LANG=en_US.UTF-8 sudo dpkg-reconfigure --frontend=noninteractive locales
LANG=en_US.UTF-8 sudo update-locale LANG=$LANG
```

## update your ssh session as well

```
sudo sed -e '/SendEnv/ s/^#*/#/' -i /etc/ssh/ssh_config
```