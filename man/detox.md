# detox

sanitze file names. yes, you still need this in 2019, even with applications developed in 2019. sad story man, sad story.

it's a 3rd party app you need to install via `brew` or `apt` or what have you, should be available everywhere.

straight from the examples page:

```
detox -s iso8859_1 -r -v -n /tmp/new_files
```

this will go recursively through all directories and sanitize the filenames using the `iso8859_1` sequence, you can also opt for `utf_8` and read more about that [over here](https://linux.die.net/man/5/detoxrc)

remove the `-n` par to actually rename the files, otherwise it's a dry-run. which is always recommended first!

## convert to lowercase

```shell
detox -s lower *
```
