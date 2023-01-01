---
date created: Saturday, September 17th 2022, 6:56:10 am
date modified: Sunday, January 1st 2023, 10:47:12 am
tags:
  - password
  - secrets
---

# password generator

xkcd style:

```shell
python -c 'import secrets;f=open("/usr/share/dict/words");words=[word.strip() for word in f];password = "-".join(secrets.choice(words) for i in range(4));print(password)'
```

random:

```shell
python -c 'import secrets;print(secrets.token_hex(32))'
```

[it's-like-awesome-you-know](https://docs.python.org/3/library/secrets.html)

if you want to pipe this into something like `pbcopy` to have it directly in your clipboard, do something like this to avoid a newline:

```shell
echo -n $(python -c 'import secrets;f=open("/usr/share/dict/words");words=[word.strip() for word in f];password = "-".join(secrets.choice(words) for i in range(4));print(password)') | pbcopy
```
