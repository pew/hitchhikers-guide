---
date created: Monday, February 2nd 2026, 7:58:13 am
date modified: Sunday, April 26th 2026, 7:34:09 am
tags:
  - node
  - npm
---

# npm

oh noez.

## default npm settings

you probably want to delay the installation of newly published packages for a few days to lower the chances of attacks and block scripts from running during installation. Add this to `~/.npmrc`:

```
min-release-age=7
ignore-scripts=true
```

### override `min-release-age`

if, for whatever reason, you need to override the `min-release-age` configured in `.npmrc` you can do this:

```
npm_config_min_release_age=0 npm i -g @openai/codex
```

## find outdated packages

* [docs](https://npm.github.io/using-pkgs-docs/working-with-packages/)

**global packages**:

```
npm outdated -g --depth=0
```

**local packages**:

```
npm update
```

within the folder/repository.

## upgrade outdated packages

ever got back to a project you didn't update for a year? well.

first, install a tool (globally) to find outdated packages:

```
npm install -g npm-check-updates
```

**check outdated packages:**

```
ncu
```

**update** `package.json`:

```
ncu -u
```

**actually update the packages:**

```
npm install
```

have fun that nothing is working. Hope you've got some tests in place.
