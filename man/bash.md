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
