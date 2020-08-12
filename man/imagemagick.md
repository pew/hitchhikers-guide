# imagemagick

install imagemagick, for example with brew:

```shell
brew install imagemagick
```

## svg to png

use `convert` to create a png out of a svg file

```shell
convert -background none -size 400x380 input.svg output.png
```

you can omit the `-size` as well

the background color can be specified like so:

```shell
-color blue
-color "#ddddff"
-color "rgb(255,255,255)"
```

## png to svg

```
convert input.png output.svg
```

if you get an error like:

```
convert: delegate failed `'potrace' --svg --output
```

install `potrace`:

```
brew install potrace
```

and you should be good to go