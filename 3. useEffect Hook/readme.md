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

##  👉🏻  useEffect **with CleanUp**

**Can't perform a React state update on an unmounted component. This is a no-op, but it indicates a memory leak in your application. To fix, cancel all subscriptions and asynchronous tasks in a useEffect cleanup function.**

- The message is straightforward. We're trying to change the state of a component, even after it's been unmounted and unavailable.

- There are multiple reasons why this can happen but the most common are that we didn’t unsubscribe to a websocket component, or this were dismount before an async operation finished.

- **The useEffect hook is built in a way that if we return a function within the method, this function will execute when the component gets disassociated. This is very useful because we can use it to remove unnecessary behavior or prevent memory leaking issues.**

### Syntax
```js
useEffect(() => {
    API.subscribe()
    return function cleanup() {
        API.unsubscribe()
    }
})
```

### Folder Structure
```
components
    +|__MouseContainer.js
```

### HookMouse
```js
...
function HookMouse() {
  ...
  useEffect(() => {
    ...
    return () => {
      console.log('Components unmounting Code')
      window.removeEventListener('mousemove', logMousePosition)
    }
  }, [])
  ...
}
...
```

### MouseContainer
```js
import React, {useState} from 'react'
import HookMouse from './HookMouse'

function MouseContainer() {
  const [display, setDisplay] = useState(true)

  return(
    <div>
      <button onClick = {() => setDisplay(!display)}>Toggle Display </button>
      {display && <HookMouse/>}
    </div>
  )
}

export default MouseContainer
```
