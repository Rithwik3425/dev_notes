# Custom Hooks
user defined hooks which may contain one or more React hooks.

* Custom Hook, allow us to reuse non-visual logic in multiple components.
* One custom hook should have one purpose, to make it reusable and portable (even across multiple projects )
  Rules of hooks apply to custom hooks too.
  
  ```
  function useFetch(url){
	  const [data,setData] =  useState([]);
	  const [isLoading, setIsLoading] = useState(false);
	  
	  useEffect(
		  function (){
			  fetch(url).then((res) => res.json()).then((res) => setData(res));
		  },
		  []
	  );
	  
	  return [data, isLoading];
  }
```