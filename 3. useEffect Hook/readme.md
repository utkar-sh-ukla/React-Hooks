#   useEffect Hook

-   The Effect Hook lets you perform **side Effects** in **Functional components**

-   It is a close replacement for `componentDidMount`, `componentDidUpdate` & `componentWillUnmount`

##  👉🏻 useEffect after render

### Folder Structure
```
components
    +|__HookCounterOne.js
```

### HookCounterOne
```js
import React, {useState, useEffect} from 'react'

function HookCounterOne() {
  const [count, setCount] = useState(0)

  useEffect(() => {
    document.title = `You clicked ${count} times`
  })

  return(
    <div>
      <button onClick={() => setCount(count + 1)}>Click {count} times </button>
    </div>
  )
}

export default HookCounterOne
```
