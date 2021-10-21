# Introduction

Hooks are a new feature addition in React version 16.8 which allow you to use React features without having to write a class.

Ex: State of a component

- Hooks don't work on classes.

### Prequisites
- Basics of React.
- Functional & class components, props, state, etc.

## Why Hooks?

### Reason Set 1 : 

- Understand how **this** keyword works in JavaScript.
- Remember to bind event handlers in class components.
- Classes don't minify very well & make hot reloading very unreliable.

### Reason Set 2 :

- There is no particular way to reuse stateful component logic.
- HOC & render props pattern do address this problem.
- Makes the code harder to follow.
- There is need to share stateful logic in a better way.

### Reason Set 3 :

- Create components for complex scenarios such as data fetching & subscribing to events.
- Related code is not organized in one place.
  - Ex: Data Fetching - In componentDidMount & componentDidUpdate.
  - Ex: Event Listeners - In componentDidMount & componentWillUnmount.
- Because of stateful logic - Cannot break components into smaller ones.