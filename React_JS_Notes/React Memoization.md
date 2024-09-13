# Memoization
Optimization technique that executes a pure function once, and saves the result in memory. If we try to execute the function again with same arguments as before, the previously saved resutl will be returned, without executing the function again
* Memoize components with memo
* Memoize objects with useMemo
* MemoiZe function with useCallback

Uses:
* Prevents wasted render
* Improve app speed/ resposivness
___
# The Memo Function
* Used to create a component that will not re-render when its parent re-renders, as long as the prop stays the same between renders
* Only affects props! A memoized component will still re-render when tis own state changes or when a context that it's subscribed to change
```
const Archive = memo(function Archive({shows}){
	.
	.
	.
	.
	return (
		.
		.
		.
	);
})
```

[[React useMemoanduseCallback]]

