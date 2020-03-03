---
tags: [ES6]
title: Proxy
created: '2020-02-11T04:00:24.269Z'
modified: '2020-02-11T05:36:12.696Z'
---

# Proxy

* Proxies are a kind of middleware to intercept objects
* Define custom behaviour for fundamental operations ( get, set etc)
* Traps refers to the methods that provide property access


```js

let handler = {

  // has a property each trap you want to set
  //get will run anytime the object is being accessed


  get(target, propName) {
    console.log(`Property ${propName} get on Object`);

    return target[propName];
  },

  set(target, propName, propValue) {
    console.log(`Getting Property ${propName} of Object`);
    target[propName] = propValue;
  }

};

let proxyObj = new Proxy({}, handler);  // object to proxy, object serving as the handler / middleman
proxyObj.name = "Vijay P R";  // O/P :Getting Property name of Object

proxyObj.gender = 'Male'; // O/P :Getting Property gender of Object


console.log(proxyObj.name); // Property name get on Object



```

## Uses :

1. Adding Custom Validations 


```js

let handler = {

  get(target, propName) {
    console.log(`Property ${propName} get on Object`);

    return target[propName];
  },

  set(target, propName, propValue) {
    if(propName === "age" && typeof(propValue) !== "number") {
      throw new TypeError("Age must be number");
    }
  

    target[propName] = propValue;
  }

};

let proxyObj = new Proxy({}, handler);

proxyObj.age = "abc";  // TypeError is thrown




```



2. Block Function Calls. Separate Validations from logic


```js

let handler = {

    apply(target, thisArg, arguments) {
        if (arguments[0] % 2 === 0) {
            throw new TypeError("Argument 1 is not odd");
        }
        return target(arguments[0], arguments[1]);
    }
}

function sum(x, y) {
    return x + y;
}

let sumProxy = new Proxy(sum, handler);
console.log(sumProxy(4, 7)); // Throws typeError if first argument is even 

```
