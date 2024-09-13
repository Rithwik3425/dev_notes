# The URL for state Management
the url is an excellent place to store ui state and an alternative to useState in some situations
EX: open|closed pannels, currently selected list item, list sorting orders applied list filters

Uses:
* Easy way to store in a global place, accessible to all components in the app
* Good way to "pass" data from one page into next page
* Makes it possible to bookmarks and share the page with the exact UI state it gad at the time
___
# Dynamic parametered Routes with URL parameters
This process is done in three steps
* First create a new route
* Link to that route
* Read the state from the URL in that route

### 1 creating a new route
```
<Route path="cities:id" element={<Citites />} /> 
```

### 2 Linking the route
```
function CiryItem({city}){
	const {cityName,emoji,data,id} = city;
	
	return (
		<li className="">
			<Link className={styles.cityItem} >
				<span className={styles.emoji}></span>
				<h3>{cityName}</h3>
				<time>({formatDate(date)})</time>
				<button>&times;</button>
			</Link>
		<li>
	);
}
```

