---
tags: [ECMA Script]
title: ES9 Javascript ( ES 2018 )
created: '2020-01-25T07:18:37.443Z'
modified: '2020-02-13T10:28:20.527Z'
---

# ES9 Javascript ( ES 2018 )


1. Template Literal Revision
2. Asynchronous Iteration
3. Promise.prototype.finally
4. Rest / Spread Properties for objects
5. Regex features



## Template Literal Revision

When a template literal is preceeded by an expression it is called `tagged template literal` 



```js

function fn(str, ...val) {
    console.log(str); // ["Hi ", " !!! and ", " xyz", raw: Array(3)]
    console.log(val); // ["vpr", "wyd", "vpr"]
}

let name = "vpr", name1 = "wyd";

fn`Hi ${name} !!! and ${name1} \n .fwwe ${name} rw` // ["Hi ", " !!! and ", " ↵ .fwwe ", " rw", raw: Array(4)]
fn`Hi ${name} !!! and ${name1} \ubuntu .fwwe ${name} rw` // ["Hi ", " !!! and ", undefined, " rw", raw: Array(4)]


```

Illegal escape sequences in a regular template literal causes an error whereas it the value of illegal sequence will be replaced with `undefined` for tagged template litera.

`let bad = bad escape sequence: \ubuntu; // error`


## Asynchronous Iteration

```js

function getAPI(value, delay) {
    return new Promise((resolve, reject) => {
        return setTimeout(() => {
                console.log("Resolved " + value);
               resolve(value);
        }, delay);
    })
}


async function xyz() {

    let y = [getAPI("value 1", 3000), getAPI("value 2", 2000), getAPI("value 3", 1000)]
    let j = 0;

    for await (let i of y) {
        console.log(`Iteration ${++j} : i = ${i}`);
    }
}


xyz();
```

* Array of Promises can resolve  at any time , but the first promise is awaited and valuated, then the next one and so on .
* When any of the promise is rejected , exception is thrown and further promises are not considered . 
* Differs from `promise.all()` in the sense if any of the promise is rejected, `then` is not evaluated , and only `catch` is . `await of` may be used when we want to evaluate certain APIs , when its expected some can fail


```js

function getAPI(value, delay) {
    return new Promise((resolve, reject) => {
        return setTimeout(() => {
                console.log("Value in promise req " + value);
               value === 2 ? reject(value) : resolve(value);
        }, delay);
    })
}


Promise.all([getAPI(1, 3000),getAPI(2, 2000), getAPI(3, 1000)]).then(([val1, val2, val3]) => {
   console.log("Entering then ")
   console.log(val1);
   console.log(val2);
   console.log(val3); 
}).catch(error => {
   console.log("Error " + error); 
});


```


### Promise.prototype.finally


```js

function getAPI(value, delay) {
    return new Promise((resolve, reject) => {
        return setTimeout(() => {
               value === 2 ? reject(value) : resolve(value);
        }, delay);
    })
}

getAPI(1, 1000).then(res => console.log("Value " + res)) // Value 1
        .catch(error => console.log("Error: " + error))
        .finally(() => console.log("Finally")); //  Finally

getAPI(2, 1000).then(res => console.log("Value " + res))
        .catch(error => console.log("Error: " + error)) //Error: 2
        .finally(() => console.log("Finally")); // Finally

```

### Rest / Spread Properties for Objects


```js

let { x, y, ...rest } = { x: 1, y: 2, a: 3, b: 4 };
x; // 1
y; // 2
rest; // { a: 3, b: 4 }

//Spread
let n = { x, y, ...rest };
n; // { x: 1, y: 2, a: 3, b: 4 }

```

### Regex Features


