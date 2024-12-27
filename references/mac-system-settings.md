---
creation date: 2024-11-05 09:49
modification date: Tuesday, 5th November 2024, 09:49:31
tags:
  - shell/system-configuration
  - os/macos
  - to-investigate-more
---

## dock

```
defaults write com.apple.dock orientation left

# Faster hide
defaults write com.apple.dock autohide-time-modifier -float 0.15
# revert: defaults delete com.apple.dock autohide-time-modifier

killall dock
```


## desktop

To hide desktop icons

```
defaults write com.apple.finder CreateDesktop false

killall finder
```

## menubar
I recently found out that it's possible to reduce the spacing of menu bar items to get more space. This doesn't change the size of the actual items, just the spacing between them.

`defaults -currentHost write -globalDomain NSStatusItemSpacing -int x`

The value I set for x was 6 but your mileage may vary. You have to log out and log back in for it to take effect. No restart required.

To reset it to the default setting, use

`defaults -currentHost delete -globalDomain NSStatusItemSpacing`


---
### references

```cardlink
url: https://git.herrbischoff.com/awesome-macos-command-line/about/
title: "awesome-macos-command-line - Use your macOS terminal shell to do awesome things."
host: git.herrbischoff.com
```


```cardlink
url: https://ss64.com/mac/
title: "An A-Z Index of the Apple macOS command line - SS64 Command line reference"
host: ss64.com
favicon: https://ss64.com/favicon.ico
```

