## What are hooks?
---
**Hooks** are predefined and reusable functions that allow applications to "hook" into reacts internal lifecycle system.
This leads to clean state changes, fetches, updates, etc. through a predefined but modular ecosystem of hooks.

*There are many different types of hooks, the main two covered in class are explained below*

## State Hooks
---
**State Hooks** are a more modular way to store values (variables) in React. You can intialize an empty array, for example, and then add values as forms are entered etc. through the applicatoin

*There are two main Hooks for State*
1. `useState`
2. `useReducer`

Both of these are essentially the same, but `useReducer` allows you to define how updates are done, while `useState` handles updates directly.

## Effect Hooks
---
**Effect Hooks** are how React components communicate with many different *external systems*. For example:
- AWS
- Other UI component libraries
- Databases
- etc.
**General Structure of a `useEffect` hook**
```JSX
function Example({ reactiveValue1 }) => {
	const [ reactiveValue2, setReactiveValue2 ] = useState{Null};
	
	useEffect(() => { 
		
		const initVal1 = initVal(reactiveValue1);
		const initVal2 = initVal(reactiveValue2);
		
		doSomething(initVal1, initVal2);
		
		return () =>
			undoSomething(initVal1, initVal2);
			
	}, [reactiveValue1, reactiveValue2]);
}
```




