---
tags: [ES6, Javascript]
title: Reflect
created: '2019-11-12T03:30:27.111Z'
modified: '2019-11-12T03:50:33.694Z'
---

# Reflect


## Reflect example

```JS

function Person(name) {
    this.name = name;
}

function Employee() {
    this.salary = 10000;
}

let person = Reflect.construct(Person, ['Vijay']);
console.log(person); // {name: "Vijay"}
console.log(person.__proto__ === Person.prototype); // true

console.log(person instanceof Person); // true


let anotherPerson = Reflect.construct(Person, ['Ajay'], Employee);
console.log(anotherPerson.__proto__ === Employee.prototype); // true
console.log(Object.getPrototypeOf(anotherPerson) === Employee.prototype); // true



```

## Reflect.apply

```js

function Person(name, age) {
    
    this.name = name;
    this.age = age;

    this.greet = function(prefix) {
        console.log(`${prefix} ${this.name} :  ${this.age}`);
    }
}

let person = Reflect.construct(Person, ['Vijay', '25']);
person.greet('Mr');  // Mr Vijay :  25

Reflect.apply(person.greet, {name: 'Ajay', age: 29}, ['Mr']); // Mr Ajay :  29



```

## Reflect getPrototype and setPrototype

```js

function Person(name, age) {
    
    this.name = name;
    this.age = age;

    this.greet = function(prefix) {
        console.log(`${prefix} ${this.name} :  ${this.age}`);
    }
}


let proto = {address: 'Mananthavady'}

let person = Reflect.construct(Person, ['Vijay', '25']);

Reflect.setPrototypeOf(person, proto);

console.log(Reflect.getPrototypeOf(person)); // {address: "Mananthavady"}

```
