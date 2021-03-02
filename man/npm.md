# npm

oh noez.

## find outdated packages

* [docs](npm.github.io/using-pkgs-docs/working-with-packages/)

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