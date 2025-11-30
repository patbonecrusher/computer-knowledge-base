---
creation date: 2025-01-03 14:55
tags:
  - shell/cli
  - shell/dotfiles
description: Manages my dotfiles
os:
  - linux
  - macos
command: chezmoi
source: brew
url: https://www.chezmoi.io/quick-start/#start-using-chezmoi-on-your-current-machine
---
---
```cardlink
url: https://www.chezmoi.io/quick-start/#start-using-chezmoi-on-your-current-machine
title: "Quick start - chezmoi"
description: "Manage your dotfiles across multiple machines, securely."
host: www.chezmoi.io
favicon: ../assets/images/favicon.png
```

To add the .config folder.

```shell
 echo ~/.config/* | xargs -rn1 | grep -v chezmoi | xargs -rn1 chezmoi add
```

tes