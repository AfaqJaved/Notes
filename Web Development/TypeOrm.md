
## Why ORM ❓

![[without orm.png]]
## Pg (Postgres client for Node Js)

```
npm install pg
```

```ts

import { Client } from 'pg';

const client = new Client({
	user: 'dbuser',
	host: 'database.server.com',
	database: 'mydb',
	password: 'secretpassword',
	port: 3211,
});

await client.connect();

const query = 'INSERT INTO users(name, email) VALUES($1, $2);';
const values = ['brianc', 'brian.m.carlson@gmail.com'];
const res = await client.query(query, values)console.log(res.rows[0])

await client.end()

```

## Disadvantages of using Clients

- Harder to maintain when application get complex
- Difficult to Debug
- Error Handling
- Boilerplate Code
- Threat of [[SQL INJECTION]]

## Advantages of using Clients

- Performance Boost
- Low Level Control


## What is ORM ❓

Object Relational Mapping (ORM) is a technique used in creating a "bridge" between object-oriented programs and SQL (Relational Databases).

Put another way, you can see the ORM as the layer that connects object orient programming (OOP) to relational databases(SQL).


![[why orm.png]]
## Advantages of Using ORM

- It speeds up development time for teams.
- Decreases the cost of development.
- Handles the logic required to interact with databases.
- Improves security. ORM tools are built to eliminate the possibility of SQL injection attacks.
- You have to write Less Code.

## Disadvantages

- Learning how to use ORM tools can be time consuming.
- ORMs are generally slower than using SQL.


# Getting Started With TypeOrm

TypeOrm Can be used with JS and TypeScript but the recommended approach is with Typescript.

## Installation

```
npm install typeorm reflect-metadata pg
```

####  Development Dependencies

```
npm install @types/node --save-dev
```


*Client depends on the relational database you want to use check supported clients by typeorm at official docs* 
https://typeorm.io/


## 1 - Configuring the DataSource


``` ts
import { DataSource } from "typeorm"

const AppDataSource = new DataSource(
{ 
	type: "mysql", 
	host: "localhost", 
	port: 3306, 
	username: "test", 
	password: "test", 
	database: "test", 
}
);


AppDataSource.initialize().then(() => { 
	console.log("Data Source has been initialized!") 
})
.catch((err) => { 
	console.error("Error during Data Source initialization", err) 
	})

```

## 2 - Entities In TypeORM

Entity is a class that maps to a database table. This is the concept which combine both the worlds (OOP with SQL).

```ts
import { Entity, PrimaryGeneratedColumn, Column } from "typeorm"

@Entity() 
export class User { 
	@PrimaryGeneratedColumn() 
	id: number;
	
	@Column() 
	firstName: string;
	 
	@Column() 
	lastName: string; 
	
	@Column() 
	isActive: boolean;
	
}
```

![[Screenshot 2023-10-29 at 1.20.48 pm.png]]


For using Decorators in Typescript For enable the following properties in **tsconfig.json**.

```json
"emitDecoratorMetadata": true,
"experimentalDecorators": true,
"strictPropertyInitialization": false, /* Check for class properties that are declared but not set in the constructor. */
```

## Working of TypeORM


![[diagram-export-29-10-2023-14_12_16.png]]

## 3- Relations

- Cascade (insert | update)
- onDelete (restrict | cascade)
- Eager and Lazy Relation
- Nullable Relation
- Two Way Relation

### One To One


![[diagram-export-29-10-2023-18_35_53 1.png]]

## One To Many

one to many from left to right (user - todo)
many to one from right to left (todo - user)

![[diagram-export-29-10-2023-21_53_32 1.png]]


## Many To Many

left to right one to many (student - courses)
right to left one to many (course - students)

![[diagram-export-29-10-2023-21_57_37 1.png]]