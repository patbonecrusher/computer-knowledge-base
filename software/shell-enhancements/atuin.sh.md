---
creation date: 2025-01-03 14:55
tags:
  - shell/enhancements
  - shell/history
description: Better shell history
os:
  - linux
  - macos
source: Installed from website
url: https://atuin.sh
---
---
```cardlink
url: https://atuin.sh
title: "Atuin - Magical Shell History"
description: "Sync, search and backup shell history with Atuin"
host: atuin.sh
favicon: https://atuin.sh/favicon.svg
image: https://atuin.sh/img/og.jpg
```


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


