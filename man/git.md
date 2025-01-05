---
date created: Tuesday, May 7th 2019, 6:33:01 pm
date modified: Sunday, January 5th 2025, 2:11:57 pm
tags:
  - git
---

# git

some commands I always forget

## git lfs / git large file storage

put large files in a git repository:

```shell
git lfs install
git lfs track '.assets/**'
```

uninstall it with:

```shell
git lfs uninstall
```

## clone and pull without full history (shallow clone)

**clone:**

```shell
git clone --depth 1 <repository-url>
```

**fetch/pull:**

```shell
git fetch --depth 1
```

```shell
git pull --depth 1
```

## find deleted file

in order to restore something, you might want to know when it was deleted…:

```shell
git --no-pager log -1 -- path/to/file.txt
```

to just get the hash:

```shell
git --no-pager log --pretty=%H -1 -- path/to/file.txt
```

you might also want to look into *[--diff-filter](https://git-scm.com/docs/git-diff#Documentation/git-diff.txt---diff-filterACDMRTUXB82308203)* for more options like only deleted, modified files etc.

the `-1` limits the output to the last/most current commit

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

## separate .git directory

syncthing solutions such as dropbox / icloud drive often don't play well with all the files and frequent changes in a `.git` directory, with `--separate-git-dir` the `.git` directory can be stored outside of these systems

```shell
git init --separate-git-dir=/path/to/dot-git-directory .
```

[stackoverflow link](https://stackoverflow.com/a/40561395/10272994)

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

## multiple profiles

… different usernames and e-mail addresses for different folders.

create a new folder or use an existing one and create a file for your git config, such as `.gitconfig-personal` in `~/private`: `~/private/.gitconfig-personal`

```
[user]
  name = Your Name
  email = your@personal.email
```

now update your global `.gitconfig` file, usually stored in your home folder, so `~/.gitconfig`

```
[user]
  name = Your Name
  email = your@work.email
```

now add the following to this file:

```
[includeIf "gitdir:~/private/"]
  path = ~/private/.gitconfig-personal
```

ideally, all repositories within `~/private/` now use the personal gitconfig and everything else the global config.

## rename branch name (master to main)

… reminder for myself:

**doing this just for a local repo**, say if it was generated by a script:

```
git branch -m master main
```

**for an existing repo on the local system and remote**:

```
git branch -m master main
git fetch origin
git branch -u origin/main main
git remote set-head origin -a
```

set is as a default for your **local git config**:

```
git config --global init.defaultBranch main
```

## find deleted contents / file in history

so you deleted this one file you never thought about needing again. well, here you a couple of months later needing that file and you remember a string in there. let's find it. **but wait**, since we're going to use `git grep`, you can also pass or remove `-i` to ignore or not ignore case distinctions of strings.

```shell
git grep -i <regexp> $(git rev-list --all)
```

if you get a result and want to restore the file, the output provides you a commit hash and the file path. To restore it, do this:

```shell
git checkout 7e942ad6eabe34289cbc791e0655f79d3c439fe8:src/folder/your-file.yaml
```

if you know even more about the missing file, you can also search a sub folder for it:

```shell
git grep -i <regexp> $(git rev-list --all -- lib/util) -- lib/util
```

## git credentials

to store git credentials for remotes on disk, run this:

```
git config --global credential.helper store
```

if you're on macOS, you can use the keychain helper as well to store them more securely:

```
git config --global credential.helper osxkeychain
```

## disable pager

just want a list of things?

```
git --no-pager branch -a
```
