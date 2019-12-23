# rbenv / ruby version manager

* [github project](https://github.com/rbenv/rbenv)

## init rbenv

```
eval "$(rbenv init -)"
```

## install ruby version

```
rbenv install 2.6.5
```

## set local or global version

`local` with create a `.ruby-version` file in the current folder. when initializing rbenv it'll use the version.

```
rbenv local 2.6.5
```

global, well, is for the `global` system, or rather for your current logged in user.

```
rbenv global 2.6.5
```

