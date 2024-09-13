# useMemo and useCallback
used to memoize values (usememo) and functions (useCallback) between renders

* Values passed into useMemo and useCallback will be stored in memory ("cached") and returned in subsequent re-renders, as long as dependecies ("inputs") stay the same
* useMemo and useCallback have a dependancy array(like useEffect) whenever one dependancy, changes the values will be re-created.

### Usage
* Memoizing props to prevent wasted renders (together with memo)
* Memoizing values to avoid expensive re-caluculations on every render
* Memoizing values that are used in dependancy array of another hook
```
cons Archive = useMemo(() => {
	return{
		show: false,
		title: `Post archieve addition to ${Posts.length}`
	};
},[posts.lenths]);

const handleAddPosts = useCallback(function handleAddPosts(port){
	setPosts((posts) => [posts,...posts]);
},[]);
```
___
### Bundle
* Java-script file containing the entire application code. Downloading the bundle will load the entire app at once, turning it into a sPA (Single Page Application)
* Bundle Size:
	* Amount of Java-script users have to download to start using the app. One of the most important things to be optimized, so that the bundle takes less time to download