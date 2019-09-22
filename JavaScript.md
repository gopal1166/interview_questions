# Date: 21-09-2019

1. Differene between var, let and const

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

