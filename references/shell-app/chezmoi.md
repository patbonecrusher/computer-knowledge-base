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
To get the square border around atuin I had to update the config in `.config/atuin/config.toml`:

```toml
## which style to use
## possible values: auto, full, compact
style = "full"
```

I also disable the auto execute on enter:

```toml
## Defaults to true. If enabled, upon hitting enter Atuin will immediately execute the command. Press tab to retu
rn to the shell and edit.
# This applies for new installs. Old installs will keep the old behaviour unless configured otherwise.
# enter_accept = true
```