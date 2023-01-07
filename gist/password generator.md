---
date created: Saturday, September 17th 2022, 6:56:10 am
date modified: Saturday, January 7th 2023, 11:40:46 am
tags:
  - password
  - secrets
  - pwgen
---

# password generator

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

## others

- pwgen
