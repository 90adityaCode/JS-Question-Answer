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
 
26. What are the pros and cons of using Promises instead of callbacks in JavaScript?
(Intermediate)

Explanation: Promises provide a cleaner, more manageable way to handle asynchronous code compared to callbacks, avoiding deeply nested "callback hell".

Example:

javascript
Copy
Edit
// Using Promises
fetch('https://api.example.com')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
Use Case:

Better error handling and readability for async flows.

Pros:

Avoids callback nesting.

Error handling is streamlined with .catch.

Cons:

Slightly more overhead when learning compared to callbacks.

27. Explain AJAX in as much detail as possible
(Basic)

Explanation: AJAX (Asynchronous JavaScript and XML) is a technique to send/receive data from a server asynchronously without refreshing the web page.

Example:

javascript
Copy
Edit
const xhr = new XMLHttpRequest();
xhr.open('GET', '/api/data');
xhr.onload = function() {
  console.log(xhr.responseText);
};
xhr.send();
Use Case:

Load data in background (e.g., search autocomplete).

Pros:

Improves user experience.

Partial updates without full page reloads.

Cons:

Increases complexity.

SEO challenges for dynamic content.

28. What are the advantages and disadvantages of using AJAX?
(Basic)

Advantages:

Enhances speed and usability.

Allows asynchronous data loading.

Disadvantages:

SEO issues (for SPAs).

Complexity in managing async flows.

CORS issues across domains.

29. What are the differences between XMLHttpRequest and fetch() in JavaScript and browsers?
(Basic)

Explanation:

XMLHttpRequest: older, more verbose API.

fetch(): modern Promise-based API for requests.

Example:

javascript
Copy
Edit
// fetch
fetch('/api/data')
  .then(response => response.json())
  .then(data => console.log(data));
Use Case:

Prefer fetch for simpler, promise-based requests.

Pros of fetch:

Cleaner, promise-based API.

Streamlined response handling.

Cons of fetch:

Requires manual error checking (response.ok).

30. How do you abort a web request using AbortController in JavaScript?
(Basic)

Explanation: AbortController allows you to cancel a fetch request.

Example:

javascript
Copy
Edit
const controller = new AbortController();
const signal = controller.signal;

fetch('/api/data', { signal })
  .catch(err => console.log('Fetch aborted:', err));

controller.abort(); // Aborts the request
Use Case:

Useful when a user navigates away from a page before a request completes.

31. What are JavaScript polyfills for?
(Advanced)

Explanation: Polyfills are pieces of code that implement modern features on older browsers that don't natively support them.

Example:

javascript
Copy
Edit
if (!Array.prototype.includes) {
  Array.prototype.includes = function(element) {
    return this.indexOf(element) !== -1;
  };
}
Use Case:

Ensuring compatibility across older browsers.

32. Why is extending built-in JavaScript objects not a good idea?
(Intermediate)

Explanation: It can cause conflicts and unexpected behavior with other code or future JavaScript versions.

Example:

javascript
Copy
Edit
Array.prototype.myMethod = function() {}; // Bad practice
Use Case:

Avoid polluting prototypes.

33. Why is it a good idea to leave the global JavaScript scope untouched?
(Intermediate)

Explanation: Adding global variables can cause name clashes, overwriting important variables or libraries.

Use Case:

Use modules or closures to encapsulate code.

34. Explain the differences between CommonJS modules and ES modules in JavaScript
(Intermediate)

Explanation:

CommonJS (require, module.exports) — used mainly in Node.js.

ES Modules (import, export) — standard for modern JavaScript.

Use Case:

Prefer ES Modules in frontend; CommonJS in older Node.js codebases.

35. What are the various data types in JavaScript?
(Basic)

Explanation:

Primitive Types: String, Number, Boolean, null, undefined, Symbol, BigInt

Object Types: Object, Array, Function

36. What language constructs do you use for iterating over object properties and array items in JavaScript?
(Basic)

Examples:

Arrays: for, forEach, map, for...of

Objects: for...in, Object.keys()

37. What are the benefits of using spread syntax in JavaScript and how is it different from rest syntax?
(Basic)

Explanation:

Spread (...) expands elements.

Rest (...) collects elements into an array.

Example:

javascript
Copy
Edit
// Spread
const arr = [1, 2, 3];
const newArr = [...arr, 4];

// Rest
function sum(...nums) {
  return nums.reduce((acc, n) => acc + n, 0);
}
38. What are iterators and generators in JavaScript and what are they used for?
(Advanced)

Explanation:

Iterator: An object that provides a sequence via next().

Generator: A function that can pause (yield) and resume.

Example:

javascript
Copy
Edit
function* generator() {
  yield 1;
  yield 2;
}
const gen = generator();
gen.next(); // {value:1, done:false}
39. Explain the difference between mutable and immutable objects in JavaScript
(Intermediate)

Explanation:

Mutable: Can be changed (e.g., Objects, Arrays).

Immutable: Cannot be changed once created (e.g., Strings, Numbers).

40. What is the difference between a Map object and a plain object in JavaScript?
(Basic)

Explanation:

Map allows keys of any type and preserves insertion order.

Plain object keys are always strings or symbols.

41. What are the differences between Map/Set and WeakMap/WeakSet in JavaScript?
(Basic)

Explanation:

WeakMap/WeakSet hold weak references — keys must be objects and don't prevent garbage collection.

42. Why might you want to create static class members in JavaScript?
(Intermediate)

Explanation: Static members belong to the class itself, not instances.

Use Case:

Utility methods (e.g., Math.random()).

43. What are Symbols used for in JavaScript?
(Intermediate)

Explanation: Symbols are unique, immutable identifiers, often used for private object properties.

44. What are server-sent events?
(Advanced)

Explanation: A way to push updates from server to client over HTTP connection (EventSource API).

45. What are JavaScript object property flags and descriptors?
(Advanced)

Explanation: Controls property behavior — writable, enumerable, configurable.

Example:

javascript
Copy
Edit
Object.defineProperty(obj, 'key', {
  writable: false
});
46. What are JavaScript object getters and setters for?
(Intermediate)

Explanation: Custom behavior when accessing or setting properties.

Example:

javascript
Copy
Edit
const obj = {
  get name() { return 'value'; },
  set name(val) { console.log(val); }
};
47. What are proxies in JavaScript used for?
(Advanced)

Explanation: Proxies intercept operations on objects (get, set, etc.).

Use Case:

Validation, debugging, auto-populating properties.

48. What tools and techniques do you use for debugging JavaScript code?
(Intermediate)

Tools:

Chrome DevTools

Console.log

Debugger statement

Breakpoints

Source maps

49. What are workers in JavaScript used for?
(Advanced)

Explanation: Workers run scripts in background threads to avoid blocking the main thread.

Example:

Web Workers

Service Workers

50. How does JavaScript garbage collection work?
(Advanced)

Explanation: Automatic memory management — JS engine frees memory occupied by objects no longer reachable.

Use Case:

Avoid memory leaks by managing object references properly.
