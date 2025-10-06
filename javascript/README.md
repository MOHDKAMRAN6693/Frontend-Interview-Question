# JavaScript Interview Questions - 75+ Comprehensive List

## 🎯 Difficulty Levels
- **🟢 Beginner**: Basic JavaScript concepts and syntax (Questions 1-25)
- **🟡 Intermediate**: Functions, objects, and DOM manipulation (Questions 26-50)
- **🔴 Advanced**: Async programming, closures, and modern ES6+ features (Questions 51-70)
- **🟣 Expert**: Performance optimization, design patterns, and advanced concepts (Questions 71-85)

---

## 🟢 BEGINNER LEVEL (Questions 1-25)

### 1. What is JavaScript and what are its key features?
**Answer:**
JavaScript is a high-level, interpreted programming language primarily used for web development. Key features:
- Dynamic typing
- Prototype-based inheritance
- First-class functions
- Event-driven programming
- Asynchronous operations

### 2. What are the different data types in JavaScript?
**Answer:**
**Primitive types:** number, string, boolean, undefined, null, symbol, bigint
**Reference types:** object, array, function

### 3. What is the difference between var, let, and const?
**Answer:**
- `var`: Function-scoped, hoisted, can be redeclared
- `let`: Block-scoped, hoisted but not initialized, cannot be redeclared
- `const`: Block-scoped, must be initialized, cannot be reassigned

### 4. What is hoisting in JavaScript?
**Answer:**
Hoisting is JavaScript's behavior of moving variable and function declarations to the top of their scope during compilation.

### 5. What is the difference between null and undefined?
**Answer:**
- `undefined`: Variable declared but not assigned a value
- `null`: Intentional absence of any object value

### 6. What are JavaScript functions and how do you create them?
**Answer:**
Functions are reusable blocks of code. Created via:
- Function declarations
- Function expressions
- Arrow functions
- IIFE (Immediately Invoked Function Expressions)

### 7. What is the difference between == and ===?
**Answer:**
- `==`: Loose equality with type coercion
- `===`: Strict equality without type coercion

### 8. What are JavaScript objects and how do you work with them?
**Answer:**
Objects are collections of key-value pairs. Access via dot notation or bracket notation.

### 9. What are arrays and how do you manipulate them?
**Answer:**
Arrays are ordered collections. Manipulated using methods like push, pop, shift, unshift, slice, splice.

### 10. What is the 'this' keyword in JavaScript?
**Answer:**
`this` refers to the object that is executing the current function. Its value depends on how the function is called.

### 11. What is scope in JavaScript?
**Answer:**
Scope determines the accessibility of variables. Types: global, function, and block scope.

### 12. What are JavaScript operators?
**Answer:**
Arithmetic, assignment, comparison, logical, bitwise, and ternary operators.

### 13. What is type coercion in JavaScript?
**Answer:**
Automatic conversion of values from one type to another during operations.

### 14. What are JavaScript comments?
**Answer:**
Single-line (`//`) and multi-line (`/* */`) comments for code documentation.

### 15. What is the typeof operator?
**Answer:**
Returns a string indicating the type of the operand.

### 16. What are JavaScript loops?
**Answer:**
for, while, do-while, for-in, for-of loops for iteration.

### 17. What are conditional statements in JavaScript?
**Answer:**
if, else if, else, switch statements for conditional execution.

### 18. What is the difference between function declaration and function expression?
**Answer:**
Function declarations are hoisted, function expressions are not.

### 19. What are JavaScript strings and string methods?
**Answer:**
Strings are sequences of characters with methods like length, charAt, substring, indexOf, etc.

### 20. What are JavaScript numbers and number methods?
**Answer:**
Numbers can be integers or floats with methods like toFixed, toPrecision, parseInt, parseFloat.

### 21. What is the difference between primitive and reference types?
**Answer:**
Primitives are stored by value, references are stored by reference.

### 22. What is the difference between function parameters and arguments?
**Answer:**
Parameters are variables in function definition, arguments are actual values passed to function.

