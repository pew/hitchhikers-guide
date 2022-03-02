# Fritz!Box

## test throughput with iperf

... this also works with repeater and other AVM stuff

- open your Fritz!Box web interface and add `/support.lua` to the URL, like so:
    - http://fritz.box/support.lua
    - http://192.168.178.1/support.lua
- search for **iperf** on this site and enable it
- install iperf (2, not 3) on your client and run it like so

```
iperf -c 192.168.178.1 -p4711 -i 1
```

you might want to update the parameters, to keep it running for one minute with a status update ever 5 seconds: 

```
iperf -c 192.168.178.1 -p4711 -t 60 -i 5
```