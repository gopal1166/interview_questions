## index | Date: 04-06-2021
1.  callback function and example
2.  Promises
3.  Closures
4.  iif(Immediately invoked functions)
5.  function binding
6.  pass by value and pass by reference
7.  normal function vs arrow function
8.  chain prototype
9.  window, document in js
10. call, apply and bind
11. window, screen, document



#### 1. Callback function:
  a function passed as an argument to another function to be executed later.  
Example:  
```javascript
<div style="background-color: rgb(50, 50, 50);">
/**
 * Callback function with example: processing response after getting api response
 *
 * @param {string} url any api
 * @param {*} callbackFun callback function to be executed right after main one
 * 
 */
function makeAPICall(url, callbackFun) {
  // we;ll get response here, callbackfun will wait till completion.
  callbackFun(url);
}

const url = 'xyz'
makeAPICall(url, function(url) {
  console.log("this is callback fun to process the api response of ", url)
})
```

#### 2. Promises:  
Callback hell: Deeply nested callbacks leads to confusion.  
To overcome this Promises introduced.  

Has three states.  
1. Pending: You don’t know if you will get that laptop
2. Fulfilled: Dad is happy, he buys you a brand new laptop
3. Rejected: Dad is unhappy, he doesn’t buy you a laptop

Syntax:  
```
new Promise(function (resolve, reject) { ... } );

let canIgetOne = true 
var newLaptop = new Promise(function (resolve, reject) {
  if(canIgetOne) {
    resolve('I am getting a new Laptop')
  } else {
    reject('No i am not')
  }
})

# Consuming
newLaptop
.then(msg => console.log(msg))
.catch(error => console.log(error))
```  


#### 3. Closures:
A function within a function is technically the closure
```
function outerFunc (){
  function closure(){
  // some logic
  } 
}
```

#### 4. IIFE (immediately invoked function expressions):
a function which is invoked right after defining.
syntax:
```
(function(){
    //...
})();
```
why:
memory inefficiently usage  
many variables and function definitions leads to global naming collision.
ex::
```
function add(a,b) {
    return a + b;
}

this add will be added to global 'window' object.

console.log(window.add())

ex:2:
var counter = 10;
console.log(window.counter); // 10

JavaScript engine will only release the memory allocated for them until when the global object loses the scope.
```

#### Normal function vs arrow function:
```
Syntax
Arguments binding
Use of this keyword
Using a new keyword
```


# Date: 21-09-2019

1.Differene between var, let and const

Main difference is Scoping rules

### a. Scoping rules:  
'var' varialbes are scoped to the nearest function.  
'let' variables are scoped to the nearest block.

```
Ex:
var a = 10;
var a = 20;
console.log(a); // 20

let b = 30;
let b = 40;
console.log(b);  // b already defined


Ex 1: 
var a = 10;
function func() {
  console.log(a);
  var a = 20;
}
console.log(a);  // undefined because var is fucntion scoped

Ex 2:
function func2() {
  
  {
    let b = 20;
    console.log(b)
  }
  
  console.log(b) // ReferenceError
}

*** drawback using var: confusing function scoped

```

### b) Hoisting:  
var varibales are 'hoisted' to the top of the block.  
can be accessible in their enclosing scope even before they are declared.
```
Ex:
function checkHosting1() {
  console.log(a);  // undefined
  var a = 10;
  console.log(a); // 10
}

Ex2:
function checkHosting2() {
  console.log(b) // Error: Reference error
  let b = 20;
  console.log(b); // 20
}
```

### c) Creating global/window object property:  
'var' creates a propery on window/global object.  
Not desired. Because if we use third party libraries, may override our varible.  
```
var a = 10;
let b = 20;

console.log(window.a) // 10
console.log(window.b) // undefined
```

### d) Redecleration  
'var' can be redeclared.  
'let raises Error.
```
var a = 10;
var a = 20;

let b = 30;
let b = 40;

console.log(a); // 20
console.log(b); // Error: b aleardy declared
```


## 2. Closures:  
A function which has access to another function's scope even after the fucntion returned.  
By creating a function inside another function.  
Outer function dont have the access to the innerr scope.  

Scope as below:
```
Global {
  Outer {
    Inner {
      access to both Outer & Global scope even after they returned
    }
  }
}
```

Ex:
```
var g_var = 10;

function outerFunc() {
  var o_var = 20;

  var innerFunc = function() {
    var i_var = 30;
    
    console.log(g_var); // 10
    console.log(o_var); // 20
    console.log(i_var); // 30
  }
  return innerFunc;
  
}

outerFunc();
```

## 8. prototype chain:  
Since JavaScript functions are objects, they can have properties. A particularly important property that each function has is called prototype.

prototype, which is itself an object, inherits from its parent’s prototype, which inherits from its parent’s prototype, and and so on. This is often referred to as the prototype chain. Object.prototype, which is always at the end of the prototype chain (i.e., at the top of the prototypal inheritance tree), contains methods like toString(), hasProperty(), isPrototypeOf(), and so on.



## call, apply and bind()  
```
**call: **method invokes a function with a given 'this' value and arguments provided one by one  
**apply:** Invokes the function and allows you to pass in arguments as an array.  
**bind(): **  returns a new function, allowing you to pass in an array and any number of arguments.  


let student = { name: 'Ram', age: 20 };
let employee = { name: 'Gopal', age: 30 };

function getDetails(salary, color) {
  console.log(this.name, this.age, salary, color);
}

getDetails.call(employee, 1000, 'blue'); // arguments
getDetails.apply(employee, [2000, 'red']); // args as an array

let newDetails = getDetails.bind(student); // bind returns a function
newDetails(30000, 'yello');

```


## 11. window, screen, document  
```
The window is the actual global object.

The screen is the screen, it contains properties about the user's display.

The document is where the DOM is.
```
