
## Scope in Js

By Default Root Scope (Global Object/Window Object)

```js
var test = "testing";

function callMe() {
  console.log(test);
}
```

The above is ok sine both live in global object.

```js
var fun = "fun"; // root scope

function test() {
	//child scope 
	var fun = "afaq"; //this will be overidden from root scope
}
```