### 23. What is the return statement in JavaScript?
**Answer:**
Returns a value from a function and terminates function execution.

### 24. What are JavaScript events?
**Answer:**
Events are actions that occur in the browser, like clicks, keypresses, page loads.

### 25. What is the difference between alert, confirm, and prompt?
**Answer:**
- `alert()`: Shows a message
- `confirm()`: Shows a message with OK/Cancel buttons
- `prompt()`: Shows a message with input field

---

## 🟡 INTERMEDIATE LEVEL (Questions 26-50)

### 26. What are closures and how do they work?
**Answer:**
Closures allow inner functions to access variables from outer functions even after the outer function has returned.

### 27. What is the difference between call, apply, and bind?
**Answer:**
All three methods allow you to set the `this` context:
- `call()`: Invokes function with given `this` and arguments
- `apply()`: Similar to call but takes arguments as array
- `bind()`: Returns new function with bound `this`

### 28. What are JavaScript modules and how do you use them?
**Answer:**
Modules allow code organization with import/export syntax for splitting code into separate files.

### 29. What is the difference between forEach, map, filter, and reduce?
**Answer:**
- `forEach()`: Executes function for each array element
- `map()`: Creates new array with transformed elements
- `filter()`: Creates new array with elements that pass test
- `reduce()`: Reduces array to single value

### 30. What are JavaScript Promises and how do you handle them?
**Answer:**
Promises represent eventual completion of asynchronous operations. Handled with `.then()`, `.catch()`, `.finally()`.

### 31. What is async/await in JavaScript?
**Answer:**
Modern syntax for handling asynchronous operations, making code look synchronous.

### 32. What is the difference between let and const in loops?
**Answer:**
`let` creates new binding for each iteration, `const` creates constant binding.

### 33. What are JavaScript classes and how do you use them?
**Answer:**
Classes are templates for creating objects with constructor, methods, and inheritance.

### 34. What is the difference between function and arrow function?
**Answer:**
Arrow functions don't have their own `this`, `arguments`, and cannot be used as constructors.

### 35. What are JavaScript destructuring assignments?
**Answer:**
Syntax for extracting values from arrays or properties from objects into distinct variables.

### 36. What is the spread operator in JavaScript?
**Answer:**
`...` operator allows expansion of arrays or objects in places where multiple elements are expected.

### 37. What are JavaScript template literals?
**Answer:**
String literals allowing embedded expressions using backticks and `${}` syntax.

### 38. What is the difference between shallow and deep copy?
**Answer:**
Shallow copy copies only first level, deep copy copies all nested levels.

### 39. What are JavaScript getters and setters?
**Answer:**
Special methods that provide access to object properties with custom logic.

### 40. What is the difference between Object.freeze() and Object.seal()?
**Answer:**
- `Object.freeze()`: Makes object immutable
- `Object.seal()`: Prevents adding/removing properties but allows modification

### 41. What are JavaScript iterators and iterables?
**Answer:**
Iterators are objects that define a sequence and return value on each call. Iterables are objects that can be iterated over.

### 42. What is the difference between for-in and for-of loops?
**Answer:**
- `for-in`: Iterates over object keys
- `for-of`: Iterates over iterable values

### 43. What are JavaScript symbols and how do you use them?
**Answer:**
Symbols are unique identifiers used as object property keys to avoid naming conflicts.

### 44. What is the difference between Object.keys(), Object.values(), and Object.entries()?
**Answer:**
- `Object.keys()`: Returns array of object keys
- `Object.values()`: Returns array of object values
- `Object.entries()`: Returns array of key-value pairs

### 45. What are JavaScript regular expressions?
**Answer:**
Patterns used to match character combinations in strings, created with `/pattern/flags` or `new RegExp()`.

### 46. What is the difference between setTimeout and setInterval?
**Answer:**
- `setTimeout()`: Executes function once after delay
- `setInterval()`: Executes function repeatedly at intervals

### 47. What are JavaScript error handling mechanisms?
**Answer:**
try-catch-finally blocks for handling errors and exceptions.

