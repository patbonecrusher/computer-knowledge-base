---
creation date: 04/22/2025
tags:
  - dev/tools
  - shell/cli
description: tail output to web
os:
  - macos
  - linux
source: brew
url: https://logdy.dev/blog/post/remote-host-logs-browser-ui
---
---

```cardlink
url: https://logdy.dev/blog/post/remote-host-logs-browser-ui
title: "Remote host logs browser UI | Logdy"
description: "It's like jq, tail, less, grep and awk merged together and available in a clean UI. Self-hosted, single binary."
host: logdy.dev
```

rtail alternative.  rtail hasn't been updated in 10 years.

```
npm install -g rtail > tail output in a browser
rtail-server in a window
tail -f /var/log/system.log | rtail in another window
```