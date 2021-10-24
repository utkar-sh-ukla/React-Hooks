#   useEffect Hook

-   The Effect Hook lets you perform **side Effects** in **Functional components**

-   It is a close replacement for `componentDidMount`, `componentDidUpdate` & `componentWillUnmount`

- By using this Hook, you tell React that your component needs to do something after render. React will remember the function you passed (we’ll refer to it as our “effect”), and call it later after performing the DOM updates. In this effect, we set the document title, but we could also perform data fetching or call some other imperative API.

- Placing useEffect inside the component lets us access the count state variable (or any props) right from the effect. We don’t need a special API to read it — it’s already in the function scope. Hooks embrace JavaScript closures and avoid introducing React-specific APIs where JavaScript already provides a solution.

- **Does useEffect run after every render?** Yes! By default, it runs both after the first render and after every update. Instead of thinking in terms of “mounting” and “updating”, you might find it easier to think that effects happen “after render”. React guarantees the DOM has been updated by the time it runs the effects.


##  👉🏻  useEffect **after render**

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

##  👉🏻  useEffect **conditional rendering**

If you pass an empty array ([]), the props and state inside the effect will always have their initial values. While passing [] as the second argument is closer to the familiar componentDidMount and componentWillUnmount mental model, there are usually better solutions to avoid re-running effects too often.

### HookCounterOne.
```js
import React, {useState, useEffect} from 'react'

function HookCounterOne() {
  const [count, setCount] = useState(0)
  const [name, setName] = useState('')

  useEffect(() => {
    console.log('useEffect - Updating document title')
    document.title = `You clicked ${count} times`
  }, [count])

  return(
    <div>
      <input type='text' value={name} onChange = {e => setName(e.target.value)} />
      <button onClick={() => setCount(count + 1)}>Click {count} times </button>
    </div>
  )
}

export default HookCounterOne
```