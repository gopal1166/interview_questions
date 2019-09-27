# Date: 27-09-2019

HOF (Higher Order Functions):  
A function witch takes another function(callback) as an argument or return function value.  
Built-in HOF:  
```
Array.proptype.map, 
Array.proptype.filter,
Array.proptype.reduce
```

### 1.map():  
Takes a function as argument and calls it on every element and creates a new array.  
Ex: Create a new list having squares of elements from a list of elements.  
#### Without HOF:
```
l = [1, 2, 3]
a = []
for(let i=0; i < l.length; i++) {
  a.push(l[i] * 2)
}

console.log(a)
```  

#### With HOF:
```
l = [1, 2, 3]
const a = l.map(item => item * 2)
console.log(a)
```

### 2.filter():  
Takes a function as an argument and creates a new list with all elements  
that passes the test provided by the callback function.  
Ex: Filter all the persons whose age is above or equal to 18 from the below.

#### Without HOF:
```
const persons = [
  { name: 'Ram', age: 10 },
  { name: "Gopal", age: 20 },
  { name: "Venkat", age: 30 }
]
let majors = []
for(let i=0; i < persons.length; i++) {
  if (persons[i].age >= 18) {}
}
console.log(a)
```
