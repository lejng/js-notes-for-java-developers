# Java Script Notes for Java Developers

## 📘 Table of Contents
- [1. Variables](#1-variables)  
- [2. Strings](#2-strings)  
- [3. Objects](#3-objects)  
- [4. Collections](#4-collections)  
  - List  
  - Map  
  - Set 
  - Object.keys, values, entries
- [5. Functions](#5-functions)  
- [6. Classes](#6-classes)  
- [7. Promise and async/await](#7-promise-and-asyncawait)  
  - Promise 
  - Async and await 

---

## 1. Variables
- Java
```Java
String name = "John";
final String CONSTANT = "value";
```
- Java Script
```JavaScript
let name = "John";     
const CONSTANT = "value";
// do not use var declaration old aproach
var old = 99;
```

## 2. Strings
```Java
String name = "John";
String template = String.format("Hello %s", name);
template.equals(name);
templat.equalsIgnoreCase(name);
str.length();
```
- Java Script
```JavaScript
let name = "John";     
let template = `Hello ${name}`;
template === name;
template.toLowerCase() === name.toLowerCase();
str.length;
```

## 3. Objects
```JavaScript
let user = {     // an object
  name: "John",  // by key "name" store value "John"
  age: 30        // by key "age" store value 30
};
// get property values of the object:
alert( user.name ); // John
alert( user.age ); // 30
```

## 4. Collections
- List
```JavaScript
// list
let arr = [];
const users = ["John", "Anna", "Mike"];
// add
users.push("Kate"); // ["John", "Anna", "Mike", "Kate"]
// delete
users.pop(); // ["John", "Anna", "Mike"]
// find index
const index = users.indexOf("Anna"); // 1
// check contains
const hasMike = users.includes("Mike"); // true
// map
const upper = users.map(name => name.toUpperCase()); 
// ["JOHN", "ANNA", "MIKE"]
arr.forEach(item => console.log(item));
```
- Map
```JavaScript
const userMap = new Map();
// size
userMap.size();
// add
userMap.set("john", {age: 30, city: "NY"});
userMap.set("anna", {age: 25, city: "LA"});
// get
const john = userMap.get("john"); // {age: 30, city: "NY"}
// check
const hasAnna = userMap.has("anna"); // true
// for
userMap.forEach((value, key) => {
    console.log(`${key}: ${value.age}`);
});
// return [key, value] array
const entries = Array.from(userMap.entries());
// return keys array
Array.from(userMap.keys());
// return values array
Array.from(userMap.values());
```
- Set
```JavaScript
let set = new Set("oranges", "apples");
set.add("bananas");
// set keeps only unique values
alert(set.size);

for (let value of set) {
    alert(value);
}

// the same with forEach:
set.forEach((value, valueAgain, set) => {
  alert(value);
});
```
- Object.keys, values, entries
```JavaScript
let obj = new Map([
    ['cucumber', 500],
    ['tomatoes', 350],
    ['onion',    50]
]);
Object.keys(obj) //returns an array of keys.
Object.values(obj) //returns an array of values.
Object.entries(obj) //returns an array of [key, value] pairs.
```
## 5. Functions
- Java
```java
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
}
```
- Java Script
```JavaScript
function add(a, b) {
    return a + b;
}

// or array function
const add = (a, b) => a + b;
```

## 6. Classes
- Java
```java
public class Person {
    private String name;

    public Person(String name) {
        this.name = name;
    }

    public String getName() {
        return this.name;
    }
}
```
- Java Script
```JavaScript
class Person {
    constructor(name) {
        this.name = name;
    }
    
    getName() {
        return this.name;
    }
}
```

## 7. Promise and async/await
- Promise
```JavaScript
let userData = null;
fetch('https://jsonplaceholder.typicode.com/users/1')
    .then(response => response.json())
    .then(user => {
        userData = user;
        console.log('Response:', userData);
    })
    .catch(error => {
        console.error('Error:', error);
    });

// Probably null because request in progress
console.log('Response:', userData); // null

```
- Async and await
```JavaScript
async function fetchData() {
    const data = await fetch('/api').then(r => r.json());
    console.log(data);
}

async function fetchDataExample2() {
    const response = await fetch('/api');
    const data = await response.json();
    console.log(data);
}

const fetchDataArrayFunction = async () => {
    const data = await fetch('/api').then(r => r.json());
    console.log(data);
};

fetchData();
fetchDataExample2();
fetchDataArrayFunction();
```