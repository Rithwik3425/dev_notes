###### First program: (the classic)
App.js
```
export default function App(){
	return(
		<div>Hello World</div>
	);
}
```
###### Another program: (Shows advices on screen from api)

```
import {useEffect, useState} from "react";

export default function App(){
	const [advice, setAdvice] = useState(" ");
	const [count, setCount] = useState(" ");

	async function getAdvice(){
		const res = await fetch("https://api.adviceslip.com/advice");
		const data = res.json();
		setAdvce(data.slip.advice);
		setCount( (c) => c +1);
	}

	useEffect( function (){
		getAdvice();
	},[]);

	return (
		<div>
			<h1>{advice}</h1>
			<button onclick={getAdvice}>Hit me</button>
			<p>You have read <strong>{count}</strong> piece of advices </p>
		</div>
	);
}
```

# React
* Java-script library for building user interfaces (or)
* Extremely popular declarative, component based state driven Java-script library for building user interfaces

* Components are the building blocks of user interfaces in react.
	*  Example: Input field, nav, search bar, and so on
* We describe how components look like and how they work using a declarative syntax called "==JSX=="
	* ==Declarative== telling react what a component should work | look like, based on current data | state

```
%% A digital Clock %%

<div class = "root"></div>
<script>
	function App(){
		const [time, setTime] = React.useState(new Date).tolocaleTimeString());

		React.useEffect(function (){
			setInterval(function () {
				setTime(new Date().tolocalTimeString());
			},1000);
		},[]);

		return (
			React.createElement("header",null,`Hello React! It's ${time}`)
		);
	}

	const root = ReactDOM.createRoot(document.getElementbyId("root"));
	root.render(React.createElement(App));
</script>
```

# JSX
Declarative syntax to describe what components look like and how they work
```
import {useState, useEffect} from "react";

const pizzadata={
	name: "pizza spinach",
	ingredints: "Bread with olive oil and remosry",
	price: 6,
	soldout: false,
};

function App(){
	return(
		<div>
			<Header /> //component named "Header"
			<Menu /> //component named "Menu"
			<Footer /> //component named "Footer"
		</div>
	);
}

function Header(){
	return <h1>Fast React JS co.</h1>
}

const Menu = () => {
	return (
		<div>
			<h2>Our Menu</h2>
			<Pizzafunc />
		</div>
	);
}

function Footer(){
	const [time,setTime] = useState(new Date().toLocaleTimeString());
	useEffect(function (){
		setInterval(function () {
			setTime(new Date().tolocaleTimeString());
		},1000);
	},[]);
	return <footer>{time}we are open now!</footer>
}

function Pizzafunc(){
	return (
		<div>
			<h3>{pizzadata.name}</h3>
			<p>{pizzadata.ingridents}</p>
		</div>
	);
}
```

[[React Props]]

[[React Conditional Rendering]]

[[React Fragments]]

[[React Effects]]

[[React Race Condition]]

[[React Hooks]]

[[React Routing]]

[[React styling]]

[[React StateManagement]]

[[React ContextApi]]

[[React Memoization]]

[[React Redux]]

[[React Query]]

___
### To store in local storage
```
useEffect{
	function (){
		localStorage.setItem("watched",JSON.stringify(watched));
	},
	[watched]
};

const [watched, setWatched] = useState(
	function () {
		const storedValue = localeStorage.getItem("watched");
		
		return JSON.parse(storedValue);
	}
);
```
___
### TO create a vite app
use the following commands:
* npm create vite@latest
* npm i
* npm run dev
___
### To configure eslint
* npm install eslint vite-plugin-eslint eslint-config-react app --save-dev
* create a new file named ".eslint.json" and write the following line code in it
```
{
	"extends": "react-app"
}
```
* and now open vite.config.js file and do 
	* import eslint from "vite-plugin-eslint";
	* and add eslint() to array
```
export default defineConfig({
	plugins: [react(),eslint()],
})
```
___
### How to plan and build a React Application
* Gather application requirements and features
* Divide the application into pages 
	* Think about the overall and page-level UI
	* Break the desired UI into components
	* Design and build a staic version (not state)
* Divide the application into features categories
	* Think about state management + data flow
* Decide on what libraries to use (tech decisions) 
___
