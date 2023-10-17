---
date created: Saturday, March 23rd 2019, 2:02:05 pm
date modified: Tuesday, October 17th 2023, 12:27:05 pm
tags:
  - awk
---

# awk

yeah, command line utils!

## prepend before each line

input:

```
a
b
c
```

what you want:

```
* a
* b
* c
```

how to achieve this:

```
cat input | awk '{print "* " $0;}'
```

## get odd and even lines

even:

```shell
echo $text | NR%2==0
```

odd:

```shell
echo $text | NR%2==1
```

## cut / skip line

```shell
awk 'NR>1' # start after 1st line, use 2, 3 etc.
awk 'NR>1 {print $1}'
```
