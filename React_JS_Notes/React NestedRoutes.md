# Nested Routes
```
<Route path="app" elements={<Applayout />} />
	<Route index element={<ListCities />} />
	<Route path="cities" index element={<ListCities />} />
	<Route path="countries" index element={<ListCountry />} />
	<Route path="form" index element={<Form />} />
</Route>
```

-in Applayout.jsx
```
function AppLayout(){
	return (
		<div className={styles.app} >
			<SideBar />
			<Map />
		</div>
	);
}
```

-in SideBar.jsx
```
function SideBar(){
	return (
		<div className={styles.sidebar} >
			<Logo />
			<AppNav />
			<Outlet />  //inbuilt in react router
		</div>
	)
}
```

-in AppNav.jsx
```
function AppNav(){
	return (
		<nav className={styles.nav}>
			<ul>
				<li>
					<Navlink to="cities">Cities</Navlink>
				</li>
				<li>
					<Navlink to="countries">Countries</Navlink>
				</li>
			</ul>
		</nav>
	)
}
```