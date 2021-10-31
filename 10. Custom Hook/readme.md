#   Custom Hook

-   A cutom Hook is basically a Javascript function whose name starts with "use".

-   A custom hook can also call other Hooks if required.

-   Used to Share logic - Alternative to HOCs & Render Props.

##  `useDocumentTitle` Custom Hook

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

