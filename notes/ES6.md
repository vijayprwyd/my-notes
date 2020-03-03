---
tags: [Javascript]
title: ES6
created: '2019-10-17T04:54:39.071Z'
modified: '2019-10-23T12:24:51.927Z'
---

# ES6 

## var vs let

1. `let` has block scope ( contained between curly braces ).

```js

"use strict";

function fun() {

    if(3+4 === 7) {
        let z = "Hi";
    }

    console.log(z); // z not defined ; let block scoped
}
fun();

```

2. `let` variables can't be redeclared like var :

```js
"use strict";

let z = 5;
let z = 6;

console.log(z);
```

3. `let`  variables are not hoisted .

```js

"use strict";

age = 27;
console.log(age);  //27
var age;


"use strict";

age = 27;
console.log(age);  //Error; let variables are not hoisted and cannot be used before it is declared
let age;

```




* `const` Block scoped with constant value

Arrays and objects are references and const holds the value of reference . Hence the array values can be modified

```js

const age = 25;
age = 26;  // Error


const ages = [10, 11, 12];
ages[0] = 12;

console.log(ages); // 12, 11, 12


```

## Object Literals

```js
let age =25, name = "Vijay P R", x = "y", space = "Spaced string";

let obj = {
    age,  // 25
    name, // Vijay P R
    "greet me"() {
        console.log(this.name + " " + this.age);  // Vijay P R 25
    },
    [x]: 40, // obj.y = 40,
    [space]: 25
 };

```
