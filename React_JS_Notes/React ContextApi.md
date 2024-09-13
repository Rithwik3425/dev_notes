# Context API
solves props drilling

* Allows components everywhere in the tree to read state that a context shares.
* Context Api is a system to pass data through the app without manually passing props down the tree
* Allows us to "broadcast" global state to the entire app
* Context API contains:
	* Provider: (a special react component) 
		* gives  all child components access to value
		* can sit everywhere in the component tree
	* Value:
		* data that we want to make available (usually state and functions)
	* Consumers:
		* all components that read the provided context value
* There are three steps to use context
	* use useContext hook or create context
```
const PostContext = createContext();
```

* Provide the context, now in App
```
return(
	<PostContext.Provider value={{
		numcount: count,
		darkmode,
	}}>
		<Counter />
		<DarkModeon />
	</PostContext.Provider>
)
```
* Consuming the context, in the counter
```
const {numcount} = useContext(PostContext);
```