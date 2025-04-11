---
creation date: 2025-01-03 14:55
tags:
  - shell/cli
  - shell/clipboards
command: pet
description: Cli snippet manager
os:
  - linux
  - macos
source: brew
url: https://github.com/knqyf263/pet?tab=readme-ov-file#mac-os-x--homebrew
---
---

```cardlink
url: https://github.com/knqyf263/pet?tab=readme-ov-file#mac-os-x--homebrew
title: "GitHub - knqyf263/pet: Simple command-line snippet manager"
description: "Simple command-line snippet manager. Contribute to knqyf263/pet development by creating an account on GitHub."
host: github.com
favicon: https://github.githubassets.com/favicons/favicon.svg
image: https://opengraph.githubassets.com/84936bf9d2c05f7d4cccb440fed97238397c87106f9a724895e3c1ab36aaff74/knqyf263/pet
```


```shell
brew install knqyf263/pet/pet
```

To quickly save a command add to .zshrc

```zsh
function prev() {
  PREV=$(fc -lrn | head -n 1)
  sh -c "pet new `printf %q "$PREV"`"
}
```

To search snippets and output on the shell add to .zshrc

```zsh
function pet-select() {
  BUFFER=$(pet search --query "$LBUFFER")
  CURSOR=$#BUFFER
  zle redisplay
}
zle -N pet-select
stty -ixon
bindkey '^s' pet-select
```