---
attachments: [Clipboard_2020-02-04-14-28-52.png, Clipboard_2020-02-04-14-29-14.png, Clipboard_2020-02-04-14-29-40.png]
tags: [Web Performance]
title: Critical Rendering Path
created: '2020-02-04T04:46:12.280Z'
modified: '2020-02-10T06:02:39.824Z'
---

# Critical Rendering Path

Sequence of steps that browser goes through while rendering a page . ie Convert HTML , CSS and JS to actual pixels on the screen

https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css

## 1. Converting HTML to the DOM

* Browser requests for html page from server
* Received HTML data is parsed by the browser 
* Whenever a tag is encountered browser emits a token( like StartTag, EndTag etc ). This is done by the tokenizer
* While tokenization , the tokens are consumed and convrted to node objects
* A node tree is contructed , based on when the nodes are generated (between which tags) and parent-child relation established
* Once all tokens are consumed we arrive at the Document Object Model ( DOM ) : Tree structure that captures the content and properties of the HTML and all the relationships betweent the Nodes
* Browser constructs the DOM incrementally; Incremental HTML rendering . Before even processing a request , headers and some static contents are rendered

![](@attachment/Clipboard_2020-02-04-14-29-40.png)

## 2. Converting CSS to CSSOM

* CSS Parses parses Characters ->  Tokens -> Nodes -> CSSOM
* CSS child nodes inherit parents style rules. ie Cascading rules and hence cascading style sheets. CSS rules cascade down

* Partial CSS tree is not possible unlike partial DOM tree because wrong styles may be used to render the page. Parent CSS would be overrriden by child nodes but partial rendering will cause wrong styles of parent node to be rendered. CSS is render blocking which means any processed content will not be rendered until CSSOM is constructed.

* Browser blocks page rendering until it receives and processes all CSS

![](@attachment/Clipboard_2020-02-04-14-29-14.png)

* More specific tags requires more work from the server. ie More specific the selector is , the rule is slower to evaluate because more nodes need to be traversed in the DOM tree


![](@attachment/Clipboard_2020-02-04-14-28-52.png)


## 3. Combine DOM and CSSOM trees into Render Tree

Start at the root node of the DOM tree and check if there are any CSS rules that match
* Render tree captures only the visible content . We can skip nodes that are not visible and its child
* Render tree captures both the content and the styles


## 4. Layout

`meta tag` tells browser that width of layout viewport should be equal to the device width

* In this stage width and position of each tag is calculated.
* If the dimensions of the viewport change the browser has to rerun the layout step, which happens every time browser is resized

## 5. Painting

* It refers to putting pixels in the screen


Analysing Entire CRP

1. Browser requests for the HTML document
2. Server returns the response
3. Browser parses the HTML ( Bytes -> Characters -> Tokens -> Nodes -> DOM tree)
4. While parsing, browser initiates requests for images css etc
5. After requesting parsing HTML is continued.
6. Once it reaches the end , it constructs the CSSOM
7. Browser constructs the render tree
8. Layout is calculated
9. Paint event is issued


CRP is a gradual process: browsers won't wait until all HTML is parsed. Parts of the content will be parsed and displayed, while the process continues with the rest of the contents that keeps coming from the network.





