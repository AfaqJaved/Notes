
1. Html
2. Css
3. Javascript
4. DOM
5. ES6 Features like arrow functions
6. Simple Project By using all the five above
7. Rest API'S
8. Code Editor Basics (VS Code)
9. Google Chrome Developers Tools (Not Necessary but a plus)
10. Node and npm (For package management) installed in your computer

# Why React JS

1. Its provides SPA ([[SPA(Single Page Applications)]]Single Page Application) experience which is way better than [[Traditional Website (Start of Web Browsers)]].
2. React is Faster due to [[Virtual Dom in ReactJS]].
3. Its is a library (hence light weight).
4. Since it is a library its very flexible (we can use our lovely packages with it).
5. Developer Friendly (Breaks things into smaller components).
6. Good community support.


# Why not ReactJS

1. Heavily dependent on third party packages for getting things done. 


# Creating our First React Project


#### Old Way (This uses Webpack as package bundler)

```
npx create-react-app my-app  
cd my-app  
npm start

```
### New Way using Vite (Faster Package Bundler)

```
npm create vite@latest
yarn create vite
```

![[vite-templates.png]]
# Concepts

Javascript + Html = JSX [[React JSX]]

**JSX*** stands for ****JavaScript XML****. JSX is basically a syntax extension of JavaScript. It helps us to write HTML in JavaScript and forms the basis of React Development.

```js
import * as React from 'react';

const title = 'React';

function App() {
  return (
		<div>
		      <h1>Hello {title}</h1>
		</div> 
);

}
export default App;
```

JSX Lists

Using map function
```js
const numbers = [1, 4, 9, 16];
const newNumbers = numbers.map(function(number) { 
	return number * 2;
});
```

```jsx
function App() {
  return (
	<div>    
		<ul>
	        {list.map(function (item) {
	          return <li>{item.title}</li>;
	        })}
		</ul>

	</div>
);
}
```

## Components (Separation of Concerns)

Components are the foundation of every React application. Like bricks for building house.

- Reusable
- Developer friendly due to separation of concerns
- Instant updates without page reloads.
- Use conditional statements within the JSX.
- The code is nice and stable.

![[web-structure.png]]

### React DOM

The only task of React Dom is to convert the JSX to Html.

```jsx
import * as React from 'react'; import ReactDOM from 'react-dom';

import App from './App';

ReactDOM.render(
  <App />,
  document.getElementById('root')

);
```

### Event Handling in JSX (Synthetic Events)

React’s synthetic event is essentially a wrapper around the browser’s native event, with more functions that are useful to prevent native browser behaviour (e.g. refreshing a page after the user clicks a form’s submit button).

```jsx
const Search = () => {

  const handleChange = (event) => {
    console.log(event);

};

  return (
    <div>
      <label htmlFor="search">Search: </label>
      <input id="search" type="text" onChange={handleChange} />
    </div> );

};
```

### Note (Always Pass functions by reference as the event handlers in JSX)

```jsx
// don't do this
<input
id="search"  
type="text" onChange={handleChange()}
/>

// do this instead
<input
id="search"  
type="text" onChange={handleChange}
/>

```

## React Props

By using so-called props in React, we can pass variables as information from one component to another component.

- Pass information from parent to child and vice versa (Child to Parent).
- For child to parent callback handlers in JSX.

```jsx
<List data={["apple","mango","grapes"]}/>

//Seprate Component
const List = (props) => (
	<ul>
	    {props.data.map((item) => (
	      <li key={item}>
	       <p>{item}</p>
		  </li>
         ))}

	</ul>
);
```

## React State

React state is used to alter information over time.

```jsx
const Search = () => {
  const [searchTerm, setSearchTerm] = React.useState('');

	... 

};
```

## Callback Handlers JSX 

This solves the problem of child to parent communication.

![[controlled vs uncontrolled.png]]


```jsx

//App Component
const App = () => {
  const stories = [ ... ];
  const handleSearch = (event) => {
    console.log(event.target.value);
  };
  return (
    
    <div>
      <h1>My Hacker Stories</h1>
      <Search onSearch={handleSearch} />
      <List list={stories} />
    </div>
    
    );

};


//Search Component
const Search = (props) => {
  const [searchTerm, setSearchTerm] = React.useState('');
  const handleChange = (event) => {
    setSearchTerm(event.target.value);
    props.onSearch(event);
};
  return ( ... );
};

```

## React Lifting State Up

We often share state with nested components. Lifting the state up refers to lift the state to the 
closest common ancestor.

