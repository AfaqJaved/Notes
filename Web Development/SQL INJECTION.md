![[Screenshot 2023-10-28 at 6.11.03 pm.png]]

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

const query = 'SELECT * FROM Users WHERE Name = $1';
const values = ['Jhon Doe'];
const res = await client.query(query, values);
console.log(res.rows[0]) //result

await client.end()

```

## Problem

![[Screenshot 2023-10-28 at 6.13.37 pm.png]]

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

const query = 'SELECT * FROM Users WHERE Name = $1';
const values = ['abc;DROP TABLE Users;'];
const res = await client.query(query, values);
console.log(res.rows[0]) //result

//const query = 'SELECT * FROM Users WHERE Name = abc;DROP TABLE Users;';

await client.end()

```