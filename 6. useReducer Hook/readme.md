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

##  🎯  useReducer(complex state & action)

### Folder Structure
```
components
    +|__CounterTwo.js
```

### CounterTwo
```js
import  React, {useReducer} from 'react'

const initialState = {
  firstCounter: 0,
  secondCounter: 10
}
const reducer = (state, action) => {
  switch(action.type) {
    case 'increment1':
      return {...state, firstCounter: state.firstCounter + action.value};
    case 'decrement1':
      return {...state, firstCounter: state.firstCounter - action.value};
    case 'increment2':
      return {...state, secondCounter: state.secondCounter + action.value};
    case 'decrement2':
      return {...state, secondCounter: state.secondCounter - action.value};
    case 'reset':
      return initialState
    default:
      return state
  }
}

function CounterTwo() {
  const [count, dispatch] = useReducer(reducer, initialState)

  return(
    <div>
      <div>First Counter - {count.firstCounter} </div>
      <div>SecondCount - {count.secondCounter} </div>
      <button onClick = {() => dispatch({type: 'increment1', value: 1})}> Increment Counter One </button>
      <button onClick = {() => dispatch({type: 'decrement1', value: 1})}> Decrement Counter One </button>
      <button onClick = {() => dispatch({type: 'increment1', value: 5})}> Increment Counter One by 5 </button>
      <button onClick = {() => dispatch({type: 'decrement1', value: 5})}> Decrement Counter One by 5</button>
      <button onClick = {() => dispatch({type: 'increment2', value: 1})}> Increment Counter Two </button>
      <button onClick = {() => dispatch({type: 'decrement2', value: 1})}> Decrement Counter Two </button>
      <button onClick = {() => dispatch({type: 'reset'})}> Reset </button>
    </div>
  )
}

export default CounterTwo
```

##  🎯  Multiple useReducer

### Folder Structure
```
components
    +|__CounterThree.js
```

### CounterThree
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

function CounterThree() {
  const [countOne, dispatchOne] = useReducer(reducer, initialState)
  const [countTwo, dispatchTwo] = useReducer(reducer, initialState)

  return(
    <div>
      <div>Counter One - {countOne} </div>
      <button onClick = {() => dispatchOne('increment')}> Increment </button>
      <button onClick = {() => dispatchOne('decrement')}> Decrement </button>
      <button onClick = {() => dispatchOne('reset')}> Reset </button>
      <div>Counter Two - {countTwo} </div>
      <button onClick = {() => dispatchTwo('increment')}> Increment </button>
      <button onClick = {() => dispatchTwo('decrement')}> Decrement </button>
      <button onClick = {() => dispatchTwo('reset')}> Reset </button>
    </div>
  )
}

export default CounterThree
```