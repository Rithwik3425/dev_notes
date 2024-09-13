These are essentially special functions that are built into React and which allow us to basically hook into some of React's Internal Mechanisms.
(or)
hooks are basically API's, that expose some internal React functionality such as creating and accessing state from the fiber tree or registering side effects in the fiber tree.

* Hooks also allow us to manually select in-store dom notes access context i.e, (Manual DOM Selection)
* All hooks start with "**use**"

###### Rules of hooks
* Only call hooks at the top level
	* Do not call hooks inside conditionals, loops, nested functions, or after an early return
	* This is necessary to ensure that hooks are always called in the same order
* Only call hooks from React functions
	* only call a hooks inside a function component or custom hooks
___

[[React useRef]]

[[React CustomHooks]]

[[React useReducer]]

[[REACT JS]]