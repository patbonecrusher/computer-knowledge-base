---
creation date: 2024-11-04 22:04
modification date: Monday, 4th November 2024, 22:04:57
tags:
  - shell/cli
  - shell/navigation
  - shell/replacements
command: cd
description: Support jumping around to previously visited folders
os:
  - linux
  - macos
---

[![Cover image for zoxide - A faster alternative to boring cd command](https://media2.dev.to/dynamic/image/width=1000,height=420,fit=cover,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F8vuq8qvkp5c1e8b1klss.jpg)](https://media2.dev.to/dynamic/image/width=1000,height=420,fit=cover,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F8vuq8qvkp5c1e8b1klss.jpg)


```cardlink
url: https://github.com/ajeetdsouza/zoxide
title: "GitHub - ajeetdsouza/zoxide: A smarter cd command. Supports all major shells."
description: "A smarter cd command. Supports all major shells. Contribute to ajeetdsouza/zoxide development by creating an account on GitHub."
host: github.com
favicon: https://github.githubassets.com/favicons/favicon.svg
image: https://repository-images.githubusercontent.com/245166720/f83acf80-9243-11eb-80f8-302e9a53427c
```


## install

```zsh
brew install zoxide
```

## config 
### nushell

```nu
# Add at the bottom of $nu.env-path
zoxide init nushell | save -f ~/.zoxide.nu
```

```nu
# Add at the bottom of $nu.config-path
source ~/.zoxide.nu
```

### zsh

```zsh
# ~/.zshrc
export CARAPACE_BRIDGES='zsh,fish,bash,inshellisense' # optional
zstyle ':completion:*' format $'\e[2;37mCompleting %d\e[m'
source <(carapace _carapace)
```