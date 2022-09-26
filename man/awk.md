---
date created: Saturday, March 23rd 2019, 2:02:05 pm
date modified: Monday, September 26th 2022, 6:40:35 am
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
