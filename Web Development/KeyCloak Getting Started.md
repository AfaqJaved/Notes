

## Docker 

```
docker run -p 8080:8080 -e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin quay.io/keycloak/keycloak:23.0.3 start-dev

```


## Realm (Create Realm)

For multi tenancy


## Users (Create User)

Create the users

## User Account Management Console

```
http://localhost:8080/realms/{realm-name}/account/#/
```
![[Screenshot 2024-01-18 at 5.47.27 PM.png]]


## Realm Roles

The roles for specific realms can be assigned to user or group.

## Groups

For Grouping Special Category of Users
- admin
- accountant
- student
- teacher

## Realm Admin

Create admin for specific realm
username admin-todo
pass admin

## Clients

In Keycloak, clients are entities that request and use identity and access management services.

1. **Public Clients (Front End Applications):** These are clients that cannot keep their credentials confidential. Examples include single-page applications (SPAs) running in a web browser where the client-side code is visible to users.

2. **Confidential Clients (Back End Applications):** These are clients that can keep their credentials confidential. Examples include traditional web applications or server-side applications that can securely store client secrets.

3. **Bearer-Only Clients:** These clients only make use of bearer tokens for authentication and do not perform the initial authentication. They are typically used for securing APIs.

4. **Service Accounts (Back End Applications without user Intervention):** Service accounts are special types of clients that can be used for machine-to-machine communication. They can obtain access tokens without user intervention.


## Performing OIDC Flow with PostMan

- realm = todo
- server = localhost:8080
- The id of the client which we have recently created
- Response type = code because we are using the Outh 2.0 standard flow.

![[Screenshot 2023-12-22 at 4.03.44 PM.png]]

### Authorization EndPoint (Try in Browser)

```http
GET http://server/realms/{realm_name}/protocol/openid-connect/auth 
?client_id={client_id} 
&redirect_uri={redirect_uri}
&response_type=code
```

### Token EndPoint Or Token Exchange EndPoint

```http
POST http://server/realms/{realm_name}/protocol/openid-connect/token 
?grant_type=authorization_code 
&code={obtained_authorization_code}
&client_id={client_id}
&redirect_uri={redirect_uri}
```

### Logging Out The Session (Try in Browser)

```http
GET http://server/realms/{realm_name}/protocol/openid-connect/logout 

```
# For Interacting With Front End Application (React)

## Install Keycloak JS

```
npm i keycloak-js
```


## Process Flow

![[Screenshot 2023-12-22 at 4.03.44 PM.png]]

## Requirement

Before an application can log in with Keycloak, it has to be registered as a client with Keycloak.

## KeyCloak Clients

Any application accessing keycloak is a client for keycloak which need to registered in keycloak with the following requirements.

- Valid redirect URIs: Where the user will be redirected after login success.
- Valid post redirect URIs: Where the user will be redirected after logout.
- Web origins:  only listen request from this urls (CORS).


## React Code

```ts
import Keycloak from "keycloak-js";

export const keycloak = new Keycloak({

	url: "http://localhost:8080",

	realm: "demo",

	clientId: "react-client",

});

  
  

try {
	const authenticated = await keycloak.init({});
	console.log(`User is ${authenticated ? "authenticated" : "not    authenticated"}`);

} catch (error) {
	console.error("Failed to initialize adapter:", error);
}

```



```tsx
import { keycloak } from "./main";

  
function App() {

	const login = async () => {

		const login = await keycloak.login();

	};

  

	const logout = async () => {

		const payload = await keycloak.logout();

		console.log(payload);

	};

  

return (

<>

	<div>

		<h2>{keycloak.token}</h2>

		<h2>{keycloak.hasRealmRole("superadmin").toString()}</h2>

	</div>

	<h1>KeyClock Demo</h1>

	<button onClick={login}>Login</button>

	<button onClick={logout}>Logout</button>

</>

);

}

  

export default App;
```


# OpenId Connect Flow

While OAuth 2.0 is a protocol for authorization, it does not cover authentication. OpenID Connect builds on top of OAuth 2.0 to add an authentication layer.

OpenID Connect defines a number of roles involved in the protocol :

- **End User**: This is the equivalent of the resource owner in OAuth 2.0. It is, of course, the human being that is authenticating.

- **Relying Party (RP)**: A somewhat confusing term for the application that would like to authenticate the end user. It is called the RP as it is a party that relies on the OpenID Provider (OP) to verify the identity of the user.

- **OpenID Provider (OP)**: The identity provider that is authenticating the user, which is the role of Keycloak.

![[Screenshot 2023-12-24 at 1.44.46 PM.png]]


## KeyCloak Service Accounts

In Keycloak, service accounts are special accounts that represent clients rather than individual users. Service accounts are used to obtain access tokens for a client application to access protected resources. They are often used in machine-to-machine communication or backend services where there is no direct user interaction.

