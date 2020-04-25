# locale(s)

## update locales (debian, ubuntu etc.)

```
sudo update-locale "LANG=en_US.UTF-8"
sudo locale-gen --purge "en_US.UTF-8"
sudo dpkg-reconfigure --frontend noninteractive locales
```

[thx](https://askubuntu.com/a/1027038)
