# rectangle

window manager for macos, installation with brew:

```shell
brew cask install rectangle
```

## almost maximize sizing

make the *almost maximize* sizing more appropriate on a smaller screen. yes, sometimes I prefer *almost* maximized instead of maximized, even if it's set to 0.99. it makes a difference!

```shell
defaults write com.knollsoft.Rectangle almostMaximizeWidth -float 0.99
defaults write com.knollsoft.Rectangle almostMaximizeHeight -float 0.99
```