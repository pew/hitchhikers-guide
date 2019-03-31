# awk

yeah, command line utils!

# prepend before each line

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
