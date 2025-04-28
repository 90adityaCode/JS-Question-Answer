# JavaScript Interview Questions

## Basic

### 1. Explain the concept of "hoisting" in JavaScript
- **Hoisting** is a JavaScript mechanism where variables and function declarations are moved to the top of their containing scope during the compile phase, before the code has been executed.
- Variables declared with `var` are hoisted and initialized with `undefined`, while functions are hoisted entirely, including their body.

### 2. What are the differences between JavaScript variables created using let, var, or const?
- **`var`**: 
  - Function-scoped, hoisted to the top of the scope with `undefined` initialization.
  - Can be redeclared in the same scope.
  
- **`let`**: 
  - Block-scoped (limited to the block where declared).
  - Hoisted but not initialized (temporal dead zone).
  - Cannot be redeclared in the same scope.
  
- **`const`**: 
  - Block-scoped, similar to `let`, but must be initialized at the time of declaration.
  - Cannot be reassigned (the value is immutable, but object properties can be modified).

### 3. What is the difference between == and === in JavaScript?
- **`==` (Loose Equality)**: 
  - Performs type coercion, meaning it compares values after converting them to a common type.
  - Example: `5 == '5'` is `true`.
  
- **`===` (Strict Equality)**:
  - Does not perform type coercion. Both the value and the type must be the same.
  - Example: `5 === '5'` is `false`.

### 4. What is the event loop in JavaScript runtimes?
- The **Event Loop** is the mechanism that allows JavaScript to perform non-blocking asynchronous operations, even though JavaScript is single-threaded.
- It continuously checks the **Call Stack** for functions to execute, and if the stack is empty, it checks the **Message Queue** for any pending events (callbacks, promises) that need to be processed.

### 5. Explain event delegation in JavaScript
- **Event delegation** is a technique where instead of attaching event listeners to each individual element, a single event listener is attached to a common ancestor. The event is propagated through the DOM and caught by the ancestor, which can then decide whether to handle the event.
- This improves performance, especially for dynamically added elements, and ensures events are handled consistently.

### 6. Explain how `this` works in JavaScript
- The keyword **`this`** refers to the context in which a function is called. It allows functions to access properties or methods on the object they're invoked on.
- **Global Context**: `this` refers to the global object (`window` in browsers).
- **Object Method**: `this` refers to the object the method is called on.
- **Arrow Functions**: Do not have their own `this`, instead inherit it from the surrounding lexical scope.
- **Event Handlers**: `this` refers to the element the event is triggered on.

---

## Additional Notes:
- Understanding these fundamental concepts is crucial for tackling **JavaScript** interviews. Each question reflects a deeper understanding of how JavaScript behaves and interacts with its environment.
