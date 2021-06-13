# vim

I'll never get used to it. Let's get started and learn..

## save with sudo

I need it every day, I just can't remember it. needs to be on the top. when you get this (opening and editing a file as a regular user but the file is owned by someone else): `'readonly' option is set (add ! to override)`, do this:

```
:w !sudo tee %
```

## indent multiple lines by `n` spaces

`n` is 2 in this example

```
set shiftwidth=2
```

select multiple lines with `v` (visual mode) and do `>`

or, **a better way** imho:

1. select the lines you want with `V`, hit `:` and do `le4` where 4 is the number of spaces

```
Vjj:le4
```

(`V` for visual mode, `jj` for selecting two lines (you can also use your arrow keys), `:le4` to indent by 4 spaces)

## convert tabs to spaces

that's correct.

```
:set tabstop=4 shiftwidth=4 expandtab
```

## create new file

```
vim file.md
```

**create new file while vim is open**:

```
:e other-filename.md
```

## paste from external clipboard

```
Ctrl + Shift + V
```

[thank you](https://www.256kilobytes.com/content/show/10503/5-tasks-you-didnt-know-you-could-do-with-vim).

## vertical highlighting

```
ctrl + v
```

[thank you](https://www.256kilobytes.com/content/show/10503/5-tasks-you-didnt-know-you-could-do-with-vim).

## search

**search and replace within the whole document:**

```
%s/search-term/replace-term/g
```

**search and replace interactively term by term:**

```
%s/search-term/replace-term/gc
```

## useful plugins

### nerdtree

* [cool vim tree explorer plugin](https://github.com/scrooloose/nerdtree)

#### switch to nerdtree window

```
ctrl + ww
```

#### toggle nerdtree window

open, close, open, close. bed up, bed down, bed up, bed down

that's the default:

```
:NERDTreeToggle
```

add something like this to your `~/.vimrc`` file

```
nnoremap <Leader>f :NERDTreeToggle<Enter>
```

with this line you can toggle nerdtree with `\f` given that `\` is your *leader* key.

#### reload tree

```
r
```

or reload the whole folder structure:

```
R
```

### vimwiki

a plain text wiki for vim including a diary function, kinda cool.

* [vimwiki docs](https://github.com/vimwiki/vimwiki)

#### key bindings

I need to learn and remember them! `<Leader>` is `\`

* `<Leader>ww` -- Open default wiki index file.
* `<Leader>wt` -- Open default wiki index file in a new tab.
* `<Leader>ws` -- Select and open wiki index file.
* `<Leader>wd` -- Delete wiki file you are in.
* `<Leader>wr` -- Rename wiki file you are in.
* `<Enter>` -- Follow/Create wiki link
* `<Shift-Enter>` -- Split and follow/create wiki link
* `<Ctrl-Enter>` -- Vertical split and follow/create wiki link
* `<Backspace>` -- Go back to parent(previous) wiki link
* `<Tab>` -- Find next wiki link
* `<Shift-Tab>` -- Find previous wiki link
 
**diary key bindings**:

* `<Leader>w<Leader>w` - create new diary file with current date
* `<Leader>wi` - go to diary index
* `<Leader>w<Leader>i` - update diary index

### vim-markdown

* [vim-markdown docs](https://github.com/plasticboy/vim-markdown) - until I've learned it by myself

### vimoutliner

* [vimoutliner docs here](https://github.com/vimoutliner/vimoutliner) - until i've learned it
* [vimoutliner cheat sheet](https://github.com/vimoutliner/vimoutliner/blob/master/doc/votl_cheatsheet.txt) - they're really tricking you in reading the README to find the cheat sheet!
