## -- Video 162 Module Introduction

What we will learn in this module.

1. What are class components.
2. why do we need class components.
3. what are error boundaries.
4. why do error boundries only work with class components.

---

## -- Video 163 What and Why

#Functional Components

```Javascript

function Product(props) {
    return <h2> A Product! </h2>
}

```

Here components are regular js functions which return renderable results (typically JSX)

#Class-based Components

```Javascript

class Product extends Component{
    render(){
        return <h2> A Product! </h2>
    }
}

```

Here, components are ES6 classes which extend the Component class from the React library.
components can also be defined as JS classes where a render() method defines the to-be-rendered output

## Key Points

1. there were only class components in React before version 16.8
2. before version 16.8, class components were the only way to use state and lifecycle hooks
3. but after version 16.8, functional components can also use state and lifecycle hooks
4. so, class components are not necessary anymore
5. but, class components are still useful for error boundaries
6. so, we will learn about class components in this module
7. class based components cannot use react hooks.

---

## -- Video 164 Adding first Class Component

class component

```javascript
import React, { Component } from "react";

class Product extends Component {
  render() {
    return (
      <div>
        <h2> {this.props.head} </h2>
        <h2> A Product! </h2>
      </div>
    );
  }
}
```

# VS

functional component

```javascript
import React from "react";

const Product = (props) => {
  return (
    <div>
      <h2> {props.head}</h2>
      <h2> A Product! </h2>
    </div>
  );
};
```

- we must use the extends component keyword to create a class component which allows us to access props and state.
