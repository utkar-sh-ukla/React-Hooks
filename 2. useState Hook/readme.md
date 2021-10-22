# useState Hook 

### Rules of Hooks

- Only call Hooks at the Top Level
  - Don't call Hooks inside loops, conditions, or nested functions.

- Only Call Hooks from React functions
  - Call them from within React functional components & not just any regular Javascript function.


### Folder Structure
```
components
    +|__HookCounter
```

### HookCounter
```js
import React, {useState} from 'react'

function HookCounter() {

  const [count, setCount] = useState(0)

  return(
    <div>
      <button onClick = {() => setCount(count + 1)}>Count : {count} </button>
    </div>
  )
}

export default HookCounter
```


## useState with *prevState*

### Folder Structure
```
components
    +|__HookCounterTwo
```

### HookCounterTwo
```js
import React, {useState} from 'react'

function HookCounterTwo() {
  
  const initialCount = 0;
  const [count, setCount] = useState(initialCount)

  const IncrementByFive = () => {
    for(let i=0; i<5; i++){
      setCount(prevCount => prevCount + 1)
    }
  }

  return(
    <div>
      Count: {count}
      <button onClick = {() => setCount(initialCount)}>Reset</button>
      <button onClick = {() => setCount(prevCount => prevCount + 1)}>Increment</button>
      <button onClick = {() => setCount(prevCount => prevCount - 1)}>Decrement</button>
      <button onClick = {IncrementByFive}>IncrementByFive</button>
    </div>
  )
}

export default HookCounterTwo
```
## useState with *object*

### Folder Structure
```
components
    +|__HookCounterThree
```

### HookCounterThree
```js
import React, {useState} from 'react'

function HookCounterThree() {
  
  const [name, setName] = useState({firstName: '', lastName: ''})

  return(
    <form>
      <input type='text' value={name.firstName} onChange={e => setName({...name, firstName: e.target.value})} />
      <input type='text' value={name.lastName} onChange={e => setName({...name, lastName: e.target.value})} />
      <h2>Your firstName is - {name.firstName} </h2>
      <h2>Your lastName is - {name.lastName} </h2>
      <h2>{JSON.stringify(name)}</h2>
    </form>
  )
}

export default HookCounterThree
```
