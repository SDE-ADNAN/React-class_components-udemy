## video 162 Module Introduction

What we will learn in this module.

1. What are class components.
2. why do we need class components.
3. what are error boundaries.
4. why do error boundries only work with class components.

## Video 163 What and Why

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
