# avahi

zero-config, bonjour

## samba finder macos sidebar icon

get rid of the question mark and replace it with a mac, create `/etc/avahi/services/smb.service`:

```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
 <name replace-wildcards="yes">%h</name>
 <service>
   <type>_smb._tcp</type>
   <port>445</port>
 </service>
 <service>
   <type>_device-info._tcp</type>
   <port>0</port>
   <txt-record>model=RackMac</txt-record>
 </service>
</service-group>
```

[source](https://unix.stackexchange.com/questions/93684/setting-up-samba-netatalk-and-avahi-bonjour-on-raspberry-pi)
