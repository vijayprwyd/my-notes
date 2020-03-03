---
tags: [Javascript]
title: Constructor Function and Prototype
created: '2019-10-08T11:05:37.421Z'
modified: '2019-10-13T07:09:15.630Z'
---

# Constructor Function and Prototype

```js

"use strict";

function Person(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;

    this.fullName = function() {
        return this.firstName + " " + this.lastName;
    }
}

var person = new Person("Vijay", "P R");
console.log(person.fullName());  // Vijay P R

var person1 = {};
Person.call(person1, "Vijay", "P R");
console.log(person1); // {firstName: "Vijay", lastName: "P R", fullName: ƒ}firstName: "Vijay"fullName: ƒ ()

```

## `new` keyword

1. Creates a new object and calls the constructor function with this object context ( `this` ).

2. Returns the newly created object unless the constructor function returns a non-null reference . In that case , reference is returned instead.

3. Prototype of the object will be equal to the prototype of constructor function

# Function Prototype

Every functions have a prototype property which points to an object . The object has a constructor property and  `__proto__`

Properties in function prototype are availiable to object instances created via the constructor function

```js
"use strict";

function Person(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;

}

Person.prototype.fullName =  function() {
    return this.firstName + " " + this.lastName;
}

var person = new Person("Vijay", "P R");
console.log(person.fullName());  // Vijay P R
```

If multiple object instances are created, they share same prototype . So same function is shared by all object which saves memory 
