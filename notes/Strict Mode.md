---
tags: [Javascript]
title: Strict Mode
created: '2019-09-28T07:28:38.049Z'
modified: '2019-10-06T10:54:56.337Z'
---

# Strict Mode

Place a program or a function in strict operating context
Makes debugging easier.
Code errors which have been ignored / failed will throw exceptions

 Using a variable before its defined causes error . In non-strict mode, when value is assigned to an undeclared variable it automatically creates a global variable.

```js

"use strict";

b = 1;
console.log(window.b);  //1 non-strict


function newCode() {
    //Use strict mode
    "use strict";
    a = 1; // Error a is not defined
}

newCode();


```

1. Strict Mode helps in avoiding accidental typos and introducing global variables

```js

var theVal = 0;

thVal = 1; // Typo error which will be caught in strict mode

if(theVal) {
    console.log("Hello");
}

```

2. Strict mode prevents us from using words that are reserved for future versions of Javascript

```js

var let = 1;  //unexpected strict mode reserved word

```

3. Strict mode doesn't allow variables, functions and function arguments to  be deleted

```js

"use strict";

var foo = "foo";
delete foo;   // Not Allowed in Strict mode

function bar(arg) {
    delete arg  // Not Allowed in Strict mode
}

bar();
delete bar;  // Not Allowed in Strict mode

```

4. Makes eval safer to use ; Prevents variable scope from leaking outside eval

```js

"use strict";

var a  = 1;
eval("var a = 2");

console.log(a); // 1 in strict mode and 2 in non-strict mode
```

5. Default value of `this` in strict mode is undefined

```js

"use strict" 

function fun() {
  console.log(this); // undefined in strict mode and window object in non-strict mode
}

fun();
```
