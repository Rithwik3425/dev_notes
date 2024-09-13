This lets us group some elements without leaving any trace in the html tree, so in the DOM
```
return(
	<main className = "menu">
	<h2>Our Menu</h2>
	{numpizza > 0?
		(
			<> or <React Fragment key="">
				<p>Authentic....</p>
				<ul className = "pizzas">
					{
						pizzas.map((i) => (
							<pizza pobj={i} />
						))
					} 
				</ul>
			</> or </React Fragment>
		):(
			<p>We are still working on it....</p>
		)
	}
);
```
