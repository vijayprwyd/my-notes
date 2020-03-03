---
tags: [Javascript]
title: Inheritance in Javascript
created: '2019-10-13T07:09:18.000Z'
modified: '2019-10-13T09:42:56.582Z'
---

# Inheritance in Javascript

## Constructor Pattern

```js

function Person(firstName, lastName) {
  this.firstName = firstName;
  this.lastName =  lastName;
}

Person.prototype.fullName = function() {
  return this.firstName + " " + this.lastName;
}

function Professional(honorofic, firstName, lastName) {
  this.honorofic = honorofic;
  Person.call(this, firstName, lastName);
}

Professional.prototype = Object.create(Person.prototype);

Professional.prototype.professionalName = function() {
  return this.honorofic + " " + this.firstName + " " + this.lastName;
}

var professional = new Professional("Mr", "Vijay",  "PR");
console.log(professional.fullName());
console.log(professional.professionalName());
console.log(Professional.prototype.constructor);


```

## Prototype Pattern

```js

var Person = {
  fullName:  function() {
    return this.firstName + " " + this.lastName;
  }
}

var Vijay = Object.create(Person, {
  firstName: {
    value: "Vijay"
  },
  lastName: {
    value: "P R"
  }
});


console.log(Vijay.fullName());

Object.getPrototypeOf(Vijay) === Person; // true
Vijay.__proto__ === Person; // true


```

### Prototype Pattern Via Factory

Factories are functions that just returns a particular object

```js

var Person = {
  fullName:  function() {
    return this.firstName + " " + this.lastName;
  }
}


function PersonFactory(firstName, lastName) {
  var person = Object.create(Person);
  person.firstName = firstName;
  person.lastName = lastName;
  return person;

}

var Vijay = PersonFactory("Vijay", "P R");

console.log(Vijay.fullName());

```

## Prototype Inheritance

```js

var Person = {
  fullName:  function() {
    return this.firstName + " " + this.lastName;
  }
}

function PersonFactory(firstName, lastName) {
  var person = Object.create(Person);
  person.firstName = firstName;
  person.lastName = lastName;
  return person;

}

function ProfessionalFactory(honorofic ,firstName, lastName) {
  var professional = Object.create(PersonFactory(firstName, lastName));
  professional.honoroficName = honorofic;
  professional.titleName = function() {
        return this.honoroficName + " " + this.firstName + " " + this.lastName
  }
  return professional;
}

var Vijay = ProfessionalFactory("Mr", "Vijay", "P R");
console.log(Vijay);
console.log(Vijay.titleName());
console.log(Vijay.fullName());

```
