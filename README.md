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
 **26. What are the pros and cons of using Promises instead of callbacks in JavaScript?**
Explanation:

Promises provide a cleaner, more manageable way to deal with asynchronous operations compared to nested callbacks ("callback hell").


Aspect	Promises	Callbacks
Readability	Cleaner, chainable .then()	Nested and harder to read
Error Handling	Centralized with .catch()	Each callback needs its own
Chaining Operations	Easy	Hard
Example:

javascript
Copy
Edit
// Using Promise
fetch('/api/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));

// Using Callback
function fetchData(callback) {
  // simulate API
  setTimeout(() => callback(null, "Data received"), 1000);
}
fetchData((err, data) => {
  if (err) console.error(err);
  else console.log(data);
});
Use Case:

Always prefer Promises for clean async operations.

**27. Explain AJAX in as much detail as possible**
Explanation:

AJAX (Asynchronous JavaScript and XML) allows web pages to communicate with servers asynchronously without reloading the page.

Originally used XML; now JSON is common.

Example:

javascript
Copy
Edit
const xhr = new XMLHttpRequest();
xhr.open('GET', '/api/data', true);
xhr.onload = function() {
  if (xhr.status === 200) {
    console.log(JSON.parse(xhr.responseText));
  }
};
xhr.send();
Use Case:

Dynamic content loading (e.g., new feeds, weather updates).

28. What are the advantages and disadvantages of using AJAX?

Advantages	Disadvantages
No full page reload	Can complicate browser history
Better UX with dynamic updates	SEO can suffer
Faster interactions	Needs careful error handling
Use Case:

Infinite scrolling feeds, dynamic forms.

29. What are the differences between XMLHttpRequest and fetch() in JavaScript and browsers?

Feature	XMLHttpRequest	fetch()
Syntax	Verbose	Cleaner, promise-based
Streams	Harder	Native ReadableStream
Error Handling	Manual	Built-in .catch() chaining
Example (fetch):

javascript
Copy
Edit
fetch('/api/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
Use Case:

Always prefer fetch() unless supporting very old browsers.

30. How do you abort a web request using AbortController in JavaScript?
Explanation:

AbortController provides a way to abort ongoing fetch requests.

Example:

javascript
Copy
Edit
const controller = new AbortController();
const signal = controller.signal;

fetch('/api/data', { signal })
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => {
    if (error.name === 'AbortError') {
      console.log('Fetch aborted');
    }
  });

// Abort after 1 second
setTimeout(() => controller.abort(), 1000);
Use Case:

Cancel fetch when users navigate away or switch pages.

31. What are JavaScript polyfills for?
Explanation:

Polyfills are pieces of code (often libraries) that implement features on older browsers that do not natively support them.

Example:

javascript
Copy
Edit
if (!Array.prototype.includes) {
  Array.prototype.includes = function(searchElement) {
    return this.indexOf(searchElement) !== -1;
  };
}
Use Case:

Ensure backward compatibility for modern JS features.

32. Why is extending built-in JavaScript objects not a good idea?
Explanation:

Extending built-in prototypes (like Array.prototype, Object.prototype) can cause conflicts with future JavaScript features or other libraries.

Example:

javascript
Copy
Edit
// BAD Practice
Array.prototype.customMethod = function() { };
Use Case:

Avoid prototype pollution and bugs caused by unexpected behavior.

33. Why is it a good idea to leave the global JavaScript scope untouched?
Explanation:

Modifying global scope increases the risk of name collisions and hard-to-debug bugs.

Example:

javascript
Copy
Edit
// BAD: Overwriting native objects or window properties
window.alert = function() {
  console.log('Hacked alert!');
};
Best Practice:

Use modules, IIFE (Immediately Invoked Function Expressions) to limit scope.

34. Explain the differences between CommonJS modules and ES modules in JavaScript

Feature	CommonJS	ES Modules
Syntax	require() / module.exports	import / export
Loading	Synchronous	Asynchronous
Used in	Node.js mainly	Modern browsers + Node.js
Example:

javascript
Copy
Edit
// CommonJS
const fs = require('fs');

// ES Module
import fs from 'fs';
Use Case:

Use ES Modules in front-end or modern back-end codebases.

35. What are the various data types in JavaScript?

Primitive Types	Non-Primitive Types
Number	Object
String	Array
Boolean	Function
Null	Date
Undefined	RegExp
Symbol	
BigInt	
36. What language constructs do you use for iterating over object properties and array items in JavaScript?
Explanation:

Arrays: for, for...of, forEach()

Objects: for...in, Object.keys(), Object.entries()

Example:

javascript
Copy
Edit
// Array
for (const item of ['a', 'b', 'c']) {
  console.log(item);
}

// Object
const obj = { a: 1, b: 2 };
for (const key in obj) {
  console.log(key, obj[key]);
}
37. What are the benefits of using spread syntax in JavaScript and how is it different from rest syntax?
Explanation:

Spread (...) expands elements.

Rest (...) collects elements.

Example:

javascript
Copy
Edit
// Spread
const arr = [1, 2, 3];
const newArr = [...arr, 4, 5];

// Rest
function sum(...args) {
  return args.reduce((acc, val) => acc + val, 0);
}
Use Case:

Spread for cloning/merging, Rest for collecting function arguments.

38. What are iterators and generators in JavaScript and what are they used for?

Concept	Description
Iterator	Object with next() method
Generator	Function that yields multiple values
Example (Generator):

javascript
Copy
Edit
function* generateNumbers() {
  yield 1;
  yield 2;
  yield 3;
}
const gen = generateNumbers();
console.log(gen.next()); // { value: 1, done: false }
Use Case:

Custom sequence generation, lazy evaluation.

39. Explain the difference between mutable and immutable objects in JavaScript

Aspect	Mutable	Immutable
Change allowed	Yes	No
Example	Arrays, Objects	Strings, Numbers (primitive)
Example:

javascript
Copy
Edit
const arr = [1,2,3];
arr.push(4); // Mutated

const str = 'hello';
const newStr = str + ' world'; // New string created
40. What is the difference between a Map object and a plain object in JavaScript?

Feature	Map	Plain Object
Key Types	Any (including objects)	Strings and Symbols only
Iteration Order	Ordered	Unordered (older engines)
Size	size property	Manual calculation needed
Example:

javascript
Copy
Edit
const map = new Map();
map.set('key', 'value');
map.set({}, 'object key');

const obj = { key: 'value' };
Use Case:

Use Map when keys are unknown or complex.
