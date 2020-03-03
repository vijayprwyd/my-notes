---
tags: [ECMA Script]
title: ES8 Javascript ( ES 2017 )
created: '2020-01-25T06:39:40.452Z'
modified: '2020-02-04T03:59:32.245Z'
---

#   ES8 Javascript ( ES 2017 )


## 1. Object.values

* Get all values of the object

```js

const obj = {a: 1, b:2}
console.log(Object.values(obj)); // Array [1, 2]

```

## 2. Object.entries

* Turns object attributes into an array of attributes

```js

const obj = {a: 1, b:2}
console.log(Object.entries(obj)); // [Array ["a", 1], Array ["b", 2]]

let x = new Map(Object.entries(obj));
console.log(x.get("a")); // 1


```

## 3. padStart and padEnd

`string.padStart(length, startString)`


* padStart pads the string with another string at the begining till the target length is reached 

```js

const str1 = '5'; 
console.log(str1.padStart(4, '0')); // "0005"

const fullNumber = '2034399002125581';
const last4Digits = fullNumber.slice(-4);
const maskedNumber = last4Digits.padStart(fullNumber.length, '*');

console.log(maskedNumber); // "************5581"

```

* padEnd pads the string with another string at the end till target length is reached 


```js

const str1 = 'Breaded Mushrooms';

console.log(str1.padEnd(25, '.'));
console.log(str1);  // "Breaded Mushrooms........"

const str2 = '200';
console.log(str2.padEnd(5));  // "200  "

```

## 4. Object.getOwnPropertyDescriptors

* returns all own ( non-inherited ) property descriptors of an object

```js

const object1 = {
  a: 42,
  b: 50
};

const descriptors1 = Object.getOwnPropertyDescriptors(object1);
console.log(descriptors1);

```

## 5. Trailing commas in function parameter lists and calls

```js

function sum(x, y, ){
	return x + y;
}

console.log(sum(2, 3,)); // 5
console.log(sum(4, 5)); // 9

```

## 6. Shared memory and atomics

## 7. Async / Await

* worknig with async functions ; returns a Promise by default
