---
creation date: 2024-12-03 21:57
tags:
  - dev/gui
  - dev/language/javascript
  - dev/platform/nodejs
---

```cardlink
url: https://github.com/samizdatco/skia-canvas
title: "GitHub - samizdatco/skia-canvas: A GPU-accelerated 2D graphics environment for Node.js"
description: "A GPU-accelerated 2D graphics environment for Node.js - samizdatco/skia-canvas"
host: github.com
favicon: https://github.githubassets.com/favicons/favicon.svg
image: https://repository-images.githubusercontent.com/285112082/4d0650b6-a4bc-4308-98b7-3980f0282589
```


```cardlink
url: https://skia-canvas.org
title: "About | Skia Canvas"
description: "Skia Canvas"
host: skia-canvas.org
favicon: https://skia-canvas.org/img/favicon.ico
image: https://skia-canvas.github.io/img/social-card.jpg
```

```javascript
import {Window} from 'skia-canvas'  
  
let win = new Window(300, 300)  
win.title = "Canvas Window"  
win.on("draw", e => {  
	let ctx = e.target.canvas.getContext("2d")  
	ctx.lineWidth = 25 + 25 * Math.cos(e.frame / 10)  
	ctx.beginPath()  
	ctx.arc(150, 150, 50, 0, 2 * Math.PI)  
	ctx.stroke()  
  
	ctx.beginPath()  
	ctx.arc(150, 150, 10, 0, 2 * Math.PI)  
	ctx.stroke()  
	ctx.fill()  
})
```
