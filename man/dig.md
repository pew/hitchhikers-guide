# dig

- [see also DNS](/man/dns)

## digrc

customize your `dig` output with a config file. Create the file `~/.digrc` for this, and add the following:

```
+noall +answer
```

the above will only show the answer, like so:

```
$ dig man.ilayk.com
man.ilayk.com.		300	IN	CNAME	hitchhikers-builder.pages.dev.
hitchhikers-builder.pages.dev. 300 IN	A	172.66.46.211
hitchhikers-builder.pages.dev. 300 IN	A	172.66.45.45
```
