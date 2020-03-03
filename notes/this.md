---
tags: [Javascript]
title: this
created: '2019-10-04T08:15:22.561Z'
modified: '2019-10-06T11:54:53.282Z'
---

# this

When used outside any function it points to the window object
this referes to the current execution context
Determined by calling context

```js

var y = 10;

function foo() {
  console.log(this);   // Points to the global object
  console.log(this.y);
}

foo();

var object = {
  a: 10,
  checkThis: function() {
    console.log(this);  
  } 
};

object.checkThis();  // {a: 10, checkThis: ƒ} . this Points to the current Object

var fun = object.checkThis;
fun(); // this points to Window Object

```

```js

var obj = {
  checkThis: function() {
    console.log(this); // Points to current object

   function checkOther() {
     console.log(this);  // Window Object because there isn't a calling context; In strict mode this would be undefined
   }
    checkOther();
  }
}

obj.checkThis();

```

## Solutions

1. `var`

```js
var obj = {
  checkThis: function() {
    console.log(this); // Points to current object
    var self = this;
   function checkOther() {
     console.log(self);  
   }
    checkOther();
  }
}

obj.checkThis();

```

2. `call` `apply` `bind`

## call

Functions are objects in Javascript with some inbuilt propoerties and we can add properties to them as well.

```js

"use strict";

function fun() {

}

fun.foo = "foo";
console.log(fun.name); //fun 
console.log(fun.foo);  // foo

```

```js

function fun() {

}
fun.call(); // Equivalent to fun();

```

With call we can explicitly pass this object / context


```js

"use strict";

function fun() {
console.log(this + 4);

}

console.log(fun.call({})); // {} as this
console.log(fun.call(1));  // 1 as this



```

```js 

"use strict";

var obj = {
  b: 10,
  checkThis: function() {
    console.log(this.b); // 10

   function checkOther() {
      console.log(this.b);  // error in strict mode if this is not explicityly passed as in  checkOther()
    }
   // checkOther();
    checkOther.call(this); // 10; this context is passed to checkOther() via call method
  }
}

obj.checkThis();


```

Passing parameters to call

```js

"use strict";

function fun(a, b, c) {
  console.log(a); // 2
  console.log(b); // 3
  console.log(c); // 4 
  console.log(this); // 1
}

fun.call(1, 2, 3, 4); // 1st parameter to call function is this

```

## apply

`apply` is similar to call except the parameters are passed as an array, which would be the second argument to apply. 



```js

"use strict";

function fun(a, b, c) {
  console.log(a); // 2
  console.log(b); // 3
  console.log(c); // 4 
  console.log(this); // 1
}

fun.apply(1, [2, 3, 4]); // 1st parameter to apply function is this and second is an array which contains all the parameters to be passed

```

Use `appply` when we want to pass variable no of parameters to the function and `call` when we want to pass fixed no of arguments

```js

"use strict";

function sum() {
  var sum = 0;
  for(let i=0; i < arguments.length; i++) {
    sum += arguments[i];
  }
  return sum;
}

var things = [1, 2, 3, 4, 5];

console.log(sum.apply(null, things)); // 15
console.log(sum.call(null, ...things)); // 15


```

## bind

At the time we define the function expression , we can define the this context of bind with `this`.

Locks this for the function 

```js
"use strict";

var person1 = {
  name: "person1",
  getName,
};

var person2 = {
  name: "person2",
  getName
}


var person = {
  name: "Bind Person"
}

var getName = function () {
  console.log(this.name);
}.bind(person);

person1.getName();  //Bind person
person2.getName(); // Bind person
```

```js

"use strict";

var obj = {
  a:'a',
  checkThis: function() {
    console.log(this.a); //a
    var checkOther = function() {
      console.log(this.a); // a
    }.bind(this);
    checkOther();
  }
}

obj.checkThis();

```



