# cpupower

get information about current cpu usage/frequency and so on.

```
cpupower frequency-info
```

## change cpu clock speed

max power save (performance bias). this goes from 0 to 15 where 0 is for most performance and 15 for most power saving:

```
sudo cpupower set -b 15
```

verify if it was set correctly with `sudo cpupower -c all info -b`

**set fixed cpu frequency:**

```
sudo cpupower frequency-set --max 2000 MHz
```

**get available cpu governors:**

```
sudo cpupower frequency-info -g
```

**set specific cpu governor**

`-c all` will apply the governor to all cpus

```
sudo cpupower -c all frequency-set -g powersave
```
