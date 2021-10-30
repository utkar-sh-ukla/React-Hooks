#   useRef Hook

It is a function which takes a maximum of one argument and returns an `Object`. The returned object has a property called `current` whose value is the argument passed to `useRef`. If you invoke it without an argument, the returned object's `current` property is set to `undefined`. 

### useRef usecase
-   To access DOM elements.
-   To persist values in successive renders.

##  🎯  Focus Input

### Folder Structure
```
components
    +|__FocusInput.js
```

### Focus Input Instance
```js
import React, { useRef, useEffect } from 'react'

function FocusInput() {
	const inputRef = useRef(null)
	useEffect(() => {
		inputRef.current.focus()
	}, [])
	return (
		<div>
			<input ref={inputRef} type="text" />
		</div>
	)
}

export default FocusInput
```

##  🎯  Stopwatch 

### Folder Structure
```
components
    +|__HookTimer.js
```
### HookTimer
```js
import React, {useState, useEffect, useRef} from 'react'

function HookTimer() {
  const [timer, setTimer] = useState(0)
  const interValRef = useRef()
  useEffect(() => {
    interValRef.current = setInterval(() => {
      setTimer(timer => timer + 1)
    }, 1000)
    return () => {
      clearInterval(interValRef.current)
    }
  }, [])
  return (
    <div>
      HookTimer - {timer} -
      <button onClick={() => clearInterval(interValRef.current)}>Clear Timer</button>
    </div>
  )
}

export default HookTimer
```