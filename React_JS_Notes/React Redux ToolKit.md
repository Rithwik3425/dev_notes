# Redux Toolkit
The modern and prefered way of writing redux code
* Allows us to write a lot of less code
  Usage
  * We can write code that mutates state inside reducers (will be converted into immutable logic behind the scenes by "immer" library).
  * Action creators are automatically created
  * Automatic setup of thunk and dev-tools
___
### Creating a store with redux toolkit (RTK)
```
npm i @reduxjs/toolkit

import {configureStore} from '@reduxjs/toolkit';
import accountReducer from "./features/account/acc";
import customerReducer from "./features/customer/cus";

const store = configureStore({
	reducer: {
		account: accountReducer,
		customer: customerReducer,
	},
});
```
___
### Creating a slice with RTK
Here we use "createSlice" which automatically create action creators from our reducers and state can be mutated inside the reducer
```
const initialState = {
	balance: 0,
	loan: 0,
	loanPurpose: " ",
	isLoading: false,
};

const accountSlice = createSlice({
	name: "account",
	initialState,
	reducers: {
		deposit (state, action){
			state.balance += action.payload;
		},
		withdraw(state, action){
			state.balance -= action.payload;
		},
		requestLoan(state, action){
			if(state.loan > 0) return;
			state.loan = action.payload.amount;
			state.loanPurpose = action.payload.purpose;
			state.balance += action.payload.amount;
		},
		payLoan(state, action){
			state.loan = 0;
			state.loanPurpsoe = " ";
			state.balance -= state.loan;
		},
	},
});

export const {deposit, withdraw, requestLoan, payLoan} = accountSlice.actions;

export default accountSlice.reducer;

requestLoan:{
	prepare(amount, purpose){
		return{
			payload: {amount, pupose},
		};
	},
	reducer(state, action){
		if(state.loan > 0 ) return:
	}
}
```

Inorder to use thunks in RTK, we use "createAsyncThunk" function

### Which to use? Context api or Redux
![[WhatsApp Image 2024-02-23 at 16.45.59_245b94cd.jpg]]