# lsblk / hard disk information

you can combine most commands, like `NAME,UUID,LABEL`

# get UUID

if you want to set some permanent settings, don't use `/dev/sda` and so on if they change, use the UUID or label.

```
lsblk -o NAME,UUID
```

# get LABEL

```
lsblk -o NAME,LABEL
```
