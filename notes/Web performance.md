---
tags: [Web Performance]
title: Web performance
created: '2020-02-01T08:24:56.799Z'
modified: '2020-02-01T11:06:48.668Z'
---

# Web performance

* **Request Latency** Time between sending a request and waiting for response

* **Page Load Time** Time taken for a website to be rendered on browser after it is requested . Multiple HTTP(s) requests are send for a page to be rendered

A web page comprises of multiple HTML files, CSS , JS and other assets ( image, audio, video etc ).

## 1. Minification

### 1.1 Minifying assets 

* Whitespace and unnecesary characters like tabs, line breaks , comments etc are stripped from a text based asset.

* Lesser data downloaded and hence total download time reduced

* Consistent performance gain for users across any device

```
npm install –g minifier html-minify

minify -o styles.min.css styles.css

minify -o jquery.min.js jquery.js

htmlminify -o index.html index.src.html

```

### 1.2. Minify CSS - Reduce total size and hence time to download

```css

// Before Minification

/* Flex based display illustration*/

div {
 display: flex;
 flex-direction : row;
flex-wrap: wrap
}

// After Minification

div{display:flex;flex-direction:row;flex-wrap:wrap}

```js

function helloWorldFromPerson(firstArg, secondArg) {

 // Logs Hello World

  let finalResult =firstArg + secondArg
  console.log("Hello World" + finalResult);

}

helloWorldFromPerson(2, 4);


// After minification

function helloWorldFromPerson(o,l){let e=o+l;console.log("Hello World"+e)}helloWorldFromPerson(2,4);


```

## 1.3 Avoid HTML Minification


* Minifying HTML may have undesirable consequences while ignoring whitespace characters and is advicable to be avoided 


```html

<ul>
    <li>simple</li>
    <li>list</li>
</ul>

<ul><li>simple</li><li>list</li></ul>


//Output

simple list
simplelist    <!-- Whitespace Ignored between aimple and list   -->
``` 


## 2. Compression of text assets


**Server Compression**

```
npm install compression

```

* User requests web page from the server

* Users request is accompanied by `Accept-Encoding` header that tells the server, the compression format browser is capable of using

* Server responds back with `Content-Encoding` header that describes compression method along with the compression content.

Server compresses the files and sends it across the network. Browser unzips it before using. 
Benefits of compression outweighs zipiing and unzipping overhead

Minifcation simply removes unwanted characters , and the minified file is a syntactivally valid CSS and JS file. Compression replaces reduntant characters by some pointers and performs other optimizations as well and the resulting file had to be unzippped.



* Avoid compressing files that already uses compression when they are encoded such as JPEG, PNGand GIFF images and WOFF, WOFF2 font files


## 3. Image Compression




