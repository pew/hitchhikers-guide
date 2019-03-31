# xfce

## examples

### resize windows

* alt + right click + drag

alternatively, change *window manager* settings theme to something with larger borders

### add application icon to application list

```
exo-desktop-item-edit --create-new ~/.local/share/applications
```

alternatively, put a file like `Firefox.desktop` into `~/.local/share/applications`:

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Firefox
Comment=
Icon=firefox
Exec=/home/chrx/Applications/firefox/firefox-bin
Path=
Terminal=false
StartupNotify=false
```
