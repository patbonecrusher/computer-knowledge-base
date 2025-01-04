---
creation date: 2024-11-04 13:30
tags:
  - shell/cli
  - shell/package-manager
command: brew
description: macOS package manager
os:
  - linux
  - macos
source: Installed from website
url: https://brew.sh
---
---
```cardlink
url: https://brew.sh
title: "Homebrew"
description: "The Missing Package Manager for macOS (or Linux)."
host: brew.sh
favicon: https://brew.sh/assets/img/favicon.ico
image: https://brew.sh/assets/img/homebrew-social-card.png
```


## setting up brew

```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## configuring brew environment variables

The following ensures brew casks are installed in the home Applications folder.  Useful if you don't have write permission under the `/Applications` folder

```zsh
# In ~/.zshrc or in $XDG_CONFIG_HOME/homebrew/brew.env (default ~/.config)
export HOMEBREW_CASK_OPTS="--appdir=~/Applications"
export HOMEBREW_BAT=1    # Uses bat instead of cat when using brew cat ...
export HOMEBREW_NO_INSECURE_REDIRECT=1 # Prevent download of suspicious origin.

```