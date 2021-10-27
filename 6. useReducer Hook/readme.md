#   useReducer Hook

-   `useReducer` is a hook that is used for **state management**.
-   It's an alternative to `useState`.

|Hooks|relation to JS|
|---|---|
|useState|state|
|useEffect|side effects|
|useContext|context API|
|useReducer|reducers|

##  reduce vs useReducer

|reduce in JavaScript|useReducer in React|
|---|---|
|array.**reduce**(*reducer*, initialValue)|**useReducer**(*reducer*,initialState)|
|singleValue = *reducer*(accumulator, itemValue)|newState = *reducer*(currentState, action)|
|**reduce** method returns a single value|**useReducer** returns a pair of values [newState, dispatch]|