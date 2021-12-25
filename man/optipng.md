# optipng

optimize png (and bmp, gif, pnm or tiff) images, install with `apt-get install optipng`

## default usage

this will override the current file and save it with the default settings. this usually works best for me

```
optipng input.png
```

## maximum optimization

you can do `-o2` to `-o7` (check the man page for any updates and changes etc.)

```
optipng -o7 input.png
```
