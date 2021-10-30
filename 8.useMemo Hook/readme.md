#   useMemo Hook

-   It allows you to memoize expensive functions so that you can avoid calling them on every render.

### Folder Structure
```
components
    +|__Counter.js
```

### Counter
```js
import React, { useState, useMemo } from 'react'

function Counter() {
	const [counterOne, setCounterOne] = useState(0)
	const [counterTwo, setCounterTwo] = useState(0)

	const incrementOne = () => {
		setCounterOne(counterOne + 1)
	}

	const incrementTwo = () => {
		setCounterTwo(counterTwo + 1)
  }

  const isEven = useMemo(() => {
    let i = 0
    while (i < 2000000000) i++
    return counterOne % 2 === 0
  }, [counterOne])

	return (
		<div>
			<div>
        <button onClick={incrementOne}>Count One - {counterOne}</button>
        <span>{isEven ? 'Even' : 'Odd'}</span>
			</div>
			<div>
        <button onClick={incrementTwo}>Count Two - {counterTwo}</button>
			</div>
		</div>
	)
}

export default Counter
```

### Difference between useMemo & useCallback

While both useMemo and useCallback remember something between renders until the dependencies change, the difference is just what they remember.

-   `useMemo` will remember the `returned value from your function`.

-   `useCallback` will remember your `actual function`.

