# bash

## iterate through array

```shell
ARRAY=(a b c)
for a in "${ARRAY[*]}"; do echo "$a";done
```

address an array by index directly:

```shell
echo ${ARRAY[2]}
```

output will be `b`

## escape strings

```shell
echo "text with spaces & special characters" | bash -c 'printf "%q" "$(cat)"'; echo
```

will output this: `text\ with\ spaces\ \&\ special\ characters`, now you can go ahead and use it in a script or something like that.

found this somewhere in [here](https://news.ycombinator.com/item?id=24659282)