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
