---
tags: [Javascript]
title: Pass by Value or Reference
created: '2019-09-28T08:51:05.533Z'
modified: '2019-09-28T09:08:08.814Z'
---

# Pass by Value or Reference 

Primitive types like strings, numbers and booleans are passed by value and objects are passed by reference.

```js

"use strict";

function foo(a) {
    a = 10;
    console.log("In Foo : a = " + a);  // a = 10;
}

var a = 5;
foo(a);

console.log("Outside Foo :  a = " + a);  // a= 5 ;  Primitives are passed by value


```

```js

"use strict";

function foo(a) {
    a.foo = "bar";
    console.log("In Foo : a = " + JSON.stringify(a));  // a = {"foo":"bar"}
}

var a = {foo: "foo"};
foo(a);

console.log("Outside Foo :  a = " + JSON.stringify(a));  //  a = {"foo":"bar"} Objects passed by reference

```

Arrays are passed by values but array elements can be modified from the function

```js

"use strict";

function foo(arr) {
    arr = [5];
    console.log(arr);  // 5
}


var a = [1, 2, 3];

foo(a);

console.log(a);  // 1, 2, 3

```

```js

"use strict";

function foo(arr) {
    arr[0] = 10;
    console.log(arr);  // 10, 2, 3
}


var a = [1, 2, 3];

foo(a);

console.log(a);  // 10, 2, 3


```

