# home-assistant / hass.io

quite cool.

# update

if installed on a raspberry pi through pip and the official documentation:

```
sudo -u homeassistant -H -s
cd /srv/homeassistant/
source bin/activate
pip3 install --upgrade homeassistant
exit
sudo systemctl restart home-assistant@homeassistant.service
```

yes, you can and should optimize this by just using docker images which they provide now.
