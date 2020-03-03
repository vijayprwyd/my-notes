---
tags: [Javascript]
title: Javasctipt Types and Equality
created: '2019-09-28T12:10:01.508Z'
modified: '2019-09-28T18:49:29.447Z'
---

# Javasctipt Types and Equality

## Primitive Types :

boolean, number, string, null, undefined, object, Symbol (in ES6 )

```js
typeof(null) // object
```


Javascript is dynamically typed .Type inferred by value assigned to the variable

```js

"use strict";

var a = 1;
console.log(typeof(a));  // number

a = 'abc';
console.log(typeof(a)); // string

```

```java
int a = 1;
a = "abc"; //Error Java is statically typed

```

## undefined vs null

* undefined neans no value
* used for uninitialized variable
* used for unknown variables and properties

Javascript never sets value of a variable to null. It is set explicitly by programmers
null has one and only one value which is null https://stackoverflow.com/questions/2797517/typeof-is-an-operator-and-a-function


## Equality vs Deep Equality

* === : Checks equality of type and value
* == : Checks equality of only values

```js

"use strict";

console.log(2 == '2');  // true
console.log(2 === '2');  // false


console.log(0 == '');  // true


```

`2 == '2'` Javascript tries to convert 2 to a string => `String(2) = '2'`
This is called type coercion `==` , tries to coerce both values so that they are of same type

It can create confusions

```js
false == 'false' // false  because Boolean('false') = true and false == true is false
```

Here String `false` is tried to convert to boolean using ```Boolean(false)``` which evaluates to `true`

# Comparison Rules

[Equality Check Rules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness#Loose_equality_using)

# Nan
 

 ```js
 typeof(NaN) // number

 console.log("abc" / 4) //Nan

 NaN == NaN // false

 ```

*  Not a number
* Result of a bad calculation
* Nan compared to anything is false
* `isNaN(arg)` can be used to check for `NaN`. The  `arg` is coerced to a number.
* Check a number is NaN or not :

```js

if(a !== a){  // NaN == NaN is false whereas its not the case for any other types 
  console.log("Not a number");
}  

```

Why NaN is not equal to NaN

```js

var a = 'asdf';
var b = null;

var intA = parseInt(a);
var intB = parseInt(b);

console.log(intA); //logs NaN
console.log(intB); //logs NaN
console.log(intA==intB);// logs false ; makes sense as asdf is not equal to null

```