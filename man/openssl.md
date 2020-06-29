# openssl

## get information / certificate from remote host

```shell
openssl s_client -connect example.com:443
```

**get certs:**

```shell
openssl s_client -connect example.com:443 -showcerts
```

**get fingerprint:**

```shell
openssl s_client -connect example.com:443|openssl x509 -fingerprint -noout
```
