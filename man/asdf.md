# asdf

version manager for all the things programming and things like that. python, node, ruby, [read more here](https://asdf-vm.com/).

It's confusing for some reason, but it's probably still better to *learn* one thing instead of rbenv, nvm, pyenv, whattheenv.

## troubleshooting

... well, this is annoying. if you install something globally with nodejs for example and the binary can't be found, try this:

```
asdf reshim nodejs
```

buh.

## list plugins

```
asdf plugin list all
```


## add plugin

```
asdf plugin add ruby
```

## install a version

**latest *stable* one:**

```
asdf install ruby latest
```

**list available versions:**

```
asdf list all ruby
```

**list even more specific ones:**

```
asdf list all ruby 2
```

**now install the actual thing:**

```
asdf install ruby 2.7.3
```

## set versions for projects / shell

define a specific version for the global environment (your user) and/or a project. Say I use ruby 3 as my global version but some other project requires ruby 2.7.

```
asdf global ruby latest
asdf local ruby 2.7.3
```

the _local_ thing will create a file in the project you're in and picking this up whenever you're in that folder.