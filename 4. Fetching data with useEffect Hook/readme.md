#   Fetching Data with useEffect Hook

### Setup
`npm install axios`

##  👉🏻 Get Request for all Posts

### Folder Structure
```
components
    +|__DataFetching.js
```

### DataFetching
```js
import React, {useState, useEffect} from 'react'
import axios from 'axios'

function DataFetching() {
  const [posts, setPosts] = useState([])

  useEffect(() => {
    axios.get('https://jsonplaceholder.typicode.com/posts')
    .then(res => {
      console.log(res)
      setPosts(res.data)
    })
    .catch(err => {
      console.log(err)
    })
  }, [])

  return(
    <div>
      <ul>
        {posts.map(post => (
          <li key={post.id}>{post.title}</li>
        ))}
      </ul>
    </div>
  ) 
}

export default DataFetching
```

##  👉🏻 Get Request for single Post

### DataFetching
```js
import React, {useState, useEffect} from 'react'
import axios from 'axios'

function DataFetching() {
  const [post, setPost] = useState([])
  const [id, setId] = useState(1)

  useEffect(() => {
    axios.get(`https://jsonplaceholder.typicode.com/posts/${id}`)
    .then(res => {
      console.log(res)
      setPost(res.data)
    })
    .catch(err => {
      console.log(err)
    })
  }, [id])

  return(
    <div>
      <input type='text' value={id} onChange={e => setId(e.target.value)} />
      <div>{post.title}</div>
      {/*<ul>
        {posts.map(post => (
          <li key={post.id}>{post.title}</li>
        ))}
      </ul>*/}
    </div>
  ) 
}

export default DataFetching
```