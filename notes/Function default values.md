---
tags: [Javascript]
title: Function default values
created: '2019-10-23T11:51:26.784Z'
modified: '2019-10-23T11:52:46.378Z'
---

# Function default values

```js
function fun(a=10, b = 20) { // a defaults to 10 only if passed value is undefined
    console.log(a); 
    console.log(b);
}

fun(undefined, 10);
```

```js

function fun(a=b, b = 20) { //Error b used before initialisation
    console.log(a); 
    console.log(b);
}
```

