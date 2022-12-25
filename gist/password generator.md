---
date created: Saturday, September 17th 2022, 6:56:10 am
date modified: Sunday, December 25th 2022, 10:15:00 am
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
