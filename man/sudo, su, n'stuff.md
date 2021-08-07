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
