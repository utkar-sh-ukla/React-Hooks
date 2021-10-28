#   useReducer Hook

-   `useReducer` is a hook that is used for **state management**.
-   It's an alternative to `useState`.

|Hooks|relation to JS|
|---|---|
|useState|state|
|useEffect|side effects|
|useContext|context API|
|useReducer|reducers|

##  😯  reduce vs useReducer

|reduce in JavaScript|useReducer in React|
|---|---|
|array.**reduce**(*reducer*, initialValue)|**useReducer**(*reducer*,initialState)|
|singleValue = *reducer*(accumulator, itemValue)|newState = *reducer*(currentState, action)|
|**reduce** method returns a single value|**useReducer** returns a pair of values [newState, dispatch]|

##  🎯  useReducer(simple state & action)

### Folder Structure
```
components
    +|__CounterOne.js
```

### CounterOne
```js
import  React, {useReducer} from 'react'

const initialState = 0;
const reducer = (state, action) => {
  switch(action) {
    case 'increment':
      return state + 1;
    case 'decrement':
      return state - 1;
    case 'reset':
      return initialState
    default:
      return state
  }
}

function CounterOne() {
  const [count, dispatch] = useReducer(reducer, initialState)

  return(
    <div>
      <div>Count - {count} </div>
      <button onClick = {() => dispatch('increment')}> Increment </button>
      <button onClick = {() => dispatch('decrement')}> Decrement </button>
      <button onClick = {() => dispatch('reset')}> Reset </button>
    </div>
  )
}

export default CounterOne
```