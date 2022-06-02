# inkscape

I think it's better than [imagemagick](/man/imagemagick/) for some tasks, especially converting svg to png.

## convert svg to png

had a lot of trouble with imagemagick, the [internet seems to agree](https://stackoverflow.com/a/14174624)

```shell
inkscape -w 512 -h 512 input.svg -o output.png
```
