# shellcheck

> finds bugs in your shell scripts.

[use or get/install it from here](https://www.shellcheck.net)

## auto-fix

shellcheck provides a diff output, so things can be automatically fixed with the `patch` command. but I guess this should be checked on a script-by-script basis.

**check the script first:**

```shell
shellcheck my-script.sh
```

read and try to understand the outputs, if it's just easy things like quoting variables you can *patch* the file automatically:

```shell
shellcheck -f diff my-script.sh | patch
```

or just show the *diff* output and review it:

```shell
shellcheck -f diff my-script.sh
```