### Date: 21-09-2019

1. Differene between var, let and const

Main difference is Scoping rules

a. Scoping rules:

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

b) Hoisting:
```
var varibales are 'hoisted' to the top of the block.
can be accessible in their enclosing scope even before they are declared.

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

c) Creating global/window object property:
