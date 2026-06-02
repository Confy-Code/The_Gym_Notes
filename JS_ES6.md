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

21. Promises: Full structure of a Promises
```javascript
const myPromise = new Promise(function (resolve, reject) {
  const success = true;

  setTimeout(function () {
    if (success) {
      resolve('Ice cream is ready!');
    } else {
      reject('Sorry, no ice cream today.');
    }
  }, 1000);
});

console.log(myPromise);

myPromise.then(
  function (message) {
    console.log('Success:', message);
  },
  function (error) {
    console.log('Failed:', error);
  }
);
```
---

22. **PROXY**: An object that stands in front of another object and intercepts operations on it
```javascript
const richard = {status: "looking for a job"};
const handler = {
  get(target, property) {
    if (property === "status") {
      return "hired";
    }
    return target[property];
  }
};
const richardProxy = new Proxy(richard, handler);
console.log(richardProxy.status); // Output: "hired"

// using set trap to intercept property assignment
const handler = {
  set(target, property, value) {
    if (property === "status") {
      console.log("Status cannot be changed.");
      return false; // Prevent the assignment
    }
    target[property] = value; // Allow other properties to be set
    return true;
  }
};
const richardProxy = new Proxy(richard, handler);
richardProxy.status = "hired"; // Output: "Status cannot be changed."

richardProxy.name = "Richard"; // This will work, as it's not the "status" property
console.log(richardProxy.name); // Output: "Richard"
```
-- 

**OTHER TRAPS**:

1. The get trap: Intercepts property access.
2. The set trap: Intercepts property assignment.  
3. The has trap: Intercepts the in operator.
   ```javascript
   const handler = {
     has(target, property) {
       if (property === "status") {
         return false; // Pretend that the "status" property does not exist
       }
       return property in target; // Default behavior for other properties
     }
   };
    const richardProxy = new Proxy(richard, handler);
    console.log("status" in richardProxy); // Output: false
    console.log("name" in richardProxy); // Output: true (assuming "name" is a property of the target object)
   ```
4. The deleteProperty trap: Intercepts the delete operator.
5. The apply trap: Intercepts function calls.
6. The construct trap: Intercepts object instantiation with the new operator.
7. The getOwnPropertyDescriptor trap: Intercepts Object.getOwnPropertyDescriptor() calls.
8. The ownKeys trap: Intercepts Object.keys(), Object.getOwnPropertyNames(), ...

**DIFFERENCE BETWEEN PROXY & GETTER/SETTER**
==> ES5 getter/setter: beforehand defined properties, only intercepts property access and assignment, cannot intercept other operations like function calls or object instantiation.

==> ES6 Proxy: can intercept a wide range of operations (property access, assignment, function calls, object instantiation, etc.), allows for dynamic behavior and more flexible object manipulation.

-----






