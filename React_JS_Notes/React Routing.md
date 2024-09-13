# What is Routing ?
basically match different urls to different views in the user interface
(or)
with routing, we match different url's to different UI views (React components): routes

* This enables user to navigate between different applications screen, using the browser URL
* keeps the UI in sync with the current browser URL

To use Router install the package into app
```
npm i react-router-dom@6
```

```
import {BrowserRouter, Routes, Route} from "react-router-dom";

import product from "./pages/Product";
import HomePage from "./pages/HomePage";
import Pricing from "./pages/Pricing";

function App() {
	return (
		<BrowserRouter>
			<Routes>
				<Route path="/" element={<HomePage />} />
				<Route path="/product" element={<Product />} />
				<Route path="/pricing" element={<Pricing />} />
			</Routes>
		</BrowserRouter>
	);
};
```
____
### Linking between pages
React router gives "link" to link in between the pages without any hard reload.
```
<Link to="/pricing">Pricing</Link> //the url to be moved ot pricing
(or)
<Navlink to="/pricing">Pricing</Navlink>
```

[[React NestedRoutes]]
