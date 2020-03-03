---
tags: [ECMA Script]
title: ES10 Javascript ( ES 2019 )
created: '2020-01-25T03:54:21.180Z'
modified: '2020-01-25T06:32:22.886Z'
---

# ES10 Javascript ( ES 2019 )

```

1. Array flat
2. Array flatMap
3. Object.fromEntries
4. trimStart() and trimEnd()
5. trimStart and trimEnd

```


## 1. Array flat

* Flattens an arrat upto given depth. If depth is `Infinity` completely flattens the array.


```js

const array = [1, [2, [3, 4, [5]]] , 6, 7];

console.log(array.flat(1)); //[1, 2, Array [3, 4, Array [5]], 6, 7]
console.log(array.flat(2)); // Array [1, 2, 3, 4, Array [5], 6, 7]
console.log(array.flat(Infinity)); // Array [1, 2, 3, 4, 5, 6, 7]


```



* Removes empty slots in the array

```js

const array1 = [1, 4, , 16];
console.log(array1.flat());  // [1, 4, 16]

```

* Iterative implementation of `Array.flat` ( For polyfill replace array with this)

```js

function flatten(array, depth = Infinity) {

    let flat = [];

    if(depth === 0 ) return array;

    for(let ele of array) {
        Array.isArray(ele) ? flat.push(...flatten(ele, depth - 1)) : flat.push(ele);      
  }
  
 return flat;
}

```

## 2. Array flatMap


* map followed by flat of depth 1


```js

let arr1 = ["it's Sunny in", "", "California"];

arr1.map(x => x.split(" "));
// [["it's","Sunny","in"],[""],["California"]]

arr1.flatMap(x => x.split(" "));
// ["it's","Sunny","in", "", "California"]


```
* Iterative implementation / Polyfill

```js

function flatMap(mapFunction) {
 return this.map(ele => mapFunction(ele)).flatten(1);
}


```

## 3. Object.fromEntries

* Transforms a list of key-value pairs into an object

```js

const entries = new Map([
  ['foo', 'bar'],
  ['baz', 42]
]);

const obj = Object.fromEntries(entries);

console.log(obj); //Object { foo: "bar", baz: 42 }


let x = [['1',  'a'], ['2' , 'b'], ['3', 'c'], ['4',  'd']];
console.log(Object.fromEntries(x)); //  Object { 1: "a", 2: "b", 3: "c", 4: "d" }

```

* Iterative implementation of Object.fromEntries

```js

function fromEntries(array) {
  	let obj = {};
	for(let x of array) {
    	obj[x[0]] = x[1]
    }
  	return obj;
}

```

## 4. trimStart() and trimEnd()

* trimStart / trimLeft removes whitespace from the begining of a string

* trimEnd / trimRight removes whitespace from the end of a string

```js

const greeting = '   Hello world!   ';

console.log(greeting); //"   Hello world!   ";
console.log(greeting.trimStart()); // "Hello world!   ";
console.log(greeting.trimEnd()); //"   Hello world!"

```

* Iterative implmentation of `trimStart` and `trimEnd`

```js

function trimStart(str) {
	for(var i = 0; str[i] == ' ' && i < str.length; i++);
	return str.substring(i, str.lenght);
}

function trimEnd(str) {
	for(var i = str.length - 1; str[i] === ' ' && i >= 0; i--);
  	return str.substring(0, i);
}

```

## 5. Optional Catch Binding 

* Catch error without the binding parameter

```js

try {
  nonExistentFunction();
}
catch {}  // Error parameter is optional

```

## 6. Symbol description

* read-only description
* String returning optional description of symbol

```js

console.log(Symbol('desc').description); // "desc"

console.log(Symbol.iterator.description); // Symbol.iterator

console.log(Symbol.for('foo').description); // "foo"

console.log(Symbol('foo').description + 'bar'); // "foobar"

console.log(Symbol().description);        // undefined

```
