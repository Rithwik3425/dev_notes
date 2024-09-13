# Redux Middleware
A function that sits between dispatching the action and the store. Allows us to run code after dispatching, but before reaching the reducer in store
* Can make asynchronous operation and then dispatch
* Fetching data in components is not ideal
* This asynchronous code can be runed by using the third party package called ==REDUX THUNK== 
___
### Making api calls with redux thunk
```
npm i redux-thunk

import thunk from 'redux-thunk';
const store = createStore(rootReducer, applyMiddleWare(thunk));

export function deposit(amount. currency){
	if(currency === 'USD') return { type: "account/deposit", payload: amount};

	return async function (dispatch,getState){
		const res = await fetch(
			'https://api.frankfuter.app/latest?amount=${amount}&from=${currency}&to=USD');
			
		const data = await res.json();
		const converted = data.rates.USD;
		
		dispatch(
			{type: "account/deposit", payload: converted}
		);
	};
}
```
___
### Redux-dev tools
* Install the dev tool extension i.e., redux dev tool
* npm i redux-devtools-extension
* const store = createStore(rootReducer,
	composeWithDevTools(applyMiddelWare(thunk))
  );
___
[[React Redux ToolKit]]

[[React Redux]]