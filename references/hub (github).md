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
---
## Forking a public repo and doing pull request

```
git clone https://repo
cd repo
hub fork
git push YOUR_USER feature
hub pull-request
```