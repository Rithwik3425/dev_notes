Props used to pass data from parent components to child components
* With props, parent component control how child component look and word
* Anything can be passed as props => Single values, arrays, objects, functions, even other components
* ![[WhatsApp Image 2024-02-22 at 17.59.12_24fe5a84.jpg]]
* Mutating props, would effect parent, creating a ==Sideffect== (not pure)
* components have to be pure functions in terms of props and state

#### Passing and receiving props
```
//Passing the props

<Pizzafunc
	name: "pizza spinaci",
	ingredints: "Whaterver they are",
	photoname: "pizzaf/spinaci.jpg",
	price: {10},
/>

<Pizzafunc
	name: "pizza Funghi",
	ingredints: "IDK bro",
	photoname: "pizzaf/funghi.jpg",
	price: {12},
/>

//receiving props
function Pizzafunc(props){
	console.log(props);
	return(
		<div className = "pizza">
			<img src = {props.photoname} alt={props.name} />
			<h3>{props.name}</h3>
			<p>{props.ingredints}</p>
		</div>
	);
}
```

[[REACT JS]]