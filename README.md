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

```JSX
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
- class components can work along with functional components. theres no restriction.
- a class component can have a function component inside render method.
- a functional component can have a class component inside jsx return statement.

---

## -- Video 165 Woking with State and Events in Class Components

- For managing state in class components we use/take helpof js constructor method. Which is the most first method called whenever react encounters that your class is used as a component.

- constructor method is a special method which is called whenever a new instance of a class is created.

```JSX
constructor(){
  // here the name state accessible on "this" keyword has to be named as state . This is a reserved keyword in react.
  super();
  this.state={}
}
```

- In reacts class components state is always an object & is initialized like above inside a class component at the very begining.

- for updating state in class components we use this.setState() method provided by react's component class which we extend in our class component. We pass an object to this method which will be merged with the current state.

```Jsx
  constructor() {
    super();
    this.state = {
      showUsers: true,
    };
  }

  toggleUsersHandler = () => {
    this.setState((curState) => {
      return { showUsers: !curState.showUsers };
    });
  };
```

- we can also pass a function to this.setState() method which will receive the current state as an argument & will return an object which will be merged with the current state.

- full component code

```JSX
import { Component } from "react";
import User from "./User";

import classes from "./Users.module.css";

const DUMMY_USERS = [
  { id: "u1", name: "Max" },
  { id: "u2", name: "Manuel" },
  { id: "u3", name: "Julie" },
];

class Users extends Component {
  constructor() {
    super();
    this.state = {
      showUsers: true,
    };
  }

  toggleUsersHandler = () => {
    this.setState((curState) => {
      return { showUsers: !curState.showUsers };
    });
  };

  render() {
    const { showUsers } = this.state;

    const usersList = showUsers && (
      <ul>
        {DUMMY_USERS.map((user) => (
          <User key={user.id} name={user.name} />
        ))}
      </ul>
    );

    return (
      <div className={classes.users}>
        <button onClick={this.toggleUsersHandler.bind(this)}>
          {showUsers ? "Hide" : "Show"} Users
        </button>
        {usersList}
      </div>
    );
  }
}
export default Users;
```

---

## -- Video 166 The Component LifeCycle (Class-based components only)

- For handling side effects in functional components we use useEffect()
- For handling side effects in class components we use lifecycle methods as we cannot use hooks in class-based components.
- Below are the lifecycle methods in class components.

1. **componentDidMount()**

   - This method is called after a component is rendered for the first time.
   - This is the best place to send http requests to fetch data from a server.
   - This method is called only once in the lifecycle of a component.
   - this is equivalent to useEffect() with empty dependency array.

   ```JSX
   componentDidMount(){
       // send http request
   }
   useEffect(()=>{
       // send http request
   },[])
   ```

2. **componentDidUpdate()**

   - This method is called after a component is updated.
   - This is the best place to send http requests to fetch data from a server.
   - This method is called every time a component is updated.
   - this is equivalent to useEffect() with dependency array.

   ```JSX
   componentDidUpdate(){
       // send http request
   }
   useEffect(()=>{
       // send http request
   },[dependencyArray])
   ```

3. **componentWillUnmount()**
   - This method is called before a component is removed from the DOM.
   - This is the best place to clean up side effects.
   - This method is called only once in the lifecycle of a component.
   - this is equivalent to useEffect() with empty dependency array.
   ```JSX
   componentWillUnmount(){
       // clean up side effects
   }
   useEffect(()=>{
     // code to run on component unmount
       return()=>{
           // clean up side effects
       }
   },[])
   ```