### Problem

```jsx
import React from "react";

export default function App() {
  return (
    <>
      <TodoCount />
      <TodoList />
      <AddTodo />
    </>
  );
}

function TodoCount() {
  return <div>Total Todos: </div>;
}

function TodoList() {
  const [todos, setTodos] = React.useState(["item 1", "item 2", "item 3"]);

  return (
    <ul>
      {todos.map((todo) => (
        <li key={todo}>{todo}</li>
      ))}
    </ul>
  );
}

function AddTodo() {
  function handleSubmit(event) {
    event.preventDefault();
    const todo = event.target.elements.todo.value;
    console.log(todo);
  }

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" id="todo" />
      <button type="submit">Add Todo</button>
    </form>
  );
}
```

### Solution 

```jsx
import React from "react";

export default function App() {
  const [todos, setTodos] = React.useState(["item 1", "item 2", "item 3"]);

  return (
    <>
      <TodoCount todos={todos} />
      <TodoList todos={todos} />
      <AddTodo setTodos={setTodos} />
    </>
  );
}

function AddTodo({ setTodos }) {
  function handleSubmit(event) {
    event.preventDefault();
    const todo = event.target.elements.todo.value;
    setTodos(prevTodos => [...prevTodos, todo]);
  }

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" id="todo" />
      <button type="submit">Add Todo</button>
    </form>
  );
}
```

## Controlled Vs Uncontrolled Components

![[controlledvsuncontrolled.png]]


## Prop Handling using JS Object Destructuring

```jsx
const Search = ({ search, onSearch }) => (
  <div>
    <label htmlFor="search">Search: </label>
    <input
      id="search"
      type="text"
      value={search}
      onChange={onSearch}
	/></div>

);
```

### Nested Structuring

```jsx
const Item = ({
  item: {
    title,
    url,
    author,
    num_comments,
    points,
},
}) => ( <li>
	<span><a href={url}>{title}</a></span>
    <span>{author}</span>
    <span>{num_comments}</span>
    <span>{points}</span>
</li> );
```


## React Side-Effects

A React side-effect occurs when we use something that is outside the scope of React in our React components e.g. Web APIs like localStorage.
**Always try to write the side-effects in useEffect Hook**.

```jsx
const App = () => {
  const [searchTerm, setSearchTerm] = React.useState(
    localStorage.getItem('search') || 'React'
);

  React.useEffect(() => {
    localStorage.setItem('search', searchTerm);
  }, [searchTerm]);

  const handleSearch = (event) => {
    setSearchTerm(event.target.value);

};

... 

);
```

## React Custom Hooks

React custom hooks are just reusable functions which help you you extract component logic.

```JSX

//PROBLEM
import React, { useState, useEffect } from 'react';

function FriendStatus(props) {
  const [isOnline, setIsOnline] = useState(null);
  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }
    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    return () => {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });

  if (isOnline === null) {
    return 'Loading...';
  }
  return isOnline ? 'Online' : 'Offline';
}




// SOLUTION

function useFriendStatus(friendID) {
  const [isOnline, setIsOnline] = useState(null);

  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }

    ChatAPI.subscribeToFriendStatus(friendID, handleStatusChange);
    return () => {
      ChatAPI.unsubscribeFromFriendStatus(friendID, handleStatusChange);
    };
  });

  return isOnline;
}
```


## React Fragments

Normally the JSX returned by a React component needs only one wrapping top-level element. To render multiple top-level elements side-by-side, we have to wrap them in one single unit. And that is where React Fragments comes in.

```jsx
const Search = ({ search, onSearch }) => (

<>
    <label htmlFor="search">Search: </label>
    <input
      id="search"
      type="text"
      value={search}
      onChange={onSearch} />
</>

);
```


## React Component Composition

We can wrap components inside components and can access inside components using children prop.

```jsx
const InputWithLabel = ({
id,
value,  
type = 'text', onInputChange, children,
}) => ( 
	<>
	    <label htmlFor={id}>{children}</label>
Fundamentals of React 84
    &nbsp;
    <input
      id={id}
      type={type}
      value={value}
      onChange={onInputChange}

/> </>
);



//Usage
 <InputWithLabel
        id="search"
        value={searchTerm}
        onInputChange={handleSearch}
>  
		Search:
      </InputWithLabel>
```

## React Conditional Rendering

```jsx

const App = () => {
 const isAdmin = true;
 
 return (
	{isAdmin ? <h1>{"Is Admin"}</h1> : <h1>{"Not a admin"}</>}
 )
}

```

