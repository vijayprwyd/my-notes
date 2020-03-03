---
tags: [Javascript]
title: Arrow Function
created: '2019-10-18T12:32:06.969Z'
modified: '2019-10-21T06:11:52.437Z'
---

# Arrow Function

* Syntatic Sugar introduced in ES6 

```js

"use strict";

let fn = a => a+5;

console.log(fn(7)); // 12

let add = (a, b) => a+5;

console.log(add(5, 7)); // 10


```

* Arrow function keeps its Context `bind`, `apply` or `call` is not required `this` doesn't change dynamically

`this` refers to context in which it was declared in arrow functions whereas in classical functions `this` refers to the context in thich it is executed


* Arrow functions don't bind their own scope but inherit scope from parent

* Arrow functions cannot be used as a constructor

```js

"use strict";

var obj = {

    firstName: "Vijay",
    lastName: "P R",

    fun: function () {
        setTimeout(() => {
            console.log(`${this.firstName} ${this.lastName}`) // Vijay P R
        }, 1000);

        setTimeout(function () {
            console.log(`${this.firstName} ${this.lastName}`) // undefined undefined
        }, 1000);
    }
}

obj.fun();


```

