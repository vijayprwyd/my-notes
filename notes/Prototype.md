---
tags: [Javascript]
title: Prototype
created: '2019-10-06T15:32:46.460Z'
modified: '2019-10-09T04:17:54.497Z'
---

# Prototype

* All objects in JS are instances of `Object`. Every object has a prototype which can be accessed via `__proto__`
* Prototype Chain: When searching for a property in an object, first the object is searched then its prototype. If it points to another object, then it searches there and so on.

```js 

"use strict";

var animal = {
  kind: "human"
}

var person = {};

person.__proto__ = animal;

//Recommmended way
Object.create(animal, {prop1: val1}) // => Created new object with animals prototype

console.log(person.kind);
console.log(animal.isPrototypeOf(person));

animal.kind = "dog";
console.log(person.kind);  // Dynamic . person property changed when animal kind changes

person.kind = "cat";
console.log(animal.kind); // not reflected in parent; property added to the object and not prototype

```

