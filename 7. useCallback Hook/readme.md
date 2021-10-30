#   useCallback

-   useCallback is a hook that will return a memoized version of the callback function that only changes if one of the dependencies has changed.

-   It is useful when passing callbacks to optimized child components that rely on referenece equality to prevent unnecessary renders.

### Folder Structure
```
components
    +|__Button.js
    +|__Count.js
    +|__ParentComponent.js
    +|__Title.js
```

### Button
```js
import React from 'react'

function Button({ handleClick, children }) {
  console.log('Rendering button - ', children)
  return (
    <button onClick={handleClick}>
      {children}
    </button>
  )
}

export default React.memo(Button)
```

### Count
```js
import React from 'react'

function Count({ text, count }) {
	console.log(`Rendering ${text}`)
	return <div>{text} - {count}</div>
}

export default React.memo(Count)
```

### ParentComponent
```js
import React, { useState, useCallback } from 'react'
import Count from './Count'
import Button from './Button'
import Title from './Title'

function ParentComponent() {
	const [age, setAge] = useState(25)
	const [salary, setSalary] = useState(50000)

	const incrementAge = useCallback(() => {
		setAge(age + 1)
	}, [age])

	const incrementSalary = useCallback(() => {
		setSalary(salary + 1000)
	}, [salary])

	return (
		<div>
			<Title />
			<Count text="Age" count={age} />
			<Button handleClick={incrementAge}>Increment Age</Button>
			<Count text="Salary" count={salary} />
			<Button handleClick={incrementSalary}>Increment Salary</Button>
		</div>
	)
}

export default ParentComponent
```

### Title
```js
import React from 'react'

function Title() {
  console.log('Rendering Title')
  return (
    <h2>
      useReducer Hook
    </h2>
  )
}

export default React.memo(Title)
```
### When to `useMemo` and `useCallback` ?

blog_link : https://kentcdodds.com/blog/usememo-and-usecallback