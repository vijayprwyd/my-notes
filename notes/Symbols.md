---
tags: [ES6, Javascript]
title: Symbols
created: '2019-11-06T04:45:31.811Z'
modified: '2019-11-06T05:47:05.632Z'
---

# Symbols

* Primitive type introduced in ES6
* Represents / Provides a unique identifier
* Symbols are not iterable ( `for in `)
* Can be used to store some meta information about the object

```js

let symbol = Symbol('debug');

console.log(symbol);  // Symbol(debug)
console.log(typeof(symbol)); // symbol


let anotherSymbol = Symbol('debug');
console.log(symbol == anotherSymbol); // false


```

```js

let obj = {
    a: 10,
    b: 20,
    [symbol]: 'someValue'
}

for(let key in obj) {
    console.log(key);  // a b => Symbols are not iterable
}

console.log(obj[symbol]);   // someValue
console.log(obj.symbol);    // undefined

```

``` js

let symbol = Symbol.for('age');

let person = {
    name: 'Vijay',
    age: 30
};

function makeAge(person) {
    let ageSymbol = Symbol.for('age');  // Prevents accidental modification of age objec tin the person
    person[ageSymbol] = 25;
}

makeAge(person);
console.log(person[symbol]);  // 25
console.log(person['age']);  // 30

```
Well known symbols can be used to override the default behaviour on built in objects
