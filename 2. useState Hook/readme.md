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

