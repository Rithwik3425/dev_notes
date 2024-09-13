##### Rendering a list
```
cons pizzadata{
	{
		name: "abc",
		ingriendts: "ABC",
		price: 6,
		soldout: false,
	},
	{
		name: "xyz",
		ingriendts: "XYZ",
		price: 12,
		soldout: false,
	},
	{
		name: "abd",
		ingriendts: "ABD",
		price: 8,
		soldout: false,
	},
	{
		name: "xya",
		ingriendts: "XYA",
		price: 10,
		soldout: false,
	},
};

function Menu(){
	return (
		<div>
			{pizzadata.map((pizza) => {
				<Pizza pizzaobj={pizza} key={pizza.name} />
			})}
		</div>
	)
}

function Pizza(props){
	return (
		<div>
			<img src = {props.pizzaobj.photoname} />
			<div>
				<h3>{pizza.pizzaobj.name}</h3>
				<p>{props.pizzaobj.ingriendts}</p>
				<span>{props.pizzaobj.price}</P
			</div>
		</div>
	);
}
```

##### Conditional Rendering with "&&"
some statements will only run if the given condition is true (also called as ==Short-Circuiting== )
```
function Footer(){
	const hr = new Date().getHours();
	const isOpen = (hr >= 12) && (hr<=22);
	return (
		<footer>
			{isOpen && <p>Open</p>} //this statement will only run iff isOpen is true
		</footer>
	);
}
```

##### Conditional Rendering with Ternary
same as normal ternary operator in other languages 
==condn?true:flase== 
```
function Footer(){
	const hr = new Date().getHours();
	const closeHr = 22;
	const openHr = 12;
	const isOpen = (hr >= openHr) && (hr <= closeHr);
	return (
		{isOpen?
			(<p>Open now!</p>):(<p>Closed!</p>)
		}
	);
}
```

##### Conditional Rendering with Multiple returns
if statement is used
```
if (props.pizzaobj.soldout) return null;
```