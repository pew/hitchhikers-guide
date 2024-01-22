# imagemagick

install imagemagick, for example with brew:

```shell
brew install imagemagick
```

## resize and keep aspect ratio

`mogrify` can also overwrite existing files and do edits inline

resize on *width*:

```shell
magick mogrify -geometry 256x *.png
```

resize on *height*:

```shell
magick mogrify -geometry x256 *.png
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

## animated webp to gif

```shell
magick mogrify -format gif filename.webp
```

[source](https://superuser.com/a/1795252)

## image to c array

useful if you're going crazy with some cool e-paper/e-ink displays and an esp32.

```
magick img.bmp img.h
```

## merge multiple images / screenshots

you can play around with the `-tile` option to position them next to each other ... like tiles you know.

```
montage -mode concatenate -tile 1x image-*.png out.jpg
```

merge them **vertically**:

```shell
magick input1.png input2.png +append output.png
```

or **horizontally:**

```shell
magick input1.png input2.png -append output.png
```

**align them** using `gravity`

if you have multiple sizes and you want them aligned in the center:

```shell
convert 1.png 2.png -gravity center -append great.png
```
