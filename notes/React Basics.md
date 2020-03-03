---
tags: [React]
title: React Basics
created: '2020-02-05T10:24:39.711Z'
modified: '2020-02-05T10:56:02.742Z'
---

# React Basics

## 1.JSX 

* JavaScript XML : XML like syntax for Javascript. syntactic sugar
* Each component returns JSX which specifies how UI should look like
* JSX is translated to `React.createElement`   ( https://babeljs.io/rep ) by Babel.
* We can use Javascript expressions in JSX

`React.createElement()` is a function which creates object called React element

```js

// Note: this structure is simplified
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world!'
  }
};

```

These objects are read and then used to construct the DOM

## 2. React elements

React elements specified by JSX are plain objects unlike browser DOM elements and are cheap to create
ReacDOM takes care of updating the DOM to match React elements.
A React component is composed of multiple React elements

## 3. React Components

* Conceptually they are Javascript functions accepting props as arguments and returning React elements describing how the UI should look like

* Component can refer other components

* Component props are `read-only`

## 4. Component State

* Do not modify state directly

```js

// Wrong
this.state.comment = 'Hello';

// Correct
this.setState({comment: 'Hello'});

```

* State updates may be asynchronous,  you should not rely on their values for calculating the next state.

```js

// Wrong
this.setState({
  counter: this.state.counter + this.props.increment,
});

// Correct
this.setState((prevState, props) => ({
  counter: prevState.counter + props.increment
}));
```



