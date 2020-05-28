# ghostscript / gs

## combine pdfs

```shell
gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -dAutoRotatePages=/None -sOutputFile=output_merged.pdf input1.pdf input2.pdf input3.pdf  
```  

[thanks](https://askubuntu.com/questions/2799/how-to-merge-several-pdf-files)