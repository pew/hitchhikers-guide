# xcode

## delete unused devices

```shell
xcrun simctl delete unavailable
```

## display touches in simulator

useful for screen recordings, set this using terminal and restart the simulator

```
defaults write com.apple.iphonesimulator ShowSingleTouches 1
```

set it back to 0 to disable it. It still won't shop up in screen recordings right out of xcode.