---
date created: Saturday, September 17th 2022, 6:56:10 am
date modified: Saturday, March 15th 2025, 9:41:58 am
tags:
  - password
  - secrets
  - pwgen
---

# password generator

## openssl

```shell
openssl rand -hex 32
```

## python

xkcd style:

```shell
python -c 'import secrets;import string;f=open("/usr/share/dict/words");words=[word.strip().title() for word in f];digits=string.digits;password = "-".join(secrets.choice(words) for i in range(4)) + "_" + "".join(secrets.choice(digits) for i in range(3));print(password)'
```

random:

```shell
python -c 'import secrets;print(secrets.token_hex(32))'
```

if you want to pipe this into something like `pbcopy` to have it directly in your clipboard, do something like this to avoid a newline:

```shell
echo -n $(python -c 'import secrets;import string;f=open("/usr/share/dict/words");words=[word.strip().title() for word in f];digits=string.digits;password = "-".join(secrets.choice(words) for i in range(4)) + "_" + "".join(secrets.choice(digits) for i in range(3));print(password)') | pbcopy
```

[you might want to check the official python docs](https://docs.python.org/3/library/secrets.html#recipes-and-best-practices).

## gpg

```shell
gpg --gen-random --armor 2 30
```

## /dev/urandom

```shell
LC_ALL=C tr -cd '[:graph:]' < /dev/urandom | head -c23
```

## others

- pwgen
