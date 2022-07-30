# tr

## strip newline from input

If you do this and paste it afterwards, it'll add a newline or will even be used as *return* in some forms:

```
head -c 32 /dev/urandom|base64|pbcopy
```

**strip the newline**

do it like this, `tr -d '\n'` is the key:

```
head -c 32 /dev/urandom|base64|tr -d '\n'|pbcopy
```

## replace newline with comma

```shell
tr '\n' ','
```
