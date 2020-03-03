---
tags: [React]
title: React Phases
created: '2020-01-29T04:03:44.538Z'
modified: '2020-01-29T08:43:56.076Z'
---

# React Phases

DOM operations ( like `appendChild` ) are expensive. Reduce DOM updates as much as possible to improve performance

React batches DOM updates
If there is a state change, that results in 30 DOM updates , they would happen at once rather than running after one another

When a state change occurs ,

* **Render Phase** : React calls createElement to get the elements that need to be rendered on the DOM.

* **Reconcilation Phase** : These elements are compared with the previously generated elements. Uses Diffing Algorithm that runs in O(n)

https://reactjs.org/docs/reconciliation.html

https://babeljs.io/rep

* **Comitting Phase** : Decides what updated need to be performed on the DOM and performs it in the most efficient way



declarative , no need to worry about what changes on every update, focus more on logic

**JSX**

```js

ui = <div id="root">Hello world</div>
ui = React.createElement('div', {id: 'root'}, 'Hello world')


function createElement(elementType, props, ...children) {}

```

```js

ui = (
  <div>
    <span>Hello</span> <span>World</span>
  </div>
);

ui = React.createElement('div', null,  {
  children: [
    React.createElement('span', null, 'Hello'),
    ' ',
    React.createElement('span', null, 'World'),
  ],
});

// Returns an object that is passed to REACTDOM.render()

{
  type: "div",
  key: null,
  ref: null,
  props: { id: "root", children: "Hello world" },
  _owner: null,
  _store: {}
};


```

**Example 2**


```js

function MyComponent() {
    return <p>Hi</p>
}


function hello() {
    return <div id="xyz" abc="5" >
        <MyComponent />
        <span><ul></ul></span></div>;
}

```

```js

function MyComponent() {
  return React.createElement("p", null, "Hi");
}

function hello() {
  return React.createElement(
    "div",
    {
      id: "xyz",
      abc: "5"
    },
    React.createElement(MyComponent, null),
    React.createElement("span", null, React.createElement("ul", null))
  );
}


```