### 48. What is the difference between local and global variables?
**Answer:**
Local variables are accessible within their scope, global variables are accessible throughout the program.

### 49. What are JavaScript event listeners?
**Answer:**
Functions that respond to specific events on DOM elements using `addEventListener()`.

### 50. What is the difference between innerHTML and textContent?
**Answer:**
- `innerHTML`: Gets/sets HTML content including tags
- `textContent`: Gets/sets text content without HTML tags

---

## 🔴 ADVANCED LEVEL (Questions 51-70)

### 51. What are JavaScript design patterns and how do you implement them?
**Answer:**
Reusable solutions to common problems. Examples: Singleton, Factory, Observer, Module patterns.

### 52. How do you optimize JavaScript performance?
**Answer:**
Techniques include debouncing, throttling, memoization, lazy loading, virtual scrolling, and code splitting.

### 53. What are JavaScript Proxies and how do you use them?
**Answer:**
Proxies allow interception and customization of operations on objects (get, set, has, deleteProperty).

### 54. What is the difference between microtasks and macrotasks?
**Answer:**
Microtasks (Promises, queueMicrotask) have higher priority than macrotasks (setTimeout, setInterval).

### 55. What are JavaScript Generators and how do you use them?
**Answer:**
Functions that can be paused and resumed using `yield` keyword, useful for creating iterators.

### 56. What is the difference between WeakMap and WeakSet?
**Answer:**
WeakMap and WeakSet hold weak references to objects, allowing garbage collection when objects are no longer referenced.

### 57. What are JavaScript decorators and how do you use them?
**Answer:**
Functions that modify or enhance other functions or classes using `@decorator` syntax.

### 58. What is the difference between static and instance methods?
**Answer:**
Static methods belong to the class, instance methods belong to instances of the class.

### 59. What are JavaScript mixins and how do you implement them?
**Answer:**
Pattern for adding functionality to classes by combining multiple objects.

### 60. What is the difference between composition and inheritance?
**Answer:**
Inheritance creates "is-a" relationships, composition creates "has-a" relationships.

### 61. What are JavaScript currying and partial application?
**Answer:**
Currying transforms functions with multiple arguments into functions with single arguments. Partial application fixes some arguments.

### 62. What is the difference between imperative and declarative programming?
**Answer:**
Imperative focuses on how to do something, declarative focuses on what to do.

### 63. What are JavaScript higher-order functions?
**Answer:**
Functions that take other functions as arguments or return functions.

### 64. What is the difference between synchronous and asynchronous JavaScript?
**Answer:**
Synchronous code executes sequentially, asynchronous code can execute out of order.

### 65. What are JavaScript event delegation and bubbling?
**Answer:**
Event delegation uses event bubbling to handle events on child elements through parent elements.

### 66. What is the difference between call stack and event loop?
**Answer:**
Call stack tracks function calls, event loop manages asynchronous operations and callback execution.

### 67. What are JavaScript memory leaks and how do you prevent them?
**Answer:**
Memory leaks occur when objects are no longer needed but still referenced. Prevent by proper cleanup and weak references.

### 68. What is the difference between shallow and deep equality?
**Answer:**
Shallow equality compares references, deep equality compares values recursively.

### 69. What are JavaScript functional programming concepts?
**Answer:**
Pure functions, immutability, higher-order functions, function composition, and avoiding side effects.

### 70. What is the difference between monads and functors in JavaScript?
**Answer:**
Functors are objects that can be mapped over, monads are functors with additional methods for chaining operations.

---

## 🟣 EXPERT LEVEL (Questions 71-85)

### 71. How do you implement advanced JavaScript testing and debugging?
**Answer:**
Comprehensive testing with frameworks, mocking, stubbing, assertion libraries, performance testing, and memory monitoring.

### 72. What are JavaScript metaprogramming techniques?
**Answer:**
Techniques for writing programs that manipulate other programs, including reflection, introspection, and code generation.

