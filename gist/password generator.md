# password generator

```shell
python -c 'import secrets;f=open("/usr/share/dict/words");words=[word.strip() for word in f];password = "-".join(secrets.choice(words) for i in range(4));print(password)'
```

[it's-like-awesome-you-know!]([url](https://docs.python.org/3/library/secrets.html))
