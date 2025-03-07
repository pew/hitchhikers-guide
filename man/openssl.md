---
tags:
  - openssl
  - certificate
date created: Monday, June 29th 2020, 6:10:02 am
date modified: Monday, August 29th 2022, 5:57:56 am
---

# openssl

## read certificate

**remote host:**

```shell
openssl s_client -connect example.com:443
```

**from file:**

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

## display public key size

```shell
openssl s_client -connect google.com:443 </dev/null 2>/dev/null | openssl x509 -text -noout | grep -i "public-key"
```

## extract fingerprint

```shell
openssl s_client -connect example.com:443|openssl x509 -fingerprint -noout
```

## remove password / passphrase from certificate

```shell
openssl rsa -in name.key -out name.key
```

## display subject / common name

```shell
openssl x509 -noout -subject -in name.crt
```

subject= /CN=foo.example.com
