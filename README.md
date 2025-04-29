# JavaScript Interview Questions (Basic to Advanced)

This document contains a comprehensive list of JavaScript interview questions along with explanations, examples, use cases, pros, and cons wherever relevant.

---

## Table of Contents

- [Basics](#basics)
- [Intermediate](#intermediate)
- [Advanced](#advanced)

---

## Basics

### 1. Explain the concept of "hoisting" in JavaScript

- JavaScript's default behavior of moving **declarations** to the top of the current scope.
- Functions and variables are hoisted differently.

**Example**:

```javascript
console.log(a); // undefined
var a = 5;
```

**Use Case**:

- Helps understand variable initialization order to prevent bugs.

---

### 2. Differences between `let`, `var`, and `const`

| Feature      | var                           | let       | const     |
| ------------ | ----------------------------- | --------- | --------- |
| Scope        | Function                      | Block     | Block     |
| Hoisting     | Yes (initializes `undefined`) | Yes (TDZ) | Yes (TDZ) |
| Reassignable | Yes                           | Yes       | No        |

**Use Case**:

- Use `let` for mutable variables and `const` for constants.

---

### 3. Difference between `==` and `===`

- `==` compares **values** after type coercion.
- `===` compares **values and types** without coercion.

**Example**:

```javascript
5 == '5'; // true
5 === '5'; // false
```

**Use Case**:

- Always prefer `===` for strict comparison.

---

### 4. What is the event loop in JavaScript?

- Manages execution of multiple pieces of code (callbacks, promises, etc.) by putting them into a queue.

**Use Case**:

- Handling async operations non-blockingly.

---

### 5. Explain event delegation

- Instead of attaching event listeners to each child element, you attach it to the parent and catch events during bubbling.

**Example**:

```javascript
document.getElementById('parent').addEventListener('click', function(event) {
  if (event.target.tagName === 'BUTTON') {
    console.log('Button clicked!');
  }
});
```

**Use Case**:

- Better performance when dealing with many elements.

---

### 6. Explain how `this` works

- Refers to the object that is executing the current function.

**Use Case**:

- In event handlers, constructors, and methods.

---

### 7. Describe the difference between a cookie, sessionStorage and localStorage

| Feature              | Cookie      | sessionStorage | localStorage |
| -------------------- | ----------- | -------------- | ------------ |
| Expiration           | Manual/Auto | On tab close   | Manual       |
| Size                 | 4KB         | 5MB            | 5MB          |
| Accessible by Server | Yes         | No             | No           |

**Use Case**:

- `sessionStorage` for one-time tabs, `localStorage` for persistent state, `cookies` for server-side sessions.

---

### 8. Describe the difference between `<script>`, `<script async>`, and `<script defer>`

| Attribute | Behavior                                         |
| --------- | ------------------------------------------------ |
| script    | Blocking execution                               |
| async     | Loads script asynchronously, may execute anytime |
| defer     | Loads async, executes after HTML parsing         |

**Use Case**:

- `defer` for scripts dependent on DOM, `async` for independent analytics.

---

### 9. What's the difference between null, undefined and undeclared?

- `null`: Explicit empty value.
- `undefined`: Declared but not initialized.
- `undeclared`: Never declared.

---

### 10. Difference between `.call` and `.apply`

- Both invoke functions with a context (`this`). Difference is in arguments passing.
- `.call(context, arg1, arg2,...)`
- `.apply(context, [args])`

**Example**:

```javascript
function greet(name) { console.log(this.message + name); }
greet.call({message: 'Hi '}, 'John');
greet.apply({message: 'Hi '}, ['John']);
```

---

### 11. Explain `Function.prototype.bind`

- Returns a new function with `this` permanently bound to a specified object.

**Example**:

```javascript
let greet = function() { console.log(this.name); }
let person = { name: 'John' };
let greetPerson = greet.bind(person);
greetPerson();
```

---

### 12. Arrow function advantages in constructor

- Lexical scoping of `this`. No rebinding issues.

**Use Case**:

- When passing callbacks inside constructors.

---

### 13. Prototypal inheritance

- Objects inherit directly from other objects.

**Example**:

```javascript
const parent = { greet() { console.log('Hello'); } };
const child = Object.create(parent);
child.greet();
```

---

### 14. Difference between:

```javascript
function Person() {}
const person = Person(); // Undefined behavior
const person = new Person(); // Proper instance
```

---

### 15. Usage of `foo` in `function foo()` vs `var foo = function()`

- Named vs anonymous function difference.
- Hoisting available in named function.

---

### 16. Use case for anonymous functions

- Inline callbacks like event handlers, array functions.

---

### 17. Ways to create objects

- Object literal
- `new Object()`
- `Object.create()`
- Classes

---

### 18. Closure in JavaScript

- A function that captures variables from outer scope.

**Use Case**:

- Private variables and currying.

---

### 19. Higher-order function

- Functions that take or return other functions.

**Example**:

```javascript
function multiply(x) {
  return function(y) {
    return x * y;
  }
}
``` 

## 21. Describe event bubbling in JavaScript and browsers
*(Basic)*

**Explanation:**
Event bubbling is the event propagation mode where the event starts from the deepest target element and bubbles up to the window.

**Example:**
```javascript
document.getElementById('child').addEventListener('click', function() {
  console.log('Child Clicked');
});

document.getElementById('parent').addEventListener('click', function() {
  console.log('Parent Clicked');
});
```

**Use Case:**
- Implementing centralized event handling (event delegation).

**Pros:**
- Efficient event handling.

**Cons:**
- Unintended handlers if not stopped.

---

## 22. Describe event capturing in JavaScript and browsers
*(Basic)*

**Explanation:**
In event capturing, the event starts from the window and propagates down to the target element.

**Example:**
```javascript
document.getElementById('child').addEventListener('click', function() {
  console.log('Child Clicked during Capturing');
}, true);
```

**Use Case:**
- When you need to intercept events before they reach the target.

**Pros:**
- More control at the start of propagation.

**Cons:**
- Less intuitive, rarely needed.

---

## 23. What is the difference between mouseenter and mouseover event in JavaScript and browsers?
*(Basic)*

**Explanation:**
- `mouseover`: triggers every time the mouse moves over a child element.
- `mouseenter`: triggers only when the mouse enters the element.

**Example:**
```javascript
// mouseenter triggers once
// mouseover triggers on each child
```

**Use Case:**
- Prefer `mouseenter` to avoid excessive event firing.

---

## 24. What is 'use strict'; in JavaScript for?
*(Advanced)*

**Explanation:**
- Enforces stricter parsing and error handling in your JavaScript code.

**Example:**
```javascript
'use strict';
x = 3.14; // Error because x is not declared
```

**Pros:**
- Safer, more predictable code.

**Cons:**
- Slightly more verbose when fixing old habits.

---

## 25. Explain the difference between synchronous and asynchronous functions in JavaScript
*(Basic)*

**Explanation:**
- **Synchronous**: Operations happen sequentially, blocking.
- **Asynchronous**: Operations happen independently, non-blocking.

**Example:**
```javascript
setTimeout(() => console.log("Async call"), 1000);
console.log("Sync call");
```

**Output:**
```
Sync call
Async call
```
# Q&A Section

## Basic Questions

**Q: Explain the difference between synchronous and asynchronous functions in JavaScript**  
A: Synchronous functions execute code sequentially, meaning each operation must complete before the next one starts. Asynchronous functions allow code execution to continue without waiting for a task to complete, often using callbacks, promises, or async/await syntax.

Example:  
```javascript
// Synchronous example
console.log('Start');
console.log('Middle');
console.log('End');

// Asynchronous example
console.log('Start');
setTimeout(() => console.log('Middle'), 1000); // Executes after 1 second
console.log('End');

##Q: **Explain AJAX in as much detail as possible** **
A: AJAX (Asynchronous JavaScript and XML) is a technique for creating dynamic web applications. It allows fetching data from a server asynchronously, meaning the web page does not reload or refresh during the data fetch. AJAX uses technologies like XMLHttpRequest or fetch() to send and receive data, often in JSON format.

Example using fetch():

JavaScript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
##Q: **What are the differences between XMLHttpRequest and fetch() in JavaScript and browsers?**
A: XMLHttpRequest is an older API for making HTTP requests, supporting event-based callbacks. fetch() is a modern API that simplifies request handling using promises and provides better readability and error handling.

Example using XMLHttpRequest:

JavaScript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data', true);
xhr.onload = function () {
  if (xhr.status === 200) {
    console.log(JSON.parse(xhr.responseText));
  }
};
xhr.send();
Example using fetch():

JavaScript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
**Q: What are the various data types in JavaScript?**
A: JavaScript has the following data types:

Primitive: string, number, boolean, null, undefined, symbol, bigint
Non-primitive: object (e.g., arrays, functions, etc.)
Example:

JavaScript
**// Primitive types**
const name = 'John'; // string
const age = 30;      // number
const isAdmin = true; // boolean
const nothing = null; // null
let notDefined;      // undefined
const uniqueId = Symbol('id'); // symbol
const largeNumber = 123456789012345678901234567890n; // bigint

**// Non-primitive type**
const user = { name: 'John', age: 30 }; // object
Q: What language constructs do you use for iterating over object properties and array items in JavaScript?
A: For arrays, you can use for, for...of, or forEach(). For objects, you can use for...in or Object.keys() combined with iteration methods like map().

Examples:

JavaScript
**// Iterating over an array**
const array = [1, 2, 3];
array.forEach(item => console.log(item));

// Iterating over an object
const obj = { a: 1, b: 2, c: 3 };
for (const key in obj) {
  console.log(`${key}: ${obj[key]}`);
}
**Q: What are the benefits of using spread syntax in JavaScript and how is it different from rest syntax?**
A: Spread syntax (...) is used to expand elements of an array/object, while rest syntax is used to collect remaining elements into an array/object. Spread is useful for merging or copying, while rest is useful for destructuring.

Example:

JavaScript
// Spread syntax
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5]; // [1, 2, 3, 4, 5]

// Rest syntax
const [first, ...rest] = arr2; // first = 1, rest = [2, 3, 4, 5]
Intermediate Questions
**Q: How do you abort a web request using AbortController in JavaScript?**
A: AbortController provides a signal that can be passed to a fetch request via its signal option. You can abort the request by calling the abort() method on the controller instance.

Example:

JavaScript
const controller = new AbortController();
const { signal } = controller;

fetch('https://api.example.com/data', { signal })
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => {
    if (error.name === 'AbortError') {
      console.log('Request aborted');
    } else {
      console.error('Error:', error);
    }
  });

// Abort the request after 1 second
setTimeout(() => controller.abort(), 1000);
**Q: Explain the differences between CommonJS modules and ES modules in JavaScript**
A: CommonJS modules (require) are synchronous and used in Node.js. ES modules (import/export) are asynchronous, modern, and work natively in browsers.

Example:

JavaScript
// CommonJS
const module = require('module');
module.doSomething();

// ES Modules
import { doSomething } from './module.js';
doSomething();



# JavaScript Questions and Answers

**## 41. What are the differences between Map/Set and WeakMap/WeakSet in JavaScript? *(Basic)***

- **Map/Set**:
  - **Map** stores key-value pairs, while **Set** stores unique values.
  - Keys in **Map** can be any data type.
  - Both are iterable, allowing you to loop through their elements.

- **WeakMap/WeakSet**:
  - **WeakMap** holds key-value pairs where keys are objects, and values can be any type.
  - **WeakSet** holds a collection of objects, and no primitive values are allowed.
  - They do not prevent garbage collection of their keys (or objects in the set).
  - They are not iterable.

---

## 42. Why might you want to create static class members in JavaScript? *(Intermediate)*

Static class members:
- Belong to the class itself, not to instances of the class.
- Are used for utility functions or shared data that do not depend on instance-specific data, such as configuration settings or cache management.

Example:
```javascript
class Example {
  static staticMethod() {
    return 'This is a static method!';
  }
}

console.log(Example.staticMethod()); // Outputs: This is a static method!
**43. What are Symbols used for in JavaScript? (Intermediate)**
Symbols are unique and immutable data types used as keys for object properties.
They prevent property name collisions in objects and allow creating hidden properties that won't interfere with other code.
Example:

JavaScript
const uniqueKey = Symbol('description');
const obj = {
  [uniqueKey]: 'value'
};

console.log(obj[uniqueKey]); // Outputs: 'value'
**44. What are server-sent events? (Advanced)**
Server-Sent Events (SSE) enable servers to push real-time updates to the browser over a single HTTP connection.
They are implemented using the EventSource API.
Commonly used for live updates, like news feeds or stock prices.
Example:

JavaScript
const eventSource = new EventSource('https://example.com/events');
eventSource.onmessage = (event) => {
  console.log(event.data);
};
**45. What are JavaScript object property flags and descriptors? (Advanced)**
Property flags and descriptors provide metadata about object properties.
Flags include:
writable – If true, the value can be changed.
enumerable – If true, the property shows up in loops.
configurable – If true, the property can be deleted or modified.
Example:

JavaScript
const obj = {};
Object.defineProperty(obj, 'prop', {
  value: 42,
  writable: false,
  enumerable: true,
  configurable: true
});

console.log(obj.prop); // Outputs: 42
**46. What are JavaScript object getters and setters for? (Intermediate)**
Getters retrieve property values, while setters define custom behavior when setting property values.
Useful for encapsulating logic behind property access.
Example:

JavaScript
const obj = {
  _value: 0,
  get value() {
    return this._value;
  },
  set value(newValue) {
    this._value = newValue > 0 ? newValue : 0;
  }
};

obj.value = 10;
console.log(obj.value); // Outputs: 10
**47. What are proxies in JavaScript used for? (Advanced)**
Proxies allow you to intercept and customize operations on objects, such as property access or assignment.
Useful for validation, logging, or implementing reactive programming.
Example:

JavaScript
const handler = {
  get(target, prop) {
    return prop in target ? target[prop] : 'Property does not exist';
  }
};

const proxy = new Proxy({}, handler);
proxy.name = 'JavaScript';
console.log(proxy.name); // Outputs: 'JavaScript'
console.log(proxy.age);  // Outputs: 'Property does not exist'
**48. What tools and techniques do you use for debugging JavaScript code? (Intermediate)**
Tools:

Browser Developer Tools (Chrome, Firefox, etc.)
Debugging in IDEs like VSCode
Online tools like JSFiddle or CodePen
Techniques:

Using console.log() for quick debugging.
Setting breakpoints in Developer Tools.
Leveraging the debugger keyword.
Writing unit tests to catch bugs early.
**49. What are workers in JavaScript used for? (Advanced)**
Workers enable running JavaScript code in background threads, separate from the main execution thread.
They improve performance by handling CPU-intensive tasks without blocking the UI.
Example:

JavaScript
const worker = new Worker('worker.js');
worker.onmessage = (event) => {
  console.log(event.data);
};
worker.postMessage('Start');
**50. How does JavaScript garbage collection work? (Advanced)**
JavaScript uses automatic garbage collection to manage memory.
The engine identifies and removes objects that are no longer reachable (e.g., out of scope or unreferenced).
Common algorithms:
Mark-and-Sweep: Marks objects reachable from the root, then sweeps and collects unmarked objects.
