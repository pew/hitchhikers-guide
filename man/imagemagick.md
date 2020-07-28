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

the background color can be specified like so:

```shell
-color blue
-color "#ddddff"
-color "rgb(255,255,255)"
```