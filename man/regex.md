# regex

I just can't get over it, it's too hard for me.

## match everything after match

the `libexec` part here is for macOS, you need gnu grep to do `-P`

```
/usr/local/opt/grep/libexec/gnubin/grep -oP '/repos/\K.*'
```

this will match everything after `repos/`, the `K` is important here. the `.*` says that it should match everything afterwards.
