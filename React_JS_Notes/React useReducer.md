# UseReducer
All alternative way of setting state, ideal for complex state and related piece of state.
```
const [state,dispatch] = useReducer(reducer,intialState);

//here dispatch is a function
```

* useReducer stores related pieces of state in a state object.
* useReducer needs reducer: function containing all logic to update state. Decouples state logic from component.
* reducer: pure function (no side effects) that takes current state and action and return the next state
* action: object that describe how to update state 
	* contains an action "type"  and so called "payload", which basically is input data
* dispatch: function to trigger state update, by "sending" actions from event handlers to the reducer
```
const[state,dispatch] = useReducer(reducer,intialState);
``` 

![[WhatsApp Image 2024-02-23 at 00.16.46_ce51234e.jpg]]
```
function reducer(state,action){
	switch(action,type){
		case 'dec':
			return state - 1;
		case "inc":
			return state + 1;
		case "setCount":
			return action.payload;
		default:
			throw new Error("unknown action");
	}
}
```
