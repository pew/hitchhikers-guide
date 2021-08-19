# git

some commands I always forget

## revert / restore single file

why wasn't this on the top, what the... let's say you want to restore a file from a previous commit. get the hash with `git log` and do:

```
git checkout 34973274ccef6ab4dfaaf86599792fa9c3fe4689 filename.md
```


## mtls / client certificate authentication

to use mutual tls client certificate authentication with git, update your `~/.gitconfig` file and add a block with the hostname in there and set the path to the certificate

```
[http "https://your.securet.git.host.com"]
sslCert = "/Users/username/.cert.pem"
sslKey = "/Users/username/.key.pem"
sslVerify = true
sslCertPasswordProtected = false
```

[thanks](https://stackoverflow.com/questions/28878549/how-to-configure-git-https-client-certificate-authentication-in-eclipse-using-eg)

## delete branch locally and remotely

```
git push --delete <remote_name> <branch_name>
git branch -d <branch_name>
```

example:

```
git push --delete origin short_url
git branch -d short_url
```

## push all branches

```
git push --all <remote>
```

for example:

```
git push --all origin
```

## git submodules

too confusing.

### add git submodule

```
git submodule add https://github.com/vimwiki/vimwiki.git
```

### init git submodules

```
git submodule init
git submodule update
```

### remove git submodules

just get rid of them, I just can't wrap my head around this stuff:

```
# Remove the submodule entry from .git/config
git submodule deinit -f path/to/submodule

# Remove the submodule directory from the superproject's .git/modules directory
rm -rf .git/modules/path/to/submodule

# Remove the entry in .gitmodules and remove the submodule directory located at path/to/submodule
git rm -f path/to/submodule
```

yes, this is from [here](https://stackoverflow.com/a/36593218)

## delete file / folder from history

well, things happen from time to time. I just wanted to get rid of a folder and move it to git *lfs*


```
git filter-branch -f --index-filter "git rm -rf --cached --ignore-unmatch .assets" -- --all
```

also cleanup remote:

```
rm -rf .git/refs/original/
git reflog expire --expire=now --all
git gc --aggressive --prune=now
git push --all --force
```

[source](https://stackoverflow.com/a/24526351)

## create tar archive from repo

```shell
git archive --format=tar HEAD -o filename.tar
```

## delete files part of .gitignore

if you added some extensions, files and/or folders to your `.gitignore` file later on and want to clean up the whole repo, there's a lot of stuff on stack overflow, but this one does what I wanted (check my gitignore file, match all the things in there, delete everything that matches):

```
git ls-files --ignored --exclude-standard -z | xargs -0 git rm --cached
```

[thank you](https://stackoverflow.com/a/23839198)

## change e-mail address for commits

install `git-filter-repo` with pip:

```
pip install git-filter-repo
```

assume you want to change the e-mail address for all commits from *old@example.com* to *new@example.com* for whatever reason:

```
git-filter-repo --replace-refs delete-no-add --partial --email-callback 'return email.replace(b"old@example.com", b"new@example.com")'
```

if it's also a repository stored on a remote server you need to force push with `git push --force`

to change the name, you can also use `--name-callback 'return name.replace(b"OldName", b"NewName")'` and/or combine the two of them and do more.

[source](https://stackoverflow.com/a/60364176/10272994)