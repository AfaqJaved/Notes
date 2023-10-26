
## What is Redux Toolkit ❓(Abstraction over core Redux)

Redux Toolkit is **our official, opinionated, batteries-included toolset for efficient Redux development**. It is intended to be the standard way to write Redux logic, and we strongly recommend that you use it.

![[redux toolkit abstraction.png]]
## Installation

```
npm install @reduxjs/toolkit react-redux
```

## Steps for Integration Redux in React App

1. Configure Store at our entry point of application
2. Provide the Redux Store to React By Wrapping the React App with the Provider.
3. Create Your First Slice which will contain the Your Reducers. (Most important Part)
	1. Define Initial State
	2. Define Slice which will contain reducers
	3. Define actions
4. Add Slice Reducers To Configure Store Function
5. Use useDispatch() and useSelector() hooks to interact with the Redux Store
	1. useDispatch() -----> For Dispatching Action
	2. useSelector() ------> For Selecting Data From Redux Store