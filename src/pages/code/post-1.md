1. Create Context
Begin with importing it and assigning it

App.jsx:

```jsx
import {createContext} from 'react'

const ExampleContext = createContext()
```


2. Provide value to child components (Assign Context)
Now we wrap everything within the return() with <ExampleContext.Provider></ExampleContext.Provider>

```jsx
return (
<ExampleContext.Provider>
	<Header title={title} navIcon={navIcon}/>
	<Main posts={searchedPosts}/>
	<Footer />
</ExampleContext.Provider>
)
```

Now lets take those props that are being passed down and populate out ExampleContext.Provider:

```jsx
return (
<ExampleContext.Provider value={{
title,
posts: searchedPosts
}}>
	<Header />
	<Main />
	<Footer />
</ExampleContext.Provider>
)
```


3. Consume Context Value
Now lets go to Header.jsx:

```jsx
import {useContext} from 'react'

function Header(){
const {title, navIcon} = useContext(ExampleContext)

return (
	<>
		<div>Welcome to {title}</div>
		<img src={navIcon} />
	</>
	)
}
```

Main.jsx
```jsx
import {useContext} from 'react'

function Main(){
const {posts} = useContext(ExampleContext)

return (
	<>
		<p>{posts.length} posts found!!</p>
	</>
	)
}
```



We can go a step further, and make a component of <ExampleProvider />

You can also add state inside of here

I still need to finish this up***