# system profiler / system_profiler

system_profiler – reports system hardware and software configuration.

## get connected Wi-Fi SSID name

I hope there's a better way? [thank you](https://discussions.apple.com/thread/255778674?answerId=260793906022&sortBy=rank#260793906022)

```shell
system_profiler SPAirPortDataType | awk '/Current Network/ {getline;$1=$1;print $0 | "tr -d ':'";exit}'
```