### 73. How do you implement advanced JavaScript concurrency patterns?
**Answer:**
Web Workers, SharedArrayBuffer, Atomics, and advanced async patterns for concurrent programming.

### 74. What are JavaScript memory management techniques?
**Answer:**
Garbage collection, memory profiling, weak references, and advanced memory optimization strategies.

### 75. How do you implement advanced JavaScript security measures?
**Answer:**
Content Security Policy, XSS prevention, CSRF protection, and secure coding practices.

### 76. What are JavaScript performance profiling techniques?
**Answer:**
Chrome DevTools profiling, memory snapshots, performance monitoring, and optimization strategies.

### 77. How do you implement advanced JavaScript build tools and bundling?
**Answer:**
Webpack, Rollup, Vite, tree shaking, code splitting, and advanced bundling strategies.

### 78. What are JavaScript advanced debugging techniques?
**Answer:**
Source maps, breakpoints, conditional breakpoints, watch expressions, and advanced debugging tools.

### 79. How do you implement advanced JavaScript architecture patterns?
**Answer:**
Micro-frontends, monorepos, component libraries, and advanced architectural patterns.

### 80. What are JavaScript advanced optimization techniques?
**Answer:**
Dead code elimination, tree shaking, minification, compression, and advanced optimization strategies.

### 81. How do you implement advanced JavaScript error handling?
**Answer:**
Global error handlers, error boundaries, custom error types, and advanced error recovery strategies.

### 82. What are JavaScript advanced testing strategies?
**Answer:**
Unit testing, integration testing, end-to-end testing, visual regression testing, and advanced testing patterns.

### 83. How do you implement advanced JavaScript data structures?
**Answer:**
Custom data structures, algorithms, and advanced data manipulation techniques.

### 84. What are JavaScript advanced async patterns?
**Answer:**
Advanced Promise patterns, async iterators, reactive programming, and complex async workflows.

### 85. How do you implement advanced JavaScript monitoring and observability?
**Answer:**
Application performance monitoring, error tracking, logging strategies, and advanced observability patterns.

---

## 🎯 Practice Exercises

### Beginner
1. Create a simple calculator with basic operations
2. Build a todo list application
3. Implement form validation
4. Create a simple game (tic-tac-toe)
5. Build a basic weather app

### Intermediate
1. Create a weather app with API integration
2. Build a photo gallery with lazy loading
3. Implement a search functionality with debouncing
4. Create a shopping cart application
5. Build a chat application

### Advanced
1. Build a real-time chat application
2. Create a data visualization dashboard
3. Implement a state management system
4. Build a PWA (Progressive Web App)
5. Create a micro-frontend architecture

### Expert
1. Design a micro-frontend architecture
2. Build a high-performance web application
3. Create a comprehensive testing suite
4. Implement advanced security measures
5. Build a scalable real-time system

---

## 📚 Additional Resources

- [MDN JavaScript Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [JavaScript.info](https://javascript.info/)
- [You Don't Know JS](https://github.com/getify/You-Dont-Know-JS)
- [JavaScript Design Patterns](https://www.dofactory.com/javascript/design-patterns)
- [Eloquent JavaScript](https://eloquentjavascript.net/)
- [JavaScript: The Good Parts](https://www.oreilly.com/library/view/javascript-the-good/9780596517748/)
- [Clean Code JavaScript](https://github.com/ryanmcdermott/clean-code-javascript)
- [JavaScript Algorithms and Data Structures](https://github.com/trekhleb/javascript-algorithms)

---

## 🎯 Interview Tips

1. **Practice coding on a whiteboard or paper**
2. **Explain your thought process out loud**
3. **Ask clarifying questions**
4. **Consider edge cases**
5. **Write clean, readable code**
6. **Test your solutions**
7. **Be prepared to optimize your code**
8. **Know the time and space complexity**
9. **Understand the trade-offs**
10. **Stay calm and think systematically**

---

*This comprehensive list covers 85+ JavaScript interview questions across all difficulty levels, providing a solid foundation for technical interviews.*