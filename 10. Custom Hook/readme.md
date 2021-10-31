#   Custom Hook

-   A cutom Hook is basically a Javascript function whose name starts with "use".

-   A custom hook can also call other Hooks if required.

-   Used to Share logic - Alternative to HOCs & Render Props.

##  🎯  `useDocumentTitle` Custom Hook

### Folder Structure
```
    src
    |__components
    |   +|__DocTitleOne.js
    |   +|__DocTitleTwo.js
   +|__hooks
        +|__useDocumentTitle.js

```

### DocTitleOne
```js
import React, {useState} from 'react'
import useDocumentTitle from '../hooks/useDocumentTitle';

function DocTitleOne() {
  const [count, setCount] = useState(0)
  useDocumentTitle(count)

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Count - {count}</button>
    </div>
  )
}

export default DocTitleOne
```

### DocTitleOne
```js
import React, {useState} from 'react'
import useDocumentTitle from '../hooks/useDocumentTitle';

function DocTitleTwo() {
  const [count, setCount] = useState(0)
  useDocumentTitle(count)
  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Count - {count}</button>
    </div>
  )
}

export default DocTitleTwo
```

### useDocumentTitle
```js
import {useEffect} from 'react'

function useDocumentTitle(count) {
  useEffect(() => {
    document.title = `Count ${count}`
  }, [count])
}

export default useDocumentTitle
```

##  🎯  `useCounter` Custom Hook

### Folder Structure
```
    src
    |__components
    |   +|__CounterOne.js
    |   +|__CounterTwo.js
    |__hooks
        +|__useCounter.js

```

### CounterOne
```js
import React from 'react'
import useCounter from '../hooks/useCounter'

function CounterOne() {
	const [count, increment, decrement, reset] = useCounter(0, 1)

	return (
		<div>
			<h2>Count = {count}</h2>
			<button onClick={increment}>Increment</button>
			<button onClick={decrement}>Decrement</button>
			<button onClick={reset}>Reset</button>
		</div>
	)
}

export default CounterOne
```

### CounterTwo
```js
import React from 'react'
import useCounter from '../hooks/useCounter'

function CounterTwo() {
	const [count, increment, decrement, reset] = useCounter(10, 10)

	return (
		<div>
			<h2>Count = {count}</h2>
			<button onClick={increment}>Increment</button>
			<button onClick={decrement}>Decrement</button>
			<button onClick={reset}>Reset</button>
		</div>
	)
}

export default CounterTwo
```

### useCounter
```js
import { useState } from 'react'

function useCounter(initialCount = 0, value) {
	const [count, setCount] = useState(initialCount)

	const increment = () => {
		setCount(prevCount => prevCount + value)
	}

	const decrement = () => {
		setCount(prevCount => prevCount - value)
	}

	const reset = () => {
		setCount(initialCount)
	}
	return [count, increment, decrement, reset]
}

export default useCounter
```

##  🎯  `useInput ` Custom Hook

### Folder Structure
```
    src
    |__components
    |   +|__UserForm.js
    |__hooks
        +|__useInput .js

```

### UserForm
```js
import React, { useState } from 'react'
import useInput from '../hooks/useInput';

function UserForm() {
  const [firstName, bindFirstName, resetFirstName] = useInput('')
  const [lastName, bindLastName, resetLastName] = useInput('')

  const submitHandler = e => {
    e.preventDefault()
    alert(`Hello ${firstName} ${lastName}`)
    resetFirstName()
    resetLastName()
  }
	return (
		<div>
      <form onSubmit={submitHandler}>
				<div>
					<label>First Name</label>
					<input
            type="text"
            {...bindFirstName}
					/>
				</div>
				<div>
					<label>Last Name</label>
					<input
            type="text"
            {...bindLastName}
					/>
        </div>
        <button>Submit</button>
			</form>
		</div>
	)
}

export default UserForm
```

### useInput
```js
import {useState} from 'react'

function useInput(initialValue) {
  const [value, setValue] = useState(initialValue)
  const reset = () => {
    setValue('')
  }
  const bind = {
    value,
    onChange: e => {
      setValue(e.target.value)
    }
  }
  return [value, bind, reset]
}

export default useInput
```