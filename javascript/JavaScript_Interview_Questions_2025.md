# JavaScript Interview Questions 2025 - 75+ Questions

## Table of Contents
1. [JavaScript Fundamentals](#javascript-fundamentals)
2. [ES6+ Features](#es6-features)
3. [Asynchronous JavaScript](#asynchronous-javascript)
4. [DOM Manipulation](#dom-manipulation)
5. [Closures and Scope](#closures-and-scope)
6. [Prototypes and Inheritance](#prototypes-and-inheritance)
7. [Event Handling](#event-handling)
8. [Error Handling](#error-handling)
9. [Performance and Optimization](#performance-and-optimization)
10. [Modern JavaScript Features](#modern-javascript-features)
11. [Browser APIs](#browser-apis)
12. [Testing and Debugging](#testing-and-debugging)

---

## JavaScript Fundamentals

### 1. What is JavaScript and what are its key characteristics?
JavaScript is a high-level, interpreted programming language that is primarily used for web development. Key characteristics include:
- Dynamic typing
- Prototype-based inheritance
- First-class functions
- Event-driven programming
- Cross-platform compatibility

### 2. What are the different data types in JavaScript?
JavaScript has 8 data types:
- **Primitive types**: `undefined`, `null`, `boolean`, `number`, `string`, `symbol`, `bigint`
- **Non-primitive type**: `object`

### 3. What is the difference between `var`, `let`, and `const`?
- **var**: Function-scoped, can be redeclared, hoisted
- **let**: Block-scoped, cannot be redeclared, hoisted but not initialized
- **const**: Block-scoped, cannot be redeclared or reassigned, must be initialized

### 4. What is hoisting in JavaScript?
Hoisting is JavaScript's behavior of moving declarations to the top of their scope before code execution. Only declarations are hoisted, not initializations.

### 5. What is the difference between `==` and `===`?
- `==` performs type coercion before comparison
- `===` performs strict comparison without type coercion

### 6. What is the `typeof` operator and what does it return?
The `typeof` operator returns a string indicating the type of the operand. It can return: "undefined", "boolean", "number", "string", "symbol", "bigint", "object", "function".

### 7. What is the difference between `null` and `undefined`?
- `undefined`: Variable declared but not assigned a value
- `null`: Intentional absence of any object value

### 8. What are truthy and falsy values in JavaScript?
**Falsy values**: `false`, `0`, `-0`, `0n`, `""`, `null`, `undefined`, `NaN`
**Truthy values**: Everything else

### 9. What is the difference between function declaration and function expression?
```javascript
// Function declaration (hoisted)
function myFunc() {}

// Function expression (not hoisted)
const myFunc = function() {};
```

### 10. What is the `this` keyword in JavaScript?
`this` refers to the object that is currently executing the function. Its value depends on how the function is called.

---

## ES6+ Features

### 11. What are arrow functions and how do they differ from regular functions?
Arrow functions are a concise way to write functions with lexical `this` binding, no `arguments` object, and cannot be used as constructors.

### 12. What are template literals?
Template literals use backticks and allow embedded expressions: `Hello ${name}!`

### 13. What is destructuring assignment?
Destructuring allows extracting values from arrays or properties from objects into distinct variables:
```javascript
const [a, b] = [1, 2];
const {name, age} = {name: 'John', age: 30};
```

### 14. What are default parameters?
Default parameters allow function parameters to have default values:
```javascript
function greet(name = 'World') {
  return `Hello ${name}!`;
}
```

### 15. What is the spread operator?
The spread operator (`...`) expands iterables into individual elements:
```javascript
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];
```

### 16. What is the rest parameter?
The rest parameter collects multiple elements into an array:
```javascript
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}
```

### 17. What are classes in JavaScript?
Classes are syntactic sugar over JavaScript's prototype-based inheritance:
```javascript
class Person {
  constructor(name) {
    this.name = name;
  }
}
```

### 18. What are modules in JavaScript?
Modules allow you to split code into separate files and import/export functionality:
```javascript
// math.js
export const add = (a, b) => a + b;

// main.js
import { add } from './math.js';
```

### 19. What is the `Map` object?
`Map` is a collection of key-value pairs where keys can be any type, unlike objects where keys must be strings.

### 20. What is the `Set` object?
`Set` is a collection of unique values, useful for removing duplicates and checking membership.

---

## Asynchronous JavaScript

### 21. What is the difference between synchronous and asynchronous code?
- **Synchronous**: Code executes line by line, blocking until each operation completes
- **Asynchronous**: Code can execute multiple operations concurrently without blocking

### 22. What are callbacks?
Callbacks are functions passed as arguments to other functions, executed at a later time:
```javascript
setTimeout(() => {
  console.log('This runs after 1 second');
}, 1000);
```

### 23. What is callback hell?
Callback hell occurs when multiple nested callbacks make code hard to read and maintain.

### 24. What are Promises?
Promises represent the eventual completion or failure of an asynchronous operation:
```javascript
const promise = new Promise((resolve, reject) => {
  // async operation
});
```

### 25. What are the three states of a Promise?
- **Pending**: Initial state, neither fulfilled nor rejected
- **Fulfilled**: Operation completed successfully
- **Rejected**: Operation failed

### 26. What is `async/await`?
`async/await` is syntactic sugar over Promises, making asynchronous code look synchronous:
```javascript
async function fetchData() {
  try {
    const response = await fetch('/api/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error:', error);
  }
}
```

### 27. What is the difference between `Promise.all()` and `Promise.allSettled()`?
- `Promise.all()`: Fails fast if any promise rejects
- `Promise.allSettled()`: Waits for all promises to settle (fulfill or reject)

### 28. What is `Promise.race()`?
`Promise.race()` returns a promise that resolves or rejects as soon as one of the promises in the iterable resolves or rejects.

### 29. What are generators?
Generators are functions that can be paused and resumed, yielding multiple values:
```javascript
function* generator() {
  yield 1;
  yield 2;
  yield 3;
}
```

### 30. What is the event loop?
The event loop is the mechanism that handles asynchronous operations in JavaScript, managing the call stack, callback queue, and microtask queue.

---

## DOM Manipulation

### 31. What is the DOM?
The Document Object Model (DOM) is a programming interface for HTML and XML documents, representing the structure as a tree of nodes.

### 32. How do you select elements in the DOM?
```javascript
// By ID
document.getElementById('myId');

// By class
document.getElementsByClassName('myClass');

// By tag
document.getElementsByTagName('div');

// Modern selectors
document.querySelector('#myId');
document.querySelectorAll('.myClass');
```

### 33. How do you create and append elements?
```javascript
const newElement = document.createElement('div');
newElement.textContent = 'Hello World';
document.body.appendChild(newElement);
```

### 34. What is the difference between `innerHTML` and `textContent`?
- `innerHTML`: Gets/sets HTML content (including tags)
- `textContent`: Gets/sets text content only (no HTML tags)

### 35. How do you add and remove CSS classes?
```javascript
element.classList.add('new-class');
element.classList.remove('old-class');
element.classList.toggle('toggle-class');
```

### 36. What is event delegation?
Event delegation is a technique where you attach a single event listener to a parent element to handle events for multiple child elements.

### 37. How do you prevent the default behavior of an event?
```javascript
element.addEventListener('click', (e) => {
  e.preventDefault();
});
```

### 38. What is the difference between `stopPropagation()` and `stopImmediatePropagation()`?
- `stopPropagation()`: Stops the event from bubbling up
- `stopImmediatePropagation()`: Stops the event and prevents other listeners on the same element from executing

---

## Closures and Scope

### 39. What is a closure?
A closure is a function that has access to variables in its outer (enclosing) scope even after the outer function returns.

### 40. What is lexical scoping?
Lexical scoping means that inner functions have access to variables in their outer scope based on where they are defined, not where they are called.

### 41. What is the scope chain?
The scope chain is the hierarchy of scopes that JavaScript uses to resolve variable names.

### 42. What is the difference between global and local scope?
- **Global scope**: Variables accessible from anywhere in the code
- **Local scope**: Variables accessible only within the function where they're declared

### 43. What is a block scope?
Block scope is the scope of variables declared with `let` and `const` within a block (curly braces).

### 44. What is the difference between function scope and block scope?
- **Function scope**: Variables declared with `var` are scoped to the entire function
- **Block scope**: Variables declared with `let`/`const` are scoped to the block

---

## Prototypes and Inheritance

### 45. What is a prototype?
A prototype is an object from which other objects inherit properties and methods.

### 46. What is prototype chaining?
Prototype chaining is the mechanism by which objects inherit properties and methods from their prototype chain.

### 47. What is the difference between `__proto__` and `prototype`?
- `__proto__`: Property that points to the object's prototype
- `prototype`: Property of constructor functions that becomes the prototype of instances

### 48. How do you create an object without a prototype?
```javascript
const obj = Object.create(null);
```

### 49. What is the difference between `Object.create()` and `new`?
- `Object.create()`: Creates an object with a specified prototype
- `new`: Creates an instance using a constructor function

### 50. What is the `instanceof` operator?
The `instanceof` operator tests whether an object has a specific prototype in its prototype chain.

---

## Event Handling

### 51. What are the different ways to attach event listeners?
```javascript
// HTML attribute
<button onclick="handleClick()">Click me</button>

// DOM property
element.onclick = handleClick;

// addEventListener (recommended)
element.addEventListener('click', handleClick);
```

### 52. What is event bubbling?
Event bubbling is the process where an event propagates from the target element up through its ancestors in the DOM tree.

### 53. What is event capturing?
Event capturing is the opposite of bubbling, where events are captured from the top of the DOM tree down to the target element.

### 54. What are the phases of event propagation?
1. **Capturing phase**: Event travels from root to target
2. **Target phase**: Event reaches the target element
3. **Bubbling phase**: Event bubbles up from target to root

---

## Error Handling

### 55. What is the `try-catch` statement?
`try-catch` allows you to handle errors gracefully:
```javascript
try {
  // risky code
} catch (error) {
  // handle error
}
```

### 56. What is the `finally` block?
The `finally` block executes regardless of whether an exception is thrown or caught.

### 57. What are the different types of errors in JavaScript?
- **SyntaxError**: Invalid syntax
- **ReferenceError**: Variable not declared
- **TypeError**: Wrong type of value
- **RangeError**: Value out of range

### 58. How do you create custom errors?
```javascript
class CustomError extends Error {
  constructor(message) {
    super(message);
    this.name = 'CustomError';
  }
}
```

---

## Performance and Optimization

### 59. What is debouncing?
Debouncing limits the rate at which a function can fire, useful for search inputs and scroll events.

### 60. What is throttling?
Throttling ensures a function is called at most once in a specified time period.

### 61. What is memoization?
Memoization is an optimization technique that caches the results of expensive function calls.

### 62. What are the different ways to optimize JavaScript performance?
- Use `requestAnimationFrame` for animations
- Implement virtual scrolling for large lists
- Use Web Workers for CPU-intensive tasks
- Minimize DOM manipulation
- Use efficient algorithms and data structures

### 63. What is the difference between `forEach` and `for` loops?
- `forEach`: Functional approach, cannot break or continue
- `for` loops: Imperative approach, can break or continue, generally faster

---

## Modern JavaScript Features

### 64. What are optional chaining (`?.`) and nullish coalescing (`??`)?
```javascript
// Optional chaining
const name = user?.profile?.name;

// Nullish coalescing
const value = user.name ?? 'Default';
```

### 65. What are private fields in classes?
Private fields are class properties that can only be accessed within the class:
```javascript
class MyClass {
  #privateField = 'secret';
}
```

### 66. What are static methods and properties?
Static methods and properties belong to the class itself, not instances:
```javascript
class MathUtils {
  static add(a, b) {
    return a + b;
  }
}
```

### 67. What are getters and setters?
Getters and setters allow you to define custom behavior for property access:
```javascript
class Person {
  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  }
}
```

---

## Browser APIs

### 68. What is the Fetch API?
The Fetch API provides a modern way to make HTTP requests:
```javascript
fetch('/api/data')
  .then(response => response.json())
  .then(data => console.log(data));
```

### 69. What is the difference between `localStorage` and `sessionStorage`?
- `localStorage`: Data persists until explicitly cleared
- `sessionStorage`: Data persists only for the session

### 70. What are Web Workers?
Web Workers allow you to run JavaScript in background threads, separate from the main thread.

### 71. What is the Intersection Observer API?
The Intersection Observer API provides a way to asynchronously observe changes in the intersection of a target element with an ancestor element.

### 72. What is the Geolocation API?
The Geolocation API allows web applications to access the user's geographical location.

---

## Testing and Debugging

### 73. What are the different ways to debug JavaScript?
- `console.log()`, `console.error()`, `console.warn()`
- Browser DevTools
- `debugger` statement
- Source maps

### 74. What is unit testing?
Unit testing is testing individual units of code in isolation to ensure they work correctly.

### 75. What are the benefits of using a testing framework like Jest?
- Test runner and assertion library
- Mocking capabilities
- Code coverage reports
- Snapshot testing
- Parallel test execution

### 76. What is the difference between `toBe()` and `toEqual()` in Jest?
- `toBe()`: Uses `Object.is()` for comparison (strict equality)
- `toEqual()`: Recursively checks all properties of object or array elements

### 77. What are mocks in testing?
Mocks are fake implementations of functions or modules used to isolate the code under test.

### 78. What is code coverage?
Code coverage measures the percentage of code that is executed during testing.

---

## Additional Advanced Questions

### 79. What is the difference between `call()`, `apply()`, and `bind()`?
- `call()`: Invokes function with specified `this` and individual arguments
- `apply()`: Invokes function with specified `this` and array of arguments
- `bind()`: Returns new function with specified `this` and arguments

### 80. What is currying?
Currying is the technique of converting a function that takes multiple arguments into a sequence of functions that each take a single argument.

### 81. What is the difference between `Object.freeze()` and `Object.seal()`?
- `Object.freeze()`: Makes object immutable (cannot add, modify, or delete properties)
- `Object.seal()`: Prevents adding/deleting properties but allows modification

### 82. What are WeakMap and WeakSet?
- `WeakMap`: Map with weak references to keys (garbage collectable)
- `WeakSet`: Set with weak references to values (garbage collectable)

### 83. What is the Temporal API?
The Temporal API is a modern date/time API that provides better alternatives to the Date object.

### 84. What are decorators in JavaScript?
Decorators are a proposal for adding metadata and modifying classes and methods at design time.

### 85. What is the difference between `import` and `require()`?
- `import`: ES6 module syntax, statically analyzed, tree-shakeable
- `require()`: CommonJS syntax, dynamically loaded, not tree-shakeable

---

## Conclusion

These 85+ JavaScript interview questions cover a comprehensive range of topics from basic concepts to advanced features. Practice explaining these concepts clearly and be prepared to write code examples during interviews. Good luck with your JavaScript interviews in 2025!
