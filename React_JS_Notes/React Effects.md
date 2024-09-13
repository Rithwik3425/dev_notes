# Effect
executed after the component mounts (initial render), and after subsequent re-renders (according to dependency  array)

```
useEffect( function (){
	fetch("https://www.ombdapi.com/?s=`inception`).
		then((data) => res.json).
			then((data) => setMovies(data.search));
	
	return () => console.log("clean up");
},[]); 

//[] is the dependency array
```

___
### Dependency Array
used to keep a component synchronized with some external system (in this example, with the API movie data)
* By default, effects run after every render. We Can prevent that by passing a dependency array
* Without the dependency array, react doesn't know when to run the effect.
* Each time one of the dependicies changes, the effect will be executed again
==NOTE==
Every state variable and prop used inside the effect MUST be included in the dependency array
___
### Using "async" for data fetching
```
useEffect(function (){
	async function fetchMovies(){
		const res = await fetch(`https://www.ombdapi.com/?key=${key}&s=${query}`);
		const data = await res.json();
		setMovies(data.search);
	}
	
	fetchMovies();
},[]);
```

___
### Handling errors in data fetching
```
const [isLoading, setIsLoading] = useState(false);
const [erroe, setError] = useState("");

useEffect(function (){
	async function fetchMovies(){
		try{
			setIsLoading(true);
			const res = await fetch(`https://www.ombdapi.com/?key=${key}&s=${query}`);
			
			if(!res.ok){
				throw new Error("Something went wrong in fetching data");
			}
			
			const data = await res.json();
			if(data.Respnse == "False")
				throw new Error("Movie not found");
			
			setMovies(data.search);
			console.log(data);
		}
		catch(err){
			console.log(err.message);
			setError(err.message);
		}
		finally{
			setIsLoading(false);
		}
	}
	
	fetchMovies();
},[]);


<Main>
	<Box>
		{isLoading && <Loader />}
		{error && <ErrorMessage msg={error} />}
		{!isLoading && !error && <MovieList movies-{movies} />}
		
	//Only on of the above conditions will work at a time
	
	</Box>
</Main>
```

___
![[WhatsApp Image 2024-02-22 at 22.30.16_c210fd81.jpg]]

___

### Clean up Function
Function that we can return from an effect
* Runs on two different occasions
	* Before the effect is executed again
		* in order to clean up the result of the previous side effects
	* After a component has unmounted
		* in order to give us the opportunity to reset the side effect that we created
* A Clean up function is necessary whenever the side effect keeps happening after the component has been re-rendered or unmounted
	* ![[WhatsApp Image 2024-02-22 at 22.51.51_06a88ecd.jpg]]

==Note==
* Each effect should do only one thing. Use one **useEffect** hook for each side effect. This makes effects easier to clean up 

```
useEffect{
	function (){
		if(!title) return;
		document.title = `Movie|${title}`;
		
		return function (){
			document.title = "usePopcorn"
		};
	},
	[title]
};
```

___
[[REACT JS]]