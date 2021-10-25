#   useContext Hook

Context provides a way to pass data through the component tree without having to pass props down manually at every level.

## 👉🏻   Context
```
components
    +|__ComponentC.js
    +|__ComponentE.js
    +|__ComponentF.js
```

### App
```js
import React from 'react';
import './App.css';
import ComponentC from './components/ComponentC'

export const UserContext = React.createContext()
export const ChannelContext = React.createContext()

function App() {
  return (
    <main>
      <UserContext.Provider value={'Jerry'}>
        <ChannelContext.Provider value={'Cartoon Network'}>
          <ComponentC />
        </ChannelContext.Provider >
      </UserContext.Provider>
    </main>
  );
}

export default App;
```

### ComponentC
```js
import React from 'react'
import ComponentE from './ComponentE'

function ComponentC(){
  return <ComponentE />
}

export default ComponentC
```

### ComponentE
```js
import React from 'react'
import ComponentF from './ComponentF'

function ComponentE(){
  return <ComponentF />
}

export default ComponentE
```

### ComponentF
```js
import React from 'react'
import { UserContext, ChannelContext } from '../App'

function ComponentF() {
	return (
		<div>
			<UserContext.Consumer>
				{user => {
					return (
						<ChannelContext.Consumer>
							{channel => {
                return <div>User context value {user}, channel context value {channel}</div>
							}}
						</ChannelContext.Consumer>
					)
				}}
			</UserContext.Consumer>
		</div>
	)
}

export default ComponentF
```

##  👉🏻  using useContext Hook

### ComponentE
```js
import React, { useContext } from 'react'
import ComponentF from './ComponentF'
import { UserContext, ChannelContext } from '../App'

function ComponentE() {

  const user = useContext(UserContext)
  const channel = useContext(ChannelContext)
  return <div>  {user} - {channel}</div>
  
}

export default ComponentE
```