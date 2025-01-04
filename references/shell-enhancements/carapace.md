---
creation date: 2024-11-04 21:56
tags:
  - shell/completion
  - shell/enhancements
description: A multi-shell completion
os:
  - macos
source: brew
url: https://carapace.sh
---


![](Pasted%20image%2020241104220221.png)

```cardlink
url: https://carapace.sh
title: "Carapace"
description: "A multi-shell completion library and binary. Supports Bash, Elvish, Fish, Nushell, Oil, Powershell, Xonsh and Zsh."
host: carapace.sh
```

## install

```zsh
brew install carapace
```

## config 
### nushell

```nu
# Add at the bottom of $nu.env-path

$env.CARAPACE_BRIDGES = 'zsh,fish,bash,inshellisense'
mkdir ~/.cache/carapace
carapace _carapace nushell | save --force ~/.cache/carapace/init.nu
```

```nu
# Add at the bottom of $nu.config-path
source ~/.cache/carapace/init.nu
```

### zsh

```zsh
# ~/.zshrc
export CARAPACE_BRIDGES='zsh,fish,bash,inshellisense' # optional
zstyle ':completion:*' format $'\e[2;37mCompleting %d\e[m'
source <(carapace _carapace)
```