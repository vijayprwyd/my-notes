---
attachments: [Clipboard_2020-02-05-12-48-03.png]
tags: [Web Performance]
title: CRP Optimization
created: '2020-02-05T04:55:46.500Z'
modified: '2020-02-05T07:29:21.605Z'
---

# CRP Optimization

* Javascript is **parser blocking**.
* Whenever `script` tag is encountered , DOM construction is blocked
* Parser finds the script tag, fetches the file from external source and executes it . The fetch process could be slower 
* Script may also want to access the CSS properties. So script execution is blocked until css arrives and we build the CSSOM. Only then we run JS and finish building the DOM
* CSS is **render blocking** as well as **script blocking**


**Critical Resources** : Resources which are render blocking or parser blocking

Non Blocking JS :

* Place `script` at the bottom of the html

* Browser fires `onload` event when page is finished loading. We could wait for that and execute the script then

* Add `async` attribute to script tag. This tells the browser that it doen't have to block the DOM construction when it encounters the script tag. Browser dispatches the script request and continues parsing the DOM
* If script is availiable before CSSOM is ready it can still be executed
* Inline scripts will always block on CSSOM


## General strategies

1. Minimize bytes ( Minify, Compress, Cache )

2. Reduce critical resources
  * Minimize use of render blocking resources ( CSS ) : Use `media queries` and `inline CSS` . Inlining may not be a good idea when we need to share the code among multiple files
  * Minimize use of parse blocking resources ( JS )

3.  Shorten CRP Length


## CRP Diagram

![](@attachment/Clipboard_2020-02-05-12-48-03.png)


**Preload Scanner**  peaks ahead in the document and discovers critical CSS nad JS files like `timing.js`

Even though parses is blocked the resources are requested .
