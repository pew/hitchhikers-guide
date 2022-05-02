# sudo / su

who knew.

## preserve environment from user

so you've exported some environment variables and want to run a command via sudo and pass the variables along?

```
sudo --preserve-env
```

## run command as another user with no login shell

assuming a user as the shell set to `/usr/sbin/nologin` but you want to run a command as this user, for, say accepting /testing an ssh connection.

```
su -s /bin/sh -c '/the/script.sh' theOtherUser
```

## disable DNS for sudo command

When your *sudo* command hangs for a while, it's doing some DNS resolution in the background until it times out or gets an answer. Apparently this is not the default but was set as a default by Debian and Ubuntu etc., so just run:

```shell
sudo visudo
```

and add this to the end of the `sudoers` file:

```
Defaults !fqdn
```

[thank you](https://superuser.com/a/1538711)