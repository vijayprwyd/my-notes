---
attachments: [Clipboard_2020-02-04-23-57-03.png]
tags: [Web Performance]
title: Render Blocking CSS
created: '2020-02-04T18:06:51.433Z'
modified: '2020-02-04T18:27:03.963Z'
---

# Render Blocking CSS

* In order to paint a page, render tree needs to be constructed
* To construct render tree, we need both DOM and CSSOM trees
* Browser needs to wait until it fetches the CSS before it can paint.ie CSS is render blocking
* Render blocking CSS can be prevented using `media-queries` .When `media-query` is there in the link attribute, browser will download the file but applies it only for that media , ie doesn't block rendering. In this way Waiting time to render the page can be reduced.


![](@attachment/Clipboard_2020-02-04-23-57-03.png)




