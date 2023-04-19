---
tags:
  - openssl
  - certificate
date created: Monday, June 29th 2020, 6:10:02 am
date modified: Monday, August 29th 2022, 5:57:56 am
---

# openssl

## get information / certificate from remote host

```shell
openssl s_client -connect example.com:443
```

## view certificate ... locally

```shell
openssl x509 -in cert.pem -text
```

## extract certificates

**without SNI:**

```shell
openssl s_client -connect example.com:443 -showcerts
```

**with SNI:**

```shell
openssl s_client -servername example.com -connect example.com:443 2>/dev/null </dev/null |  openssl x509 -outform pem
```

## extract fingerprint

```shell
openssl s_client -connect example.com:443|openssl x509 -fingerprint -noout
```

## remove password / passphrase from certificate

```shell
openssl rsa -in name.key -out name.key
```
