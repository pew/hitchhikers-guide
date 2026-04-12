---
date created: Monday, February 2nd 2026, 7:58:13 am
date modified: Sunday, April 12th 2026, 11:46:28 am
tags:
  - node
  - npm
---

# npm

oh noez.

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
