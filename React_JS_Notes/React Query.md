Powerful library for managing remote (server) state
Many features that allow us to write a lot less code, while also making the UX a lot better
* Data is stored in a cache
* Automatic loading and error stated
* Automatic re-fetching to keep state synched
* Pre-fetching
* Easy remote state mutation (updating)
* offline support

Needed because remote state is fundamentally different from regular UI state
```
npm i @tomstack/react-query@version


const queryClient = new QueryClient({
	defaultOptions: {
		queries: {
			staleTime: 60*1000, //60 is seconds and 1000 is milliseconds
		},
	},
});


function App(){
	return (
		<QueryClientProvider client={queryClient}>
		.
		.
		.
		.
		</ueryClientProvider>
	);
}
```