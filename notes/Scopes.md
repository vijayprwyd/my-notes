---
tags: [Javascript]
title: Scopes
created: '2019-09-29T05:35:10.474Z'
modified: '2019-10-21T06:21:06.090Z'
---

# Scopes

## Global Scope

* Variables declared outside the function : Availiable in any part of the program. Variables are automatically added as a property to the window object.

* All global variables are properties of window objects

```js

"use strict";

var x = 10;

console.log(window.x); //10

```

* The window object is availiable only in browsers

## Function Scope

Variables declared within the function have function scope / local scope

`var` has function scope

```js

"use strict";

for(var i = 0; i < 5; i++) {
  //Some code
}

console.log(i); // 5; var has function scope and not block scope
```

## Variable Hoisting

* Lifting of variable declarations to top of the enclosing scope.
* Variable declarations are only hoisted and not initializations.
* Function declarations are also hoisted

```js

"use strict";

console.log(a); //No error; a = undefined
var a = 10;

```

```js

"use strict";

foo();  //Function declarations are also hoisted

function foo() {
    return 5;
}

```

```js

"use strict";

foo(); // Error ; foo is a function expression and initialization is not hoisted
var foo = function() { // Foo declaration is hoisted

    console.log("Bar");
}


```

## Scope Chain

Variables are searched within the enclosing scope. If not found, searched in the next outer / enclosing scope .

```js

"use strict";

function foo() {
    var myVar = 1;

    function bar() {
        console.log(myVar); // 1; Scope chaining , next enclosing scope searched
    }

    bar();
}

foo();


```

## IIFE ( Immediately Invoked Function Expression )

* Function Expression which is invoked immediately .
* Doesn't pollute global namespace as the variables are within the scope of IIFE function

```js

"use strict";

(function() {
    var x = 3;
    console.log(x);
})()


```

## Closures

* When a function returns a function the returned function keeps a reference of any variables that it needs to execute.
* can refer to variables in scope external to itself
* With closure, function will have access to variables even after it should have been deleted / disposed by JS engine
* Inner functions store their outer function’s variables by reference, not by value

```js

function foo(name) {

    let someUnusedVariable = "a"; // This reference cannot be  accessed by closure since its not used in the function
    return function() {
        return "Hello " + name; // name can be accessed at the point where the function is called.
    }

}

var x = foo("Vijay");
x(); // Hello Vijay

```

```js

"use strict"

var foo = [];

function fun() {

    for(var i = 0; i < 5; i++) {
        foo[i] = function() {            
                return i;
        }
    }
}

fun();
console.log(foo[0]());   // 5
console.log(foo[1]());  // 5
console.log(foo[2]());  // 5
console.log(foo[3]());  // 5

```

```js

"use strict"

var foo = [];

function fun() {

    for(var i = 0; i < 5; i++) {
       (function() {
            var y = i;
            foo[i] = function() {
             return y;
            } 
        })(i)
    }
}

fun();

console.log(foo[0]());   // 0
console.log(foo[1]());  // 1
console.log(foo[2]());  // 2
console.log(foo[3]());  // 3


```

### Closure with Callback

```js

"use strict"

function fun() {

  var i = 10;
  var j= 5;
 
  function cb() {
    console.log(i);
  }
  hoc(cb);
}

function hoc(cb) {
  cb();
}

fun();

```

### Closure for Private Variables 

```js 

"use strict";

function Person(firstName, lastName) {

    this.fullName = function() {
        return firstName + " " + lastName;
    }
}

var person = new Person("Vijay", "P R");
console.log(person.fullName());  // Vijay P R


```


## Static Vs Dynamic Scope :

In dynamic scope, the scope is based on call stack and not on nesting of scopes. It is determined at run time and not an compile time

```js
"use strict";

var a = 5;

function foo() {
    var a =10;
    bar();
}

function bar() {
    console.log(a);  //5
}

foo();
```
