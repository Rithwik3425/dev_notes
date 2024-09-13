# State
Data that a component can hold overtime necessary for the information that it need to remember throughout app's lifecycle
		==State => Component's memory==

### State variable / piece of state
a single variable in a component

---
### Component State
single local component variable 
* Updating ==component state== triggers React to ==re-render== the component
* ![[WhatsApp Image 2024-02-22 at 18.52.58_4cc9f10f.jpg]]

---
### Controlled Elements
* Step 1: Create a state
* Step 2: Use the state that we want to control ex: value={state}
* step 3:Update the state variable
```
onChange((e) => setDescription(e.target.value))
```

___
### Derived State
state that is computed from an existing piece of state or form from props
```
const [cart, setCart] = useState([
	{name: "JS Course", price: 15.99},
	{name: "Node JS",price: 14.99},
]);

const [numItem,SetNumItem] = useState(2);
const [totalPrice, setTotalPrice] = useState(30.98);

//now by deriving the state,
const [cart, setCart] = useState([
	{name: "JS Course", price: 15.99},
	{name: "Node JS",price: 14.99},
]);

const numItems = cart.length;
const totalPrice = cart.reduce((acc,curr) => acc + curr.price,0);
```

[[React StateManagement]]