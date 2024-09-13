(Mutable object in React)
* Like a box into which we can put any data that want to be preserved between renders
	* Object with a mutable current property that is persisted across render ("normal" variables are always reset)

###### Two big use cases
* Creating a variable that stays the same between render (Ex: previous state, setTimedout id, etc)
* Selecting and string DOM elements

* Refs are for "data that is not rendered" usually only appear in event handlers or effect, not in JSX (otherwise use state)
* Do not read write or read.current in render logic (like state)


```
function Search({query, setQuery}){
	const inputEL = useRef(null);
	
	useEffect(function (){
		console.log(inputEL.current);
		inputEL.current.focus;
	},[]);
	
	
	return (
		<input
			className = "search"
			type = "text"
			placeholder = "search movies...."
			value={query}
			onchange = {(e) => setQuery(e.target.value);}
			ref={inputEL}
		/>
	);
}
```
