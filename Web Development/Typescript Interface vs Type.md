#typescript #interface #type 

```tsx
interface User {
 name : string;
 age : number
}


type User = {
name : string;
age : number


// Some Naming Convertions for interface 
interface IUser {
 name : string;
 age : number
}

type TUser = {
 name : string;
 age : number;
}
}```

## Extending Types And Interfaces

```tsx
//Extending Types
type UserProps = {
	name : string;
	age : number;
}

type AdminProps = UserProps & {
	role : string;
}

//Extending Interfaces

interface User {
	name : string;
	age : number;
}

interface AdminUser extends User {
	role : string;
}

```

## Interface can only Describe Objects (Not Primitive Types) But Types can describe all (Objects + Primitive Types)

```ts

//Types
type Address = string;
const address : Address = `This is the address`;

type User = {
	name : string;
	age : number;
}
const user : User = {name : "afaq",age : 22};

//This is not possible (interface can only describe Objects)
interface Address = string;
```

## Types can also define Union Types but Interface Can Not

```jsx
type PhoneNumber = string | number;
const phone  : PhoneNumber = "+9234343423";

//Not possible with interface
interface PhoneNumber = string | number;
```

## Types can use Utility Types and interface can too but with ugly Syntax

```jsx
type UserProps = {
	name : string;
	age : number;
	createdAt : Date;
}

type GuestProps = Omit<UserProps , "name" | "age">;

//Same can be done with interface

interface User {
	name : string;
	age : number;
	createAt : Date;
}

interface Guest extends  Omit<User , "name" | "age"> {};

```

## Types Can Define Tuples and interface can also but with ugly Syntax

```js
type Address = [string,number];

const address = ["Karachi Pakisnta" , 75010];



//Same with interface with ugly syntax
interface Address extends Array<number | string> {
 0 : string;
 1 : number;
}
```


## Types can help in extracting Types from Another Object

```js
// extracting type from something else
const project = {
	title: "Project 1",
	specification: {
	areaSize: 100,
	rooms: 3,
};

type Specification = typeof project["specification"];
```

## Interfaces Can Be Merged (Be Aware of Third Party Libraries)

```js
// "interfaces are open" and "type aliases are closed"
interface User {
	name: string;
	age: number;
}

interface User {
	role: string;
}

```

## Types can easily be implemented In classes as Well

```js
type TUser {
	name: string;
	age: number;
}

class User implements TUser {
	name: string;
	age: number;
	
	constructor (name: string, age: number) {
		this.name name;
		this.age = age;
	}
}

```

## Some good Arguments 😜

**interface** = 9 words
**type** = 4 words

### Its Typescript Not Interface Script 😱
