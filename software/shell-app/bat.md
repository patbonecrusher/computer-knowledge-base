---
creation date: 2025-01-02 14:21
tags:
  - shell/cli
  - shell/replacements
  - shell/app
command: cat (or bat)
description: nicer `cat`
os:
  - linux
  - macos
source: brew
url: https://github.com/sharkdp/bat
---
---
```cardlink
url: https://github.com/sharkdp/bat
title: "GitHub - sharkdp/bat: A cat(1) clone with wings."
description: "A cat(1) clone with wings. Contribute to sharkdp/bat development by creating an account on GitHub."
host: github.com
favicon: https://github.githubassets.com/favicons/favicon.svg
image: https://repository-images.githubusercontent.com/130464961/20727580-dd13-11e9-8f03-0789a00a3b64
```


```shell
brew install bat
```

### using bat with man

```shell
export MANPAGER="sh -c 'col -bx | bat -l man -p'"
```