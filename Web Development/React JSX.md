#jsx #reactjsx #jsexpression #expression

![[jsx.png]]

## Why JSX ❓

- It is faster than normal JavaScript as it performs optimisation while translating to regular JavaScript.
- Developer friendly. It makes it easier for us to create templates. Instead of separating the markup and logic in separate files we put every thing in the same file.
- As JSX is an expression [[JS Expression]], we can use it inside of **if statements** and for loops, **assign it to variables**, **accept it as arguments**, or **return it from functions**.

## How React Handles Html attributes (class) keyword ❓


```jsx
//css
.heading {
	font-size : 30px;
}

//html
<h1 class="heading">This is heading</h1>


//jsx

const element = <h1 class="heading">This is heading</h1>;

class Person {
 constructor() {
	this.name = "afaq";
 }
}
```

JSX allows us to use attributes with the HTML elements just like we do with normal HTML. But instead of the normal naming convention of HTML, JSX uses the camelcase convention for attributes.

- The change of class attribute to className:
    
    The __class__ in HTML becomes __className__ in JSX. The main reason behind this is that some attribute names in HTML like ‘__class__‘ are reserved keywords in JavaScript. So, in order to avoid this problem, JSX uses the camel case naming convention for attributes.
    
- Creation of custom attributes :
    
    We can also use custom attributes in JSX. For custom attributes, the names of such attributes should be prefixed by ****data-***** attribute.

```jsx
const element = <h1 className="hello">Hello World!!!</h1>;
const element2 = <h2 data-sampleAttribute="sample">Custom attribute</h2></div>;
```





