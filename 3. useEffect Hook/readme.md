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

##  👉🏻  useEffect **only once**

If you want to run an effect and clean it up only once (on mount and unmount), you can pass an empty array ([]) as a second argument. This tells React that your effect doesn’t depend on any values from props or state, so it never needs to re-run. This isn’t handled as a special case — it follows directly from how the dependencies array always works

### Folder Structure
```
components
    +|__HookMouse.js
```

### HookMouse
```js
import React, {useState, useEffect} from 'react'

function HookMouse() {
  const [x, setX] = useState(0)
  const [y, setY] = useState(0)

  const logMousePosition = e => {
    console.log('Mouse Event')

    setX(e.clientX)
    setY(e.clientY)
  }

  useEffect(() => {
    console.log('useEffect called')
    window.addEventListener('mousemove', logMousePosition)
  }, [])

  return (
    <div>
      Hooks X - {x} Y - {y}
    </div>
  )
}

export default HookMouse
```

