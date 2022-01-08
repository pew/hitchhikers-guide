# locale(s)

## update locales (debian, ubuntu etc.)

2020.. nvmd. I'm sure this will never ever work for all the systems.

```
LANG=en_US.UTF-8 sudo sed -i -e "s/# $LANG.*/$LANG.UTF-8 UTF-8/" /etc/locale.gen
LANG=en_US.UTF-8 sudo dpkg-reconfigure --frontend=noninteractive locales
LANG=en_US.UTF-8 sudo update-locale LANG=$LANG
```

## update locales, including things like raspberry pi os

… it'll probably not work in some other edge cases. this is one of the million reasons why linux will never be on the desktop

```
echo -e 'LANG="en_US.UTF-8"\nLANGUAGE="en_US:en"\n' | sudo tee /etc/default/locale
sudo sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen
sudo dpkg-reconfigure --frontend=noninteractive locales
# sudo locale-gen --purge en_US.UTF-8
sudo update-locale LANG=en_US.UTF-8
```

## update your ssh session as well

```
sudo sed -e '/SendEnv/ s/^#*/#/' -i /etc/ssh/ssh_config
```