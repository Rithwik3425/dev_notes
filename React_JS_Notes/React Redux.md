* 3rd party library to manage global state
* Standalone library, but easy to integrate with React apps using react-redux library.
* All global state is stored in one globally accessible store, which is easy to update using "actions" (like useReducer)
* It's conceptually similar to using the {context api + useReducer}
* Two versions
	* classic redux
	* Modern Redux Toolkit
==npm i redux==
```
const initialState = {
	balance: 0,
	loan: 0,
	loanpurpose: "",
};

function reducer(state = initialState, action){
	switch(action.type){
		case "account/deposit":
			return {
				...state, balance: state.balance + action.payload;
			};
		case "account/withdraw":
			return {
				...state, balance: state.balance + action.payload;
			};
		case "account/requestLoan":
			if(state.loan > 0) return state;
			return{
				...state, loan: action.payload;
			};
		case "account/payloan":
			return{
				...state,
				loan: 0,
				loanPurpose: " ",
				balance: state.balance - state.loan
			};
		defalult:
			return state;
	};
}


const store = createStore(reducer);
store.dispatch({type: "accout/deposit", payloadL 500});
console.log(store.getState()); //shows the current state of the store
```
___
### Action creator function
functions that return actions 
Redux would work fine without these functions
```
function deposit(amount){
	return {type: "account/deposit", payload: amount};
}

function withdraw(amount){
	return {type: "account/withdraw", payload: amount};
}

function requestLoan(amount, purpose){
	return {type: "account/requestLoan", 
			payload: {amout,purpose}
	};
}

function payLoan(){
	return { type: "accoutn/payLoan" };
}

store.dispatch(deposit(5000));
store.dispatch(withdraw(2000));
store.dispatch(requestLoan(500, "Buy a new car"));
store.dispatch(payLoan());
```
___
==npm i react-redux==
___
### For multiple reducers
```
const rootReducer = combineReducers({
	account: accountReducer,
	customer: coustomerReducer,
});
const store = createStore(rootReducer);

<React.strictMode>
	<Provider store={store}>
		<App />
	</Provider>
</React.strictMode>

//To select from the store/ Redux store, we use useSelector hook

const customer = useSelector((store) => store.customer);
const dispatch = useDispatch();
```
___
[[React Redux MiddleWare]]

[[REACT JS]]