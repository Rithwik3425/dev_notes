# Cancelling the "race Condition"
The condition at which multiple http requests are sent
* This can be cancelled with the help of clean up function

```
useEffect{
	function (){
		const controller = new AbortController();
		
		async function fetchMovies(){
			try{
				setIsLoading(true);
				setError(" ");
				
				const res = await fetch(`http://www.ombdapi.com/?apiKey=${key}&s=${query}`,{signal: controller.signal});
			}
			catch(err){
				if(err.name !== "Abort Error"){
					setError(err.message);
				}
			}
		}
		
		fetchMovies();
		
		return function(){
			controller.abort();
		};
	},
	[query]
};
```