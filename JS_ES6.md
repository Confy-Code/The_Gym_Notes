**Author:** Confy-Code
**Date:** 2026-May-29

---

ES6 - UDACITY NOTES
===

1. * let and const: block-scoped variable declaration, no hoisting, no redeclaration
* var: function-scoped variable declaration, hoisting, redeclaration allowed

---

2. Template literals --> (`${}`)
*Example:*
```javascript
const name = "Alice";
const greeting = `Hello, ${name}!`;
```
---

3. Object literal shorthand (elimination of keyword 'function')
*Example:*
```javascript
const obj = {
  method() {
    console.log("This is a method.");
  }
};

instead of:
const obj = {
  method: function() {
    console.log("This is a method.");
  }
};  
```
---

4. Array properties ==> Array.prototype.decimalfy [TO SEE]

5. Pythonic capitalize() equivalence in JS: 
```javascript
function capitalize(str) {
  return str.charAt(0).toUpperCase() + str.slice(1);
}
```
---

6. Rest parameter (2 uses: destructuring an array , variadic functions)
```javascript
// Destructuring an array   
const [first, ...rest] = [1, 2, 3, 4];
// Variadic function
function sum(...numbers) {
  return numbers.reduce((acc, num) => acc + num, 0);
}
```
---

7. Arrow functions are always expressions (Arrow function expressions)
8. Arrow functions syntax(concise and block body syntaces)
```javascript
// Concise body syntax
const add = (a, b) => a + b;
// Block body syntax
const add = (a, b) => {
    return a + b;
    };
```
---

9.  JS classes - use static functions for comparing the obj of the 
		same class
```javascript
class Person {
  constructor(name) {
    this.name = name;
  }

  static compare(person1, person2) {
    return person1.name === person2.name;
  }
}
```
---

10. "Super" is used to pass variables child --> Parent class

11. Symbol(description): Handle duplicate properties in an object.
```javascript
const obj1 = {
  name: "Confy",
  [Symbol("id")]: 123
  [Symbol("id")]: 456
};
```
---

12. [Symbol.iterator](): to simulate linked-lists
```javascript
const arr = [1, 2, 3];
arr_values = arr[Symbol.iterator]();
console.log(arr_values.next()); // { value: 1, done: false }

while(!arr_values.next().done) {
  console.log(arr_values.next().value);
}
```
---

13.  Sets operations: .add, .delete, .clear
14.  Iterate through sets: setIterator & for...of
```javascript
const mySet = new Set([1, 2, 3]);
const setIterator = mySet.values();

//using for...of loop
for (const value of mySet) {
  console.log(value);
}

//using setIterator
let result = setIterator.next();

```
---

15.  Weak sets: only objects (use it for double-deletion of objects)
```javascript
const weakSet = new WeakSet();
let obj1 = { name: "Confy" };
weakSet.add(obj1);
console.log(weakSet.has(obj1)); // true
obj1 = null; // Remove reference to the object
// After garbage collection, the object will be removed from the weak set
```
16.  Garbage collection: automatic memory management, removes unused objects from memory

17.  Map ops: .set(), .delete(key), .clear, .has, .get
```javascript
const myMap = new Map();
myMap.set("key1", "value1");
myMap.set("key2", "value2");
console.log(myMap.get("key1")); // value1
console.log(myMap.has("key2")); // true
myMap.delete("key1");
myMap.clear();
```
---

18.  Map iterations: MapIterator, for...of, .forEach()
```javascript
const myMap = new Map([["key1", "value1"], ["key2", "value2"]]);
// Using MapIterator
const mapIterator = myMap.entries();

// Using for...of loop
for (const [key, value] of myMap) {
  console.log(`${key}: ${value}`);
}
// Using .forEach() method
myMap.forEach((value, key) => {
  console.log(`${key}: ${value}`);
});
``` 
---

19.  destructuring needs brackets!
20.  weakMap(): only object-keys
```javascript
const weakMap = new WeakMap();
let objKey = { name: "Confy" };
weakMap.set(objKey, "This is a value");
console.log(weakMap.get(objKey)); // This is a value
objKey = null; // Remove reference to the object
// After garbage collection, the object and its associated value will be removed from the weak map
```
---