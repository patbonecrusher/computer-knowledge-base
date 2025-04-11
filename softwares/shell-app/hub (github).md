---
creation date: 2024-11-27 13:30
tags:
  - dev/git
  - shell/cli
  - shell/replacements
command: git or hub
description: github extensions for the git cli
os:
  - linux
  - macos
  - windows
source: brew
url: https://hub.github.com
---
---
```cardlink
url: https://hub.github.com
title: "hub · an extension to command-line git"
host: hub.github.com
```

## Forking a public repo and doing pull request

```
git clone https://repo
cd repo
hub fork
git push YOUR_USER feature
hub pull-request
```