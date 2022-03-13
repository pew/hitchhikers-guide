# sed

I can't believe it's not butter

## remove all lines except matching one

let's say you've got this file with sha hashes and you want to verify just one file of it (and you're using a version of `sha256sum` which can't just ignore/skip missing files):

```
8edf5e31e28c5e56df3f87334d193cc777f241481ba091930ec53220b01c135d  yt-dlp.exe
e35bc18f766fd61ed46a42913f89680d5ea1d714135898eb6df5cd9248213ccc  yt-dlp_x86.exe
25cc412d1d3c0725a1f2f5b7e4682f6fb40e6d15f7024e96f7afd572e9919535  yt-dlp
ae08e0b56fea59a8bfdadacd92eddc9bdfdc1473199178cb4e31bacfd991864a  yt-dlp.tar.gz
5bd59c0b95740cfd667b12c627b93c0031e1d4e2fbb3e09b7ede293b48757bee  yt-dlp.zip
```

I just want the line containing the `yt-dlp` hash, not the `.zip`, `.tar.gz` etc.


```shell
sed -i '/yt-dlp$/!d' filename.txt
```

## remove after match

example: `foo:1234`, I want to get rid of `:1234`

```shell
echo foo:1234 | sed 's/\:.*//'
```

## remove empty lines

```shell
sed '/^$/d'
```

## append to end of line

I want to add a comma `,` to the end of every line

```shell
sed 's/$/,/'
```
