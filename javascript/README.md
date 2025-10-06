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

**Detailed Explanation:**
JavaScript was created by Brendan Eich in 1995 and has evolved from a simple scripting language to a powerful, versatile programming language. It's the only programming language that runs natively in web browsers and is now also used for server-side development (Node.js), mobile apps, desktop applications, and even IoT devices.

**Key Features with Examples:**

1. **Dynamic Typing:**
```javascript
let variable = 42;        // number
variable = "Hello";        // string
variable = true;           // boolean
variable = { name: "John" }; // object
```

2. **Prototype-based Inheritance:**
```javascript
function Person(name) {
    this.name = name;
}
Person.prototype.greet = function() {
    return `Hello, I'm ${this.name}`;
};

const john = new Person("John");
console.log(john.greet()); // "Hello, I'm John"
```

3. **First-class Functions:**
```javascript
// Functions can be assigned to variables
const add = function(a, b) { return a + b; };

// Functions can be passed as arguments
function calculate(operation, a, b) {
    return operation(a, b);
}

// Functions can be returned from other functions
function createMultiplier(factor) {
    return function(number) {
        return number * factor;
    };
}
```

4. **Event-driven Programming:**
```javascript
document.getElementById('button').addEventListener('click', function() {
    console.log('Button clicked!');
});
```

5. **Asynchronous Operations:**
```javascript
// Using Promises
fetch('https://api.example.com/data')
    .then(response => response.json())
    .then(data => console.log(data));

// Using async/await
async function fetchData() {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
}
```

### 2. What are the different data types in JavaScript?
**Answer:**
**Primitive types:** number, string, boolean, undefined, null, symbol, bigint
**Reference types:** object, array, function

**Detailed Explanation:**
JavaScript has two main categories of data types: primitive and reference types. Primitive types are immutable and stored by value, while reference types are mutable and stored by reference.

**Primitive Types with Examples:**

1. **Number:**
```javascript
let age = 25;           // integer
let price = 99.99;      // float
let infinity = Infinity;
let notANumber = NaN;
console.log(typeof age); // "number"
```

2. **String:**
```javascript
let name = "John";      // double quotes
let city = 'New York';  // single quotes
let template = `Hello ${name}`; // template literal
console.log(typeof name); // "string"
```

3. **Boolean:**
```javascript
let isActive = true;
let isComplete = false;
console.log(typeof isActive); // "boolean"
```

4. **Undefined:**
```javascript
let variable;           // declared but not assigned
console.log(variable);  // undefined
console.log(typeof variable); // "undefined"
```

5. **Null:**
```javascript
let data = null;        // intentional absence of value
console.log(typeof data); // "object" (this is a known quirk)
```

6. **Symbol (ES6):**
```javascript
let id = Symbol('id');
let id2 = Symbol('id');
console.log(id === id2); // false (symbols are unique)
console.log(typeof id); // "symbol"
```

7. **BigInt (ES2020):**
```javascript
let bigNumber = 123456789012345678901234567890n;
console.log(typeof bigNumber); // "bigint"
```

**Reference Types with Examples:**

1. **Object:**
```javascript
let person = {
    name: "John",
    age: 30,
    isActive: true
};
console.log(typeof person); // "object"
```

2. **Array:**
```javascript
let fruits = ["apple", "banana", "orange"];
console.log(typeof fruits); // "object"
console.log(Array.isArray(fruits)); // true
```

3. **Function:**
```javascript
function greet() {
    return "Hello!";
}
console.log(typeof greet); // "function"
```

**Type Checking Examples:**
```javascript
// Checking types
console.log(typeof 42);           // "number"
console.log(typeof "hello");      // "string"
console.log(typeof true);         // "boolean"
console.log(typeof undefined);    // "undefined"
console.log(typeof null);         // "object" (quirk!)
console.log(typeof {});           // "object"
console.log(typeof []);           // "object"
console.log(typeof function(){}); // "function"

// More precise checking
console.log(Array.isArray([]));   // true
console.log(Array.isArray({}));  // false
```

### 3. What is the difference between var, let, and const?
**Answer:**
- `var`: Function-scoped, hoisted, can be redeclared
- `let`: Block-scoped, hoisted but not initialized, cannot be redeclared
- `const`: Block-scoped, must be initialized, cannot be reassigned

**Detailed Explanation:**
The main differences between `var`, `let`, and `const` relate to scoping, hoisting behavior, and mutability. Understanding these differences is crucial for writing reliable JavaScript code.

**Scoping Examples:**

1. **var (Function-scoped):**
```javascript
function example() {
    if (true) {
        var x = 1;
    }
    console.log(x); // 1 (accessible outside the block)
}

// Global scope
var globalVar = "I'm global";
```

2. **let (Block-scoped):**
```javascript
function example() {
    if (true) {
        let y = 1;
        console.log(y); // 1 (accessible within the block)
    }
    // console.log(y); // ReferenceError: y is not defined
}

// Block scope with loops
for (let i = 0; i < 3; i++) {
    setTimeout(() => console.log(i), 100); // 0, 1, 2
}
```

3. **const (Block-scoped):**
```javascript
function example() {
    if (true) {
        const z = 1;
        // z = 2; // TypeError: Assignment to constant variable
    }
    // console.log(z); // ReferenceError: z is not defined
}
```

**Hoisting Examples:**

```javascript
// var hoisting
console.log(a); // undefined (not ReferenceError)
var a = 5;

// let/const hoisting (Temporal Dead Zone)
console.log(b); // ReferenceError: Cannot access 'b' before initialization
let b = 5;

console.log(c); // ReferenceError: Cannot access 'c' before initialization
const c = 5;
```

**Redeclaration Examples:**

```javascript
// var - can be redeclared
var name = "John";
var name = "Jane"; // No error

// let - cannot be redeclared
let age = 25;
// let age = 30; // SyntaxError: Identifier 'age' has already been declared

// const - cannot be redeclared
const city = "NYC";
// const city = "LA"; // SyntaxError: Identifier 'city' has already been declared
```

**Reassignment Examples:**

```javascript
// var - can be reassigned
var count = 0;
count = 1; // OK

// let - can be reassigned
let score = 100;
score = 200; // OK

// const - cannot be reassigned
const PI = 3.14159;
// PI = 3.14; // TypeError: Assignment to constant variable
```

**Object and Array Mutability with const:**

```javascript
// const prevents reassignment, not mutation
const person = { name: "John", age: 30 };
person.age = 31; // OK - object is mutated
person.city = "NYC"; // OK - property added
// person = { name: "Jane" }; // TypeError: Assignment to constant variable

const numbers = [1, 2, 3];
numbers.push(4); // OK - array is mutated
numbers[0] = 10; // OK - element changed
// numbers = [5, 6, 7]; // TypeError: Assignment to constant variable
```

**Best Practices:**
```javascript
// Use const by default
const API_URL = "https://api.example.com";
const users = [];

// Use let when you need to reassign
let currentUser = null;
let counter = 0;

// Avoid var in modern JavaScript
// var oldStyle = "don't use this";
```

### 4. What is hoisting in JavaScript?
**Answer:**
Hoisting is JavaScript's behavior of moving variable and function declarations to the top of their scope during compilation.

**Detailed Explanation:**
Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their containing scope during the compilation phase, before code execution. This means you can use variables and functions before they are declared in your code.

**Variable Hoisting Examples:**

```javascript
// var hoisting
console.log(x); // undefined (not ReferenceError)
var x = 5;
console.log(x); // 5

// What actually happens:
var x; // declaration is hoisted
console.log(x); // undefined
x = 5; // assignment stays in place
console.log(x); // 5
```

```javascript
// let and const hoisting (Temporal Dead Zone)
console.log(y); // ReferenceError: Cannot access 'y' before initialization
let y = 10;

console.log(z); // ReferenceError: Cannot access 'z' before initialization
const z = 15;
```

**Function Hoisting Examples:**

```javascript
// Function declarations are fully hoisted
console.log(sayHello()); // "Hello!" (works!)

function sayHello() {
    return "Hello!";
}

// Function expressions are NOT hoisted
console.log(sayGoodbye()); // TypeError: sayGoodbye is not a function
var sayGoodbye = function() {
    return "Goodbye!";
};
```

**Hoisting Order:**
```javascript
// 1. Function declarations (highest priority)
// 2. Variable declarations
// 3. Function expressions and assignments

var name = "John";
function name() {
    return "Jane";
}
console.log(typeof name); // "string" (variable assignment wins)
```

### 5. What is the difference between null and undefined?
**Answer:**
- `undefined`: Variable declared but not assigned a value
- `null`: Intentional absence of any object value

**Detailed Explanation:**
Both `null` and `undefined` represent the absence of a value, but they have different meanings and use cases in JavaScript.

**Undefined Examples:**

```javascript
// Variable declared but not assigned
let variable;
console.log(variable); // undefined

// Function parameter not provided
function greet(name) {
    console.log(name); // undefined if no argument passed
}
greet();

// Object property doesn't exist
let obj = {};
console.log(obj.nonExistent); // undefined

// Array element doesn't exist
let arr = [1, 2];
console.log(arr[5]); // undefined

// Function with no return statement
function noReturn() {
    // no return statement
}
console.log(noReturn()); // undefined
```

**Null Examples:**

```javascript
// Explicitly setting a variable to null
let data = null;
console.log(data); // null

// Function returning null to indicate no result
function findUser(id) {
    if (id === 1) {
        return { name: "John" };
    }
    return null; // explicitly no user found
}

// Clearing an object reference
let user = { name: "John" };
user = null; // explicitly clear the reference
```

**Comparison Examples:**

```javascript
// Type checking
console.log(typeof undefined); // "undefined"
console.log(typeof null);      // "object" (historical quirk)

// Equality comparisons
console.log(undefined == null);  // true (loose equality)
console.log(undefined === null); // false (strict equality)

// Checking for null/undefined
let value = null;
if (value === null) {
    console.log("Value is null");
}

let value2;
if (value2 === undefined) {
    console.log("Value is undefined");
}

// Modern nullish checking
let value3 = null;
console.log(value3 ?? "default"); // "default"

let value4 = undefined;
console.log(value4 ?? "default"); // "default"
```

### 6. What are JavaScript functions and how do you create them?
**Answer:**
Functions are reusable blocks of code. Created via:
- Function declarations
- Function expressions
- Arrow functions
- IIFE (Immediately Invoked Function Expressions)

**Detailed Explanation:**
Functions are first-class citizens in JavaScript, meaning they can be assigned to variables, passed as arguments, and returned from other functions.

**Function Declaration Examples:**

```javascript
// Basic function declaration
function greet(name) {
    return `Hello, ${name}!`;
}
console.log(greet("John")); // "Hello, John!"

// Function with multiple parameters
function add(a, b) {
    return a + b;
}
console.log(add(5, 3)); // 8

// Function with default parameters
function greetWithDefault(name = "World") {
    return `Hello, ${name}!`;
}
console.log(greetWithDefault()); // "Hello, World!"
console.log(greetWithDefault("Alice")); // "Hello, Alice!"
```

**Function Expression Examples:**

```javascript
// Basic function expression
const multiply = function(a, b) {
    return a * b;
};
console.log(multiply(4, 5)); // 20

// Named function expression
const factorial = function fact(n) {
    if (n <= 1) return 1;
    return n * fact(n - 1);
};
console.log(factorial(5)); // 120

// Function expression as callback
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(function(num) {
    return num * 2;
});
console.log(doubled); // [2, 4, 6, 8, 10]
```

**Arrow Function Examples:**

```javascript
// Basic arrow function
const square = (x) => x * x;
console.log(square(4)); // 16

// Arrow function with multiple parameters
const add = (a, b) => a + b;
console.log(add(3, 7)); // 10

// Arrow function with block body
const processArray = (arr) => {
    const result = [];
    for (let item of arr) {
        result.push(item * 2);
    }
    return result;
};
console.log(processArray([1, 2, 3])); // [2, 4, 6]

// Arrow function as callback
const numbers = [1, 2, 3, 4, 5];
const evens = numbers.filter(num => num % 2 === 0);
console.log(evens); // [2, 4]
```

**IIFE (Immediately Invoked Function Expression) Examples:**

```javascript
// Basic IIFE
(function() {
    console.log("This runs immediately!");
})();

// IIFE with parameters
(function(name) {
    console.log(`Hello, ${name}!`);
})("John");

// IIFE that returns a value
const result = (function(a, b) {
    return a + b;
})(5, 3);
console.log(result); // 8

// IIFE for creating private scope
const counter = (function() {
    let count = 0;
    return {
        increment: () => ++count,
        decrement: () => --count,
        getCount: () => count
    };
})();

console.log(counter.increment()); // 1
console.log(counter.increment()); // 2
console.log(counter.getCount()); // 2
```

**Function as First-Class Citizens:**

```javascript
// Function assigned to variable
const operation = function(a, b) {
    return a + b;
};

// Function passed as argument
function calculate(a, b, operation) {
    return operation(a, b);
}
console.log(calculate(5, 3, operation)); // 8

// Function returned from function
function createMultiplier(factor) {
    return function(number) {
        return number * factor;
    };
}
const double = createMultiplier(2);
console.log(double(5)); // 10
```

### 7. What is the difference between == and ===?
**Answer:**
- `==`: Loose equality with type coercion
- `===`: Strict equality without type coercion

**Detailed Explanation:**
The main difference is that `==` performs type coercion before comparison, while `===` does not. This makes `===` more predictable and generally preferred.

**Loose Equality (==) Examples:**

```javascript
// Type coercion examples
console.log(5 == "5");        // true (string "5" converted to number 5)
console.log(true == 1);       // true (boolean true converted to number 1)
console.log(false == 0);      // true (boolean false converted to number 0)
console.log(null == undefined); // true (special case)
console.log("" == 0);          // true (empty string converted to 0)
console.log(" " == 0);         // true (space string converted to 0)

// Tricky cases
console.log([] == 0);          // true (array converted to string, then to number)
console.log([1] == 1);         // true (array [1] converted to string "1", then to number 1)
console.log([1,2] == "1,2");   // true (array converted to string)
```

**Strict Equality (===) Examples:**

```javascript
// No type coercion
console.log(5 === "5");        // false (different types)
console.log(true === 1);       // false (different types)
console.log(false === 0);      // false (different types)
console.log(null === undefined); // false (different types)
console.log("" === 0);         // false (different types)

// Same type and value
console.log(5 === 5);          // true
console.log("hello" === "hello"); // true
console.log(true === true);    // true
console.log(null === null);    // true
console.log(undefined === undefined); // true
```

**Best Practices:**

```javascript
// Always use === unless you specifically need type coercion
if (value === null) {
    // Handle null case
}

if (value === undefined) {
    // Handle undefined case
}

// Check for both null and undefined
if (value == null) { // This is equivalent to value === null || value === undefined
    // Handle both null and undefined
}

// Modern nullish checking
if (value ?? false) {
    // Handle truthy values (excluding null and undefined)
}
```

### 8. What are JavaScript objects and how do you work with them?
**Answer:**
Objects are collections of key-value pairs. Access via dot notation or bracket notation.

**Detailed Explanation:**
Objects are one of the most important data structures in JavaScript. They allow you to group related data and functionality together.

**Object Creation Examples:**

```javascript
// Object literal
const person = {
    name: "John",
    age: 30,
    city: "New York"
};

// Using new Object()
const car = new Object();
car.brand = "Toyota";
car.model = "Camry";

// Using Object.create()
const animal = Object.create(null);
animal.type = "dog";
animal.name = "Buddy";
```

**Object Access Examples:**

```javascript
const person = {
    name: "John",
    age: 30,
    "favorite-color": "blue", // property with special characters
    address: {
        street: "123 Main St",
        city: "New York"
    }
};

// Dot notation
console.log(person.name); // "John"
console.log(person.age); // 30

// Bracket notation (required for special characters)
console.log(person["favorite-color"]); // "blue"
console.log(person["name"]); // "John" (also works for regular properties)

// Dynamic property access
const propertyName = "age";
console.log(person[propertyName]); // 30

// Nested object access
console.log(person.address.street); // "123 Main St"
console.log(person["address"]["city"]); // "New York"
```

**Object Methods Examples:**

```javascript
const calculator = {
    result: 0,
    
    add: function(num) {
        this.result += num;
        return this;
    },
    
    subtract: function(num) {
        this.result -= num;
        return this;
    },
    
    multiply: function(num) {
        this.result *= num;
        return this;
    },
    
    getResult: function() {
        return this.result;
    }
};

// Method chaining
const result = calculator
    .add(5)
    .multiply(3)
    .subtract(2)
    .getResult();
console.log(result); // 13
```

**Object Manipulation Examples:**

```javascript
const user = {
    name: "John",
    age: 30
};

// Adding properties
user.email = "john@example.com";
user["phone"] = "123-456-7890";

// Modifying properties
user.age = 31;

// Deleting properties
delete user.phone;

// Checking if property exists
console.log("name" in user); // true
console.log(user.hasOwnProperty("age")); // true
console.log(user.hasOwnProperty("toString")); // false (inherited property)

// Getting all keys, values, and entries
console.log(Object.keys(user)); // ["name", "age", "email"]
console.log(Object.values(user)); // ["John", 31, "john@example.com"]
console.log(Object.entries(user)); // [["name", "John"], ["age", 31], ["email", "john@example.com"]]
```

### 9. What are arrays and how do you manipulate them?
**Answer:**
Arrays are ordered collections. Manipulated using methods like push, pop, shift, unshift, slice, splice.

**Detailed Explanation:**
Arrays are ordered lists of values that can be of any type. They are zero-indexed and have many built-in methods for manipulation.

**Array Creation Examples:**

```javascript
// Array literal
const fruits = ["apple", "banana", "orange"];

// Using Array constructor
const numbers = new Array(1, 2, 3, 4, 5);

// Array with mixed types
const mixed = [1, "hello", true, { name: "John" }];

// Empty array
const empty = [];

// Array with specific length
const fixedLength = new Array(5); // [undefined, undefined, undefined, undefined, undefined]
```

**Array Access Examples:**

```javascript
const colors = ["red", "green", "blue"];

// Accessing elements
console.log(colors[0]); // "red"
console.log(colors[1]); // "green"
console.log(colors[2]); // "blue"
console.log(colors[3]); // undefined

// Modifying elements
colors[1] = "yellow";
console.log(colors); // ["red", "yellow", "blue"]

// Array length
console.log(colors.length); // 3
```

**Array Manipulation Methods:**

```javascript
const numbers = [1, 2, 3];

// Adding elements
numbers.push(4);        // Add to end: [1, 2, 3, 4]
numbers.unshift(0);     // Add to beginning: [0, 1, 2, 3, 4]

// Removing elements
const last = numbers.pop();     // Remove from end: [0, 1, 2, 3], last = 4
const first = numbers.shift(); // Remove from beginning: [1, 2, 3], first = 0

// Slicing (creates new array)
const slice1 = numbers.slice(1, 3); // [2, 3] (from index 1 to 2)
const slice2 = numbers.slice(1);    // [2, 3] (from index 1 to end)

// Splicing (modifies original array)
const removed = numbers.splice(1, 1, 10, 20); // Remove 1 element at index 1, add 10, 20
console.log(numbers); // [1, 10, 20, 3]
console.log(removed); // [2]
```

**Array Iteration Methods:**

```javascript
const numbers = [1, 2, 3, 4, 5];

// forEach - execute function for each element
numbers.forEach(num => console.log(num * 2));

// map - create new array with transformed elements
const doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

// filter - create new array with elements that pass test
const evens = numbers.filter(num => num % 2 === 0);
console.log(evens); // [2, 4]

// reduce - reduce array to single value
const sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum); // 15

// find - find first element that passes test
const found = numbers.find(num => num > 3);
console.log(found); // 4

// some - check if any element passes test
const hasEven = numbers.some(num => num % 2 === 0);
console.log(hasEven); // true

// every - check if all elements pass test
const allPositive = numbers.every(num => num > 0);
console.log(allPositive); // true
```

### 10. What is the 'this' keyword in JavaScript?
**Answer:**
`this` refers to the object that is executing the current function. Its value depends on how the function is called.

**Detailed Explanation:**
The `this` keyword is one of the most confusing aspects of JavaScript. Its value is determined by how a function is called, not where it's defined.

**Global Context:**

```javascript
console.log(this); // Window object (in browser) or global object (in Node.js)

function globalFunction() {
    console.log(this); // Window object (in browser)
}
globalFunction();
```

**Object Method Context:**

```javascript
const person = {
    name: "John",
    greet: function() {
        console.log(`Hello, I'm ${this.name}`);
    }
};

person.greet(); // "Hello, I'm John" (this refers to person object)
```

**Function Context (Strict vs Non-strict):**

```javascript
// Non-strict mode
function regularFunction() {
    console.log(this); // Window object (in browser)
}
regularFunction();

// Strict mode
"use strict";
function strictFunction() {
    console.log(this); // undefined
}
strictFunction();
```

**Arrow Functions vs Regular Functions:**

```javascript
const obj = {
    name: "John",
    
    regularMethod: function() {
        console.log(this.name); // "John"
        
        // Regular function inside method
        function innerFunction() {
            console.log(this.name); // undefined (this is Window in non-strict)
        }
        innerFunction();
        
        // Arrow function inside method
        const innerArrow = () => {
            console.log(this.name); // "John" (inherits this from outer scope)
        };
        innerArrow();
    },
    
    arrowMethod: () => {
        console.log(this.name); // undefined (arrow functions don't have their own this)
    }
};

obj.regularMethod();
obj.arrowMethod();
```

**Explicit Binding (call, apply, bind):**

```javascript
const person1 = { name: "John" };
const person2 = { name: "Jane" };

function greet(greeting) {
    console.log(`${greeting}, I'm ${this.name}`);
}

// call - invoke function with specific this and arguments
greet.call(person1, "Hello"); // "Hello, I'm John"
greet.call(person2, "Hi"); // "Hi, I'm Jane"

// apply - similar to call but arguments as array
greet.apply(person1, ["Hey"]); // "Hey, I'm John"

// bind - returns new function with bound this
const boundGreet = greet.bind(person1);
boundGreet("Welcome"); // "Welcome, I'm John"
```

**Constructor Context:**

```javascript
function Person(name) {
    this.name = name;
    this.greet = function() {
        console.log(`Hello, I'm ${this.name}`);
    };
}

const john = new Person("John");
john.greet(); // "Hello, I'm John"
```

**Event Handler Context:**

```javascript
const button = document.getElementById('myButton');

button.addEventListener('click', function() {
    console.log(this); // button element
});

// Arrow function in event handler
button.addEventListener('click', () => {
    console.log(this); // Window object (inherits from outer scope)
});
```

### 11. What is scope in JavaScript?
**Answer:**
Scope determines the accessibility of variables. Types: global, function, and block scope.

**Detailed Explanation:**
Scope defines where variables can be accessed in your code. JavaScript has lexical scoping, meaning the scope is determined by where variables are declared in the code.

**Global Scope Examples:**

```javascript
// Global variables
var globalVar = "I'm global";
let globalLet = "I'm also global";
const globalConst = "Me too";

function checkGlobal() {
    console.log(globalVar);  // "I'm global"
    console.log(globalLet);  // "I'm also global"
    console.log(globalConst); // "Me too"
}

// Variables declared without var, let, or const become global
function createGlobal() {
    accidentalGlobal = "I'm global too!";
}
createGlobal();
console.log(accidentalGlobal); // "I'm global too!"
```

**Function Scope Examples:**

```javascript
function outerFunction() {
    var functionScoped = "I'm in function scope";
    let alsoFunctionScoped = "Me too";
    
    function innerFunction() {
        console.log(functionScoped);  // "I'm in function scope"
        console.log(alsoFunctionScoped); // "Me too"
        
        var innerVar = "I'm in inner function";
        console.log(innerVar); // "I'm in inner function"
    }
    
    innerFunction();
    // console.log(innerVar); // ReferenceError: innerVar is not defined
}

outerFunction();
// console.log(functionScoped); // ReferenceError: functionScoped is not defined
```

**Block Scope Examples:**

```javascript
function blockScopeExample() {
    if (true) {
        var varInBlock = "I'm var in block";
        let letInBlock = "I'm let in block";
        const constInBlock = "I'm const in block";
        
        console.log(varInBlock);  // "I'm var in block"
        console.log(letInBlock);  // "I'm let in block"
        console.log(constInBlock); // "I'm const in block"
    }
    
    console.log(varInBlock);  // "I'm var in block" (var is function-scoped)
    // console.log(letInBlock);  // ReferenceError: letInBlock is not defined
    // console.log(constInBlock); // ReferenceError: constInBlock is not defined
}

blockScopeExample();
```

**Scope Chain Examples:**

```javascript
var globalVar = "global";

function outer() {
    var outerVar = "outer";
    
    function inner() {
        var innerVar = "inner";
        
        console.log(innerVar);  // "inner" (from current scope)
        console.log(outerVar);  // "outer" (from outer scope)
        console.log(globalVar); // "global" (from global scope)
    }
    
    inner();
}

outer();
```

### 12. What are JavaScript operators?
**Answer:**
Arithmetic, assignment, comparison, logical, bitwise, and ternary operators.

**Detailed Explanation:**
Operators are symbols that perform operations on operands. JavaScript has many types of operators for different purposes.

**Arithmetic Operators:**

```javascript
let a = 10, b = 3;

console.log(a + b);  // 13 (addition)
console.log(a - b);  // 7 (subtraction)
console.log(a * b);  // 30 (multiplication)
console.log(a / b);  // 3.333... (division)
console.log(a % b);  // 1 (modulus/remainder)
console.log(a ** b); // 1000 (exponentiation)

// Increment and decrement
let x = 5;
console.log(++x); // 6 (pre-increment)
console.log(x++); // 6 (post-increment, x becomes 7)
console.log(--x); // 6 (pre-decrement)
console.log(x--); // 6 (post-decrement, x becomes 5)
```

**Assignment Operators:**

```javascript
let x = 10;

x += 5;  // x = x + 5 (15)
x -= 3;  // x = x - 3 (12)
x *= 2;  // x = x * 2 (24)
x /= 4;  // x = x / 4 (6)
x %= 5;  // x = x % 5 (1)
x **= 3; // x = x ** 3 (1)

// Destructuring assignment
let [a, b, c] = [1, 2, 3];
let {name, age} = {name: "John", age: 30};
```

**Comparison Operators:**

```javascript
let a = 5, b = "5";

console.log(a == b);   // true (loose equality)
console.log(a === b);  // false (strict equality)
console.log(a != b);   // false (loose inequality)
console.log(a !== b);  // true (strict inequality)
console.log(a > 3);   // true (greater than)
console.log(a < 10);  // true (less than)
console.log(a >= 5);  // true (greater than or equal)
console.log(a <= 5);  // true (less than or equal)
```

**Logical Operators:**

```javascript
let x = true, y = false;

console.log(x && y);   // false (logical AND)
console.log(x || y);   // true (logical OR)
console.log(!x);       // false (logical NOT)

// Short-circuit evaluation
let result = x && "Hello"; // "Hello" (if x is truthy, return second operand)
let result2 = y || "Default"; // "Default" (if y is falsy, return second operand)

// Nullish coalescing
let value = null;
let defaultValue = value ?? "Default Value"; // "Default Value"
```

**Bitwise Operators:**

```javascript
let a = 5;  // 101 in binary
let b = 3;  // 011 in binary

console.log(a & b);   // 1 (bitwise AND)
console.log(a | b);   // 7 (bitwise OR)
console.log(a ^ b);   // 6 (bitwise XOR)
console.log(~a);      // -6 (bitwise NOT)
console.log(a << 1);  // 10 (left shift)
console.log(a >> 1);  // 2 (right shift)
console.log(a >>> 1); // 2 (unsigned right shift)
```

**Ternary Operator:**

```javascript
let age = 18;
let status = age >= 18 ? "adult" : "minor";
console.log(status); // "adult"

// Nested ternary (avoid in complex cases)
let score = 85;
let grade = score >= 90 ? "A" : 
            score >= 80 ? "B" : 
            score >= 70 ? "C" : "F";
console.log(grade); // "B"
```

### 13. What is type coercion in JavaScript?
**Answer:**
Automatic conversion of values from one type to another during operations.

**Detailed Explanation:**
Type coercion is JavaScript's automatic conversion of values from one type to another when performing operations. This can lead to unexpected results if not understood properly.

**Implicit Type Coercion Examples:**

```javascript
// String concatenation
console.log("5" + 3);        // "53" (number converted to string)
console.log(5 + "3");        // "53" (number converted to string)
console.log("5" + 3 + 2);    // "532" (left to right evaluation)
console.log(5 + 3 + "2");    // "82" (arithmetic first, then string)

// Arithmetic operations
console.log("5" - 3);         // 2 (string converted to number)
console.log("5" * 3);         // 15 (string converted to number)
console.log("5" / 3);         // 1.666... (string converted to number)

// Boolean conversion
console.log(!"hello");       // false (string is truthy, ! makes it false)
console.log(!!"hello");      // true (double negation)
console.log(!"0");           // false (non-empty string is truthy)
console.log(!!0);            // false (0 is falsy)
console.log(!!1);             // true (1 is truthy)
```

**Explicit Type Coercion Examples:**

```javascript
// String conversion
let num = 42;
console.log(String(num));    // "42"
console.log(num.toString());  // "42"
console.log(num + "");       // "42" (implicit)

// Number conversion
let str = "42";
console.log(Number(str));    // 42
console.log(parseInt(str));  // 42
console.log(parseFloat("42.5")); // 42.5
console.log(+str);           // 42 (unary plus)

// Boolean conversion
console.log(Boolean(1));     // true
console.log(Boolean(0));     // false
console.log(Boolean(""));    // false
console.log(Boolean("hello")); // true
console.log(Boolean(null));  // false
console.log(Boolean(undefined)); // false
```

**Tricky Coercion Examples:**

```javascript
// Array coercion
console.log([] + []);        // "" (empty arrays become empty strings)
console.log([] + {});        // "[object Object]"
console.log({} + []);        // "[object Object]"
console.log({} + {});        // "[object Object][object Object]"

// Object coercion
console.log({} == {});       // false (different objects)
console.log({} === {});     // false (different objects)
console.log([] == []);       // false (different arrays)
console.log([] == ![]);      // true (tricky!)

// Falsy values
console.log(Boolean(0));     // false
console.log(Boolean(""));    // false
console.log(Boolean(null));  // false
console.log(Boolean(undefined)); // false
console.log(Boolean(NaN));   // false
console.log(Boolean(false)); // false
```

### 14. What are JavaScript comments?
**Answer:**
Single-line (`//`) and multi-line (`/* */`) comments for code documentation.

**Detailed Explanation:**
Comments are used to document code, explain logic, and make code more readable. They are ignored by the JavaScript engine during execution.

**Single-line Comments:**

```javascript
// This is a single-line comment
let name = "John"; // This is an inline comment

// Comments can be used to disable code
// console.log("This won't execute");
console.log("This will execute");
```

**Multi-line Comments:**

```javascript
/*
This is a multi-line comment
It can span multiple lines
Useful for detailed explanations
*/

let user = {
    name: "John",
    age: 30
    /* 
    email: "john@example.com",
    phone: "123-456-7890"
    */
};
```

**JSDoc Comments (for documentation):**

```javascript
/**
 * Calculates the area of a rectangle
 * @param {number} width - The width of the rectangle
 * @param {number} height - The height of the rectangle
 * @returns {number} The area of the rectangle
 */
function calculateArea(width, height) {
    return width * height;
}

/**
 * Represents a person
 * @class
 */
class Person {
    /**
     * Creates an instance of Person
     * @param {string} name - The person's name
     * @param {number} age - The person's age
     */
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
}
```

**Comment Best Practices:**

```javascript
// Good: Explain why, not what
// Calculate tax for high-income earners
if (income > 100000) {
    tax = income * 0.3;
}

// Bad: Obvious comment
// Add 1 to counter
counter++;

// Good: Complex logic explanation
// Use bitwise AND to check if number is even
// (number & 1) === 0 means the last bit is 0, so number is even
const isEven = (number) => (number & 1) === 0;
```

### 15. What is the typeof operator?
**Answer:**
Returns a string indicating the type of the operand.

**Detailed Explanation:**
The `typeof` operator is used to determine the type of a value or variable. It returns a string representing the type.

**Basic typeof Examples:**

```javascript
console.log(typeof 42);           // "number"
console.log(typeof "hello");      // "string"
console.log(typeof true);          // "boolean"
console.log(typeof undefined);     // "undefined"
console.log(typeof null);          // "object" (historical quirk)
console.log(typeof {});            // "object"
console.log(typeof []);            // "object"
console.log(typeof function(){}); // "function"
console.log(typeof Symbol());      // "symbol"
console.log(typeof 123n);          // "bigint"
```

**typeof with Variables:**

```javascript
let name = "John";
let age = 30;
let isActive = true;
let data = null;
let user = { name: "John" };
let numbers = [1, 2, 3];
let greet = function() { return "Hello"; };

console.log(typeof name);    // "string"
console.log(typeof age);     // "number"
console.log(typeof isActive); // "boolean"
console.log(typeof data);    // "object" (null quirk)
console.log(typeof user);    // "object"
console.log(typeof numbers); // "object"
console.log(typeof greet);   // "function"
```

**typeof Edge Cases:**

```javascript
// Undeclared variables
console.log(typeof undeclaredVar); // "undefined" (no error thrown)

// Function declarations vs expressions
function declaredFunction() {}
const expressionFunction = function() {};
const arrowFunction = () => {};

console.log(typeof declaredFunction);  // "function"
console.log(typeof expressionFunction); // "function"
console.log(typeof arrowFunction);     // "function"

// Arrays and objects
console.log(typeof []);           // "object"
console.log(typeof {});           // "object"
console.log(Array.isArray([]));  // true (better way to check arrays)

// Classes
class MyClass {}
console.log(typeof MyClass);     // "function" (classes are functions)
```

**Practical typeof Usage:**

```javascript
function processValue(value) {
    if (typeof value === "string") {
        return value.toUpperCase();
    } else if (typeof value === "number") {
        return value * 2;
    } else if (typeof value === "boolean") {
        return !value;
    } else {
        return "Unknown type";
    }
}

console.log(processValue("hello")); // "HELLO"
console.log(processValue(5));       // 10
console.log(processValue(true));     // false
console.log(processValue(null));    // "Unknown type"
```

### 16. What are JavaScript loops?
**Answer:**
for, while, do-while, for-in, for-of loops for iteration.

**Detailed Explanation:**
Loops allow you to execute a block of code repeatedly. JavaScript provides several types of loops for different iteration scenarios.

**for Loop Examples:**

```javascript
// Basic for loop
for (let i = 0; i < 5; i++) {
    console.log(i); // 0, 1, 2, 3, 4
}

// for loop with array
const fruits = ["apple", "banana", "orange"];
for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i]); // "apple", "banana", "orange"
}

// Nested for loops
for (let i = 0; i < 3; i++) {
    for (let j = 0; j < 3; j++) {
        console.log(`i: ${i}, j: ${j}`);
    }
}
```

**while Loop Examples:**

```javascript
// Basic while loop
let count = 0;
while (count < 5) {
    console.log(count); // 0, 1, 2, 3, 4
    count++;
}

// while loop with condition
let number = 10;
while (number > 0) {
    console.log(number);
    number -= 2;
}
```

**do-while Loop Examples:**

```javascript
// do-while executes at least once
let x = 0;
do {
    console.log(x); // 0 (executes even though condition is false)
    x++;
} while (x < 0);

// Practical example
let userInput;
do {
    userInput = prompt("Enter a number between 1 and 10:");
} while (userInput < 1 || userInput > 10);
```

**for-in Loop Examples:**

```javascript
// Iterating over object properties
const person = {
    name: "John",
    age: 30,
    city: "New York"
};

for (let key in person) {
    console.log(`${key}: ${person[key]}`);
    // name: John
    // age: 30
    // city: New York
}

// for-in with arrays (not recommended)
const colors = ["red", "green", "blue"];
for (let index in colors) {
    console.log(`${index}: ${colors[index]}`);
    // 0: red
    // 1: green
    // 2: blue
}
```

**for-of Loop Examples:**

```javascript
// Iterating over array values
const numbers = [1, 2, 3, 4, 5];
for (let number of numbers) {
    console.log(number); // 1, 2, 3, 4, 5
}

// for-of with strings
const text = "Hello";
for (let char of text) {
    console.log(char); // H, e, l, l, o
}

// for-of with objects (using Object.entries)
const person = { name: "John", age: 30 };
for (let [key, value] of Object.entries(person)) {
    console.log(`${key}: ${value}`);
}
```

**Loop Control Statements:**

```javascript
// break - exit loop completely
for (let i = 0; i < 10; i++) {
    if (i === 5) {
        break; // Exit loop when i equals 5
    }
    console.log(i); // 0, 1, 2, 3, 4
}

// continue - skip current iteration
for (let i = 0; i < 10; i++) {
    if (i % 2 === 0) {
        continue; // Skip even numbers
    }
    console.log(i); // 1, 3, 5, 7, 9
}
```

### 17. What are conditional statements in JavaScript?
**Answer:**
if, else if, else, switch statements for conditional execution.

**Detailed Explanation:**
Conditional statements allow you to execute different code blocks based on different conditions.

**if-else Examples:**

```javascript
// Basic if statement
let age = 18;
if (age >= 18) {
    console.log("You are an adult");
}

// if-else statement
let temperature = 25;
if (temperature > 30) {
    console.log("It's hot");
} else {
    console.log("It's not hot");
}

// if-else if-else chain
let score = 85;
if (score >= 90) {
    console.log("Grade: A");
} else if (score >= 80) {
    console.log("Grade: B");
} else if (score >= 70) {
    console.log("Grade: C");
} else {
    console.log("Grade: F");
}
```

**Nested Conditionals:**

```javascript
let user = {
    age: 25,
    hasLicense: true,
    hasInsurance: false
};

if (user.age >= 18) {
    if (user.hasLicense) {
        if (user.hasInsurance) {
            console.log("You can drive");
        } else {
            console.log("You need insurance");
        }
    } else {
        console.log("You need a license");
    }
} else {
    console.log("You're too young to drive");
}
```

**Switch Statement Examples:**

```javascript
// Basic switch
let day = "Monday";
switch (day) {
    case "Monday":
        console.log("Start of work week");
        break;
    case "Friday":
        console.log("End of work week");
        break;
    case "Saturday":
    case "Sunday":
        console.log("Weekend");
        break;
    default:
        console.log("Regular day");
}

// Switch with fall-through
let month = 2;
switch (month) {
    case 1:
    case 3:
    case 5:
    case 7:
    case 8:
    case 10:
    case 12:
        console.log("31 days");
        break;
    case 4:
    case 6:
    case 9:
    case 11:
        console.log("30 days");
        break;
    case 2:
        console.log("28 or 29 days");
        break;
}
```

**Ternary Operator Examples:**

```javascript
// Basic ternary
let age = 20;
let status = age >= 18 ? "adult" : "minor";
console.log(status); // "adult"

// Nested ternary (use sparingly)
let score = 85;
let grade = score >= 90 ? "A" : 
            score >= 80 ? "B" : 
            score >= 70 ? "C" : "F";
console.log(grade); // "B"

// Ternary with function calls
let user = null;
let userName = user ? user.name : "Guest";
console.log(userName); // "Guest"
```

### 18. What is the difference between function declaration and function expression?
**Answer:**
Function declarations are hoisted, function expressions are not.

**Detailed Explanation:**
The main difference is in how they are hoisted and when they become available in the code.

**Function Declaration Examples:**

```javascript
// Function declaration - hoisted
console.log(sayHello()); // "Hello!" (works because of hoisting)

function sayHello() {
    return "Hello!";
}

// Function declarations are fully hoisted
function outer() {
    console.log(inner()); // "Inner function" (works)
    
    function inner() {
        return "Inner function";
    }
}
outer();
```

**Function Expression Examples:**

```javascript
// Function expression - not hoisted
// console.log(sayGoodbye()); // TypeError: sayGoodbye is not a function

var sayGoodbye = function() {
    return "Goodbye!";
};

console.log(sayGoodbye()); // "Goodbye!" (works after assignment)

// Named function expression
const factorial = function fact(n) {
    if (n <= 1) return 1;
    return n * fact(n - 1);
};
console.log(factorial(5)); // 120
```

**Hoisting Differences:**

```javascript
// Function declaration hoisting
console.log(declaredFunction()); // "I'm declared" (works)

function declaredFunction() {
    return "I'm declared";
}

// Function expression hoisting
console.log(expressionFunction); // undefined (not hoisted)
console.log(expressionFunction()); // TypeError: expressionFunction is not a function

var expressionFunction = function() {
    return "I'm expressed";
};
```

**Arrow Function Expressions:**

```javascript
// Arrow function expression - not hoisted
// console.log(arrowFunction()); // TypeError: arrowFunction is not a function

const arrowFunction = () => {
    return "I'm an arrow function";
};

console.log(arrowFunction()); // "I'm an arrow function"

// Arrow function with parameters
const add = (a, b) => a + b;
console.log(add(5, 3)); // 8
```

**Practical Differences:**

```javascript
// Function declaration can be called before definition
function processData() {
    return helper(); // Works because helper is hoisted
}

function helper() {
    return "data processed";
}

// Function expression cannot be called before assignment
function processData2() {
    // return helper2(); // ReferenceError: helper2 is not defined
}

const helper2 = function() {
    return "data processed";
};
```

### 19. What are JavaScript strings and string methods?
**Answer:**
Strings are sequences of characters with methods like length, charAt, substring, indexOf, etc.

**Detailed Explanation:**
Strings are immutable sequences of characters. JavaScript provides many methods for string manipulation.

**String Creation Examples:**

```javascript
// String literals
let str1 = "Hello World";
let str2 = 'Hello World';
let str3 = `Hello World`; // Template literal

// String constructor
let str4 = new String("Hello World");

// String concatenation
let firstName = "John";
let lastName = "Doe";
let fullName = firstName + " " + lastName; // "John Doe"
let templateName = `${firstName} ${lastName}`; // "John Doe"
```

**String Properties:**

```javascript
let text = "Hello World";
console.log(text.length); // 11 (number of characters)
```

**String Methods Examples:**

```javascript
let text = "Hello World";

// charAt() - get character at index
console.log(text.charAt(0)); // "H"
console.log(text.charAt(6)); // "W"

// charCodeAt() - get character code
console.log(text.charCodeAt(0)); // 72 (ASCII code for 'H')

// indexOf() - find index of substring
console.log(text.indexOf("World")); // 6
console.log(text.indexOf("o")); // 4 (first occurrence)
console.log(text.lastIndexOf("o")); // 7 (last occurrence)

// substring() - extract substring
console.log(text.substring(0, 5)); // "Hello"
console.log(text.substring(6)); // "World"

// slice() - extract substring (can use negative indices)
console.log(text.slice(0, 5)); // "Hello"
console.log(text.slice(-5)); // "World"
console.log(text.slice(6, 11)); // "World"

// toUpperCase() and toLowerCase()
console.log(text.toUpperCase()); // "HELLO WORLD"
console.log(text.toLowerCase()); // "hello world"

// replace() - replace substring
console.log(text.replace("World", "JavaScript")); // "Hello JavaScript"
console.log(text.replace(/o/g, "0")); // "Hell0 W0rld" (global replacement)

// split() - split string into array
console.log(text.split(" ")); // ["Hello", "World"]
console.log(text.split("")); // ["H", "e", "l", "l", "o", " ", "W", "o", "r", "l", "d"]

// trim() - remove whitespace
let spacedText = "  Hello World  ";
console.log(spacedText.trim()); // "Hello World"

// startsWith() and endsWith()
console.log(text.startsWith("Hello")); // true
console.log(text.endsWith("World")); // true

// includes() - check if string contains substring
console.log(text.includes("World")); // true
console.log(text.includes("JavaScript")); // false
```

**Template Literals (ES6):**

```javascript
let name = "John";
let age = 30;

// Basic template literal
let greeting = `Hello, my name is ${name} and I'm ${age} years old`;
console.log(greeting); // "Hello, my name is John and I'm 30 years old"

// Multi-line strings
let multiLine = `
This is a
multi-line
string
`;
console.log(multiLine);

// Expression evaluation
let a = 5, b = 10;
let calculation = `${a} + ${b} = ${a + b}`;
console.log(calculation); // "5 + 10 = 15"
```

### 20. What are JavaScript numbers and number methods?
**Answer:**
Numbers can be integers or floats with methods like toFixed, toPrecision, parseInt, parseFloat.

**Detailed Explanation:**
JavaScript has one number type that can represent both integers and floating-point numbers. Numbers are stored as 64-bit floating-point values.

**Number Creation Examples:**

```javascript
// Number literals
let integer = 42;
let float = 3.14159;
let scientific = 1.23e4; // 12300
let negative = -42;
let zero = 0;

// Number constructor
let num = new Number(42);
let num2 = Number("42"); // 42

// Special number values
let infinity = Infinity;
let negativeInfinity = -Infinity;
let notANumber = NaN;
```

**Number Properties:**

```javascript
console.log(Number.MAX_VALUE); // 1.7976931348623157e+308
console.log(Number.MIN_VALUE); // 5e-324
console.log(Number.MAX_SAFE_INTEGER); // 9007199254740991
console.log(Number.MIN_SAFE_INTEGER); // -9007199254740991
console.log(Number.POSITIVE_INFINITY); // Infinity
console.log(Number.NEGATIVE_INFINITY); // -Infinity
console.log(Number.NaN); // NaN
```

**Number Methods Examples:**

```javascript
let num = 123.456789;

// toFixed() - format with fixed decimal places
console.log(num.toFixed(2)); // "123.46"
console.log(num.toFixed(0)); // "123"

// toPrecision() - format with specified precision
console.log(num.toPrecision(4)); // "123.5"
console.log(num.toPrecision(2)); // "1.2e+2"

// toString() - convert to string
console.log(num.toString()); // "123.456789"
console.log(num.toString(2)); // "1111011.0111010010111100011010100111111011111001110111" (binary)
console.log(num.toString(16)); // "7b.74bc6a7ef9db" (hexadecimal)

// toExponential() - convert to exponential notation
console.log(num.toExponential(2)); // "1.23e+2"
```

**Number Parsing Examples:**

```javascript
// parseInt() - parse integer from string
console.log(parseInt("123")); // 123
console.log(parseInt("123.45")); // 123
console.log(parseInt("123abc")); // 123
console.log(parseInt("abc123")); // NaN
console.log(parseInt("1010", 2)); // 10 (binary to decimal)

// parseFloat() - parse float from string
console.log(parseFloat("123.45")); // 123.45
console.log(parseFloat("123.45abc")); // 123.45
console.log(parseFloat("abc123")); // NaN

// Number() - convert to number
console.log(Number("123")); // 123
console.log(Number("123.45")); // 123.45
console.log(Number("abc")); // NaN
console.log(Number(true)); // 1
console.log(Number(false)); // 0
```

**Number Validation Examples:**

```javascript
// isNaN() - check if value is NaN
console.log(isNaN(123)); // false
console.log(isNaN("123")); // false
console.log(isNaN("abc")); // true
console.log(isNaN(NaN)); // true

// isFinite() - check if value is finite
console.log(isFinite(123)); // true
console.log(isFinite(Infinity)); // false
console.log(isFinite(-Infinity)); // false
console.log(isFinite(NaN)); // false

// Number.isInteger() - check if value is integer
console.log(Number.isInteger(123)); // true
console.log(Number.isInteger(123.45)); // false
console.log(Number.isInteger("123")); // false
```

**Mathematical Operations:**

```javascript
let a = 10, b = 3;

// Basic arithmetic
console.log(a + b); // 13
console.log(a - b); // 7
console.log(a * b); // 30
console.log(a / b); // 3.3333333333333335
console.log(a % b); // 1
console.log(a ** b); // 1000

// Math object methods
console.log(Math.abs(-5)); // 5
console.log(Math.ceil(4.1)); // 5
console.log(Math.floor(4.9)); // 4
console.log(Math.round(4.5)); // 5
console.log(Math.max(1, 2, 3)); // 3
console.log(Math.min(1, 2, 3)); // 1
console.log(Math.random()); // Random number between 0 and 1
console.log(Math.sqrt(16)); // 4
console.log(Math.pow(2, 3)); // 8
```

### 21. What is the difference between primitive and reference types?
**Answer:**
Primitives are stored by value, references are stored by reference.

**Detailed Explanation:**
This is a fundamental concept in JavaScript that affects how data is copied and compared.

**Primitive Types (Stored by Value):**

```javascript
// Primitive types: number, string, boolean, undefined, null, symbol, bigint
let a = 5;
let b = a; // b gets a copy of the value
a = 10;
console.log(a); // 10
console.log(b); // 5 (unchanged)

let str1 = "Hello";
let str2 = str1; // str2 gets a copy of the value
str1 = "World";
console.log(str1); // "World"
console.log(str2); // "Hello" (unchanged)
```

**Reference Types (Stored by Reference):**

```javascript
// Reference types: object, array, function
let obj1 = { name: "John", age: 30 };
let obj2 = obj1; // obj2 gets a reference to the same object
obj1.name = "Jane";
console.log(obj1.name); // "Jane"
console.log(obj2.name); // "Jane" (changed because they reference the same object)

let arr1 = [1, 2, 3];
let arr2 = arr1; // arr2 gets a reference to the same array
arr1.push(4);
console.log(arr1); // [1, 2, 3, 4]
console.log(arr2); // [1, 2, 3, 4] (changed because they reference the same array)
```

**Comparison Examples:**

```javascript
// Primitive comparison (by value)
let a = 5;
let b = 5;
console.log(a === b); // true (same value)

let str1 = "Hello";
let str2 = "Hello";
console.log(str1 === str2); // true (same value)

// Reference comparison (by reference)
let obj1 = { name: "John" };
let obj2 = { name: "John" };
console.log(obj1 === obj2); // false (different objects)

let obj3 = obj1;
console.log(obj1 === obj3); // true (same reference)
```

**Copying Examples:**

```javascript
// Shallow copy of objects
let original = { name: "John", age: 30 };
let copy = { ...original }; // Shallow copy
copy.name = "Jane";
console.log(original.name); // "John" (unchanged)
console.log(copy.name); // "Jane"

// Deep copy needed for nested objects
let originalNested = { 
    name: "John", 
    address: { city: "NYC", country: "USA" } 
};
let shallowCopy = { ...originalNested };
shallowCopy.address.city = "LA";
console.log(originalNested.address.city); // "LA" (changed!)

// Deep copy using JSON (limited)
let deepCopy = JSON.parse(JSON.stringify(originalNested));
deepCopy.address.city = "Chicago";
console.log(originalNested.address.city); // "LA" (unchanged)
```

### 22. What is the difference between function parameters and arguments?
**Answer:**
Parameters are variables in function definition, arguments are actual values passed to function.

**Detailed Explanation:**
Parameters are the names listed in the function definition, while arguments are the actual values passed to the function when it's called.

**Basic Examples:**

```javascript
// Parameters: name, age (in function definition)
function greet(name, age) {
    return `Hello ${name}, you are ${age} years old`;
}

// Arguments: "John", 30 (actual values passed)
console.log(greet("John", 30)); // "Hello John, you are 30 years old"
console.log(greet("Jane", 25)); // "Hello Jane, you are 25 years old"
```

**Parameter vs Argument Examples:**

```javascript
// Function with parameters
function calculateArea(width, height) {
    return width * height;
}

// Calling with arguments
let area1 = calculateArea(10, 5); // Arguments: 10, 5
let area2 = calculateArea(20, 3); // Arguments: 20, 3

console.log(area1); // 50
console.log(area2); // 60
```

**Default Parameters:**

```javascript
// Parameters with default values
function greet(name = "Guest", greeting = "Hello") {
    return `${greeting}, ${name}!`;
}

// Calling without arguments (uses defaults)
console.log(greet()); // "Hello, Guest!"

// Calling with some arguments
console.log(greet("John")); // "Hello, John!"
console.log(greet("Jane", "Hi")); // "Hi, Jane!"
```

**Rest Parameters:**

```javascript
// Rest parameter (...args) collects remaining arguments
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3)); // 6
console.log(sum(1, 2, 3, 4, 5)); // 15
console.log(sum()); // 0
```

**Arguments Object:**

```javascript
// Traditional function has arguments object
function traditionalFunction() {
    console.log("Number of arguments:", arguments.length);
    console.log("Arguments:", Array.from(arguments));
}

traditionalFunction(1, 2, 3);
// Number of arguments: 3
// Arguments: [1, 2, 3]

// Arrow functions don't have arguments object
const arrowFunction = () => {
    // console.log(arguments); // ReferenceError: arguments is not defined
};
```

**Parameter Destructuring:**

```javascript
// Destructuring parameters
function displayUser({ name, age, city }) {
    return `${name} is ${age} years old and lives in ${city}`;
}

let user = { name: "John", age: 30, city: "NYC" };
console.log(displayUser(user)); // "John is 30 years old and lives in NYC"

// Array destructuring
function getFirstAndLast([first, ...rest]) {
    return { first, last: rest[rest.length - 1] };
}

let numbers = [1, 2, 3, 4, 5];
console.log(getFirstAndLast(numbers)); // { first: 1, last: 5 }
```

### 23. What is the return statement in JavaScript?
**Answer:**
Returns a value from a function and terminates function execution.

**Detailed Explanation:**
The `return` statement is used to exit a function and optionally return a value to the caller.

**Basic Return Examples:**

```javascript
// Function with return value
function add(a, b) {
    return a + b; // Returns the sum
}

let result = add(5, 3);
console.log(result); // 8

// Function without return (returns undefined)
function greet(name) {
    console.log(`Hello, ${name}!`);
    // No return statement
}

let greeting = greet("John"); // "Hello, John!"
console.log(greeting); // undefined
```

**Return vs No Return:**

```javascript
// Function with return
function getFullName(firstName, lastName) {
    return `${firstName} ${lastName}`;
}

let name = getFullName("John", "Doe");
console.log(name); // "John Doe"

// Function without return
function displayName(firstName, lastName) {
    console.log(`${firstName} ${lastName}`);
}

let display = displayName("Jane", "Smith"); // "Jane Smith"
console.log(display); // undefined
```

**Early Return Examples:**

```javascript
// Early return for validation
function divide(a, b) {
    if (b === 0) {
        return "Cannot divide by zero";
    }
    return a / b;
}

console.log(divide(10, 2)); // 5
console.log(divide(10, 0)); // "Cannot divide by zero"

// Early return in loops
function findFirstEven(numbers) {
    for (let num of numbers) {
        if (num % 2 === 0) {
            return num; // Returns first even number
        }
    }
    return null; // No even number found
}

console.log(findFirstEven([1, 3, 4, 5, 6])); // 4
console.log(findFirstEven([1, 3, 5, 7])); // null
```

**Multiple Return Points:**

```javascript
function getGrade(score) {
    if (score >= 90) {
        return "A";
    } else if (score >= 80) {
        return "B";
    } else if (score >= 70) {
        return "C";
    } else if (score >= 60) {
        return "D";
    } else {
        return "F";
    }
}

console.log(getGrade(95)); // "A"
console.log(getGrade(75)); // "C"
console.log(getGrade(45)); // "F"
```

**Returning Objects and Arrays:**

```javascript
// Returning an object
function createPerson(name, age) {
    return {
        name: name,
        age: age,
        greet: function() {
            return `Hello, I'm ${this.name}`;
        }
    };
}

let person = createPerson("John", 30);
console.log(person.greet()); // "Hello, I'm John"

// Returning an array
function getEvenNumbers(numbers) {
    return numbers.filter(num => num % 2 === 0);
}

let evens = getEvenNumbers([1, 2, 3, 4, 5, 6]);
console.log(evens); // [2, 4, 6]
```

### 24. What are JavaScript events?
**Answer:**
Events are actions that occur in the browser, like clicks, keypresses, page loads.

**Detailed Explanation:**
Events are user interactions or browser actions that can be detected and handled by JavaScript code.

**Common Event Types:**

```javascript
// Mouse events
button.addEventListener('click', function() {
    console.log('Button clicked!');
});

button.addEventListener('mouseover', function() {
    console.log('Mouse over button');
});

button.addEventListener('mouseout', function() {
    console.log('Mouse left button');
});

// Keyboard events
document.addEventListener('keydown', function(event) {
    console.log('Key pressed:', event.key);
});

document.addEventListener('keyup', function(event) {
    console.log('Key released:', event.key);
});

// Form events
form.addEventListener('submit', function(event) {
    event.preventDefault(); // Prevent form submission
    console.log('Form submitted');
});

input.addEventListener('change', function() {
    console.log('Input value changed:', this.value);
});

// Window events
window.addEventListener('load', function() {
    console.log('Page loaded');
});

window.addEventListener('resize', function() {
    console.log('Window resized');
});

window.addEventListener('scroll', function() {
    console.log('Page scrolled');
});
```

**Event Object Examples:**

```javascript
// Accessing event object
button.addEventListener('click', function(event) {
    console.log('Event type:', event.type);
    console.log('Target element:', event.target);
    console.log('Mouse position:', event.clientX, event.clientY);
    console.log('Timestamp:', event.timeStamp);
});

// Preventing default behavior
link.addEventListener('click', function(event) {
    event.preventDefault(); // Prevent link navigation
    console.log('Link clicked but navigation prevented');
});

// Stopping event propagation
innerDiv.addEventListener('click', function(event) {
    event.stopPropagation(); // Prevent event from bubbling up
    console.log('Inner div clicked');
});

outerDiv.addEventListener('click', function() {
    console.log('Outer div clicked');
});
```

**Event Delegation Examples:**

```javascript
// Event delegation - handle events on dynamically added elements
document.addEventListener('click', function(event) {
    if (event.target.classList.contains('delete-btn')) {
        console.log('Delete button clicked');
        event.target.parentElement.remove();
    }
});

// Adding new elements dynamically
function addNewButton() {
    const button = document.createElement('button');
    button.textContent = 'Delete';
    button.className = 'delete-btn';
    document.body.appendChild(button);
}
```

**Custom Events:**

```javascript
// Creating custom events
const customEvent = new CustomEvent('myCustomEvent', {
    detail: { message: 'Hello from custom event' }
});

// Dispatching custom events
button.addEventListener('click', function() {
    document.dispatchEvent(customEvent);
});

// Listening for custom events
document.addEventListener('myCustomEvent', function(event) {
    console.log('Custom event received:', event.detail.message);
});
```

### 25. What is the difference between alert, confirm, and prompt?
**Answer:**
- `alert()`: Shows a message
- `confirm()`: Shows a message with OK/Cancel buttons
- `prompt()`: Shows a message with input field

**Detailed Explanation:**
These are browser's built-in dialog methods for user interaction. They block the execution until the user responds.

**Alert Examples:**

```javascript
// Basic alert
alert("Hello World!");

// Alert with variables
let name = "John";
alert(`Hello, ${name}!`);

// Alert for debugging
let data = { name: "John", age: 30 };
alert("Debug info: " + JSON.stringify(data));

// Alert with line breaks
alert("Line 1\nLine 2\nLine 3");
```

**Confirm Examples:**

```javascript
// Basic confirm
let result = confirm("Are you sure you want to delete this item?");
if (result) {
    console.log("User clicked OK");
    // Proceed with deletion
} else {
    console.log("User clicked Cancel");
    // Cancel deletion
}

// Confirm in a function
function deleteItem() {
    if (confirm("Delete this item?")) {
        console.log("Item deleted");
        return true;
    } else {
        console.log("Deletion cancelled");
        return false;
    }
}

// Chaining confirms
if (confirm("Do you want to save changes?")) {
    if (confirm("Save to current file?")) {
        console.log("Saving...");
    } else {
        console.log("Save cancelled");
    }
} else {
    console.log("Changes not saved");
}
```

**Prompt Examples:**

```javascript
// Basic prompt
let name = prompt("What is your name?");
if (name) {
    console.log(`Hello, ${name}!`);
} else {
    console.log("No name provided");
}

// Prompt with default value
let age = prompt("What is your age?", "25");
console.log("Age entered:", age);

// Prompt with validation
function getValidAge() {
    let age;
    do {
        age = prompt("Enter your age (must be a number):");
        if (age === null) {
            return null; // User cancelled
        }
    } while (isNaN(age) || age < 0);
    return parseInt(age);
}

let userAge = getValidAge();
if (userAge !== null) {
    console.log(`You are ${userAge} years old`);
}
```

**Combined Examples:**

```javascript
// Multi-step user interaction
function userRegistration() {
    // Step 1: Get name
    let name = prompt("Enter your name:");
    if (!name) {
        alert("Registration cancelled");
        return;
    }
    
    // Step 2: Get age
    let age = prompt("Enter your age:");
    if (!age || isNaN(age)) {
        alert("Invalid age. Registration cancelled");
        return;
    }
    
    // Step 3: Confirm registration
    let confirmMessage = `Name: ${name}\nAge: ${age}\n\nIs this information correct?`;
    if (confirm(confirmMessage)) {
        alert("Registration successful!");
        return { name, age: parseInt(age) };
    } else {
        alert("Registration cancelled");
        return null;
    }
}

// Usage
let user = userRegistration();
if (user) {
    console.log("Registered user:", user);
}
```

**Modern Alternatives:**

```javascript
// Modern alternatives to alert, confirm, prompt
// Using custom modals or libraries like SweetAlert2

// Example with a simple custom confirm
function customConfirm(message) {
    return new Promise((resolve) => {
        const modal = document.createElement('div');
        modal.innerHTML = `
            <div style="position: fixed; top: 50%; left: 50%; transform: translate(-50%, -50%); 
                       background: white; padding: 20px; border: 1px solid #ccc; z-index: 1000;">
                <p>${message}</p>
                <button id="ok">OK</button>
                <button id="cancel">Cancel</button>
            </div>
        `;
        document.body.appendChild(modal);
        
        modal.querySelector('#ok').onclick = () => {
            document.body.removeChild(modal);
            resolve(true);
        };
        
        modal.querySelector('#cancel').onclick = () => {
            document.body.removeChild(modal);
            resolve(false);
        };
    });
}

// Usage
customConfirm("Are you sure?").then(result => {
    console.log("User choice:", result);
});
```

---

## 🟡 INTERMEDIATE LEVEL (Questions 26-50)

### 26. What are closures and how do they work?
**Answer:**
Closures allow inner functions to access variables from outer functions even after the outer function has returned.

**Detailed Explanation:**
A closure is a function that has access to variables in its outer (enclosing) scope even after the outer function has returned. This is one of JavaScript's most powerful features and is fundamental to understanding how JavaScript works.

**Basic Closure Examples:**

```javascript
// Simple closure
function outerFunction(x) {
    // Outer function's variable
    let outerVariable = x;
    
    // Inner function (closure)
    function innerFunction(y) {
        return outerVariable + y; // Access to outer variable
    }
    
    return innerFunction;
}

const closure = outerFunction(10);
console.log(closure(5)); // 15 (10 + 5)
console.log(closure(3)); // 13 (10 + 3)
```

**Closure with Multiple Variables:**

```javascript
function createCounter(initialValue = 0) {
    let count = initialValue;
    
    return {
        increment: function() {
            count++;
            return count;
        },
        decrement: function() {
            count--;
            return count;
        },
        getValue: function() {
            return count;
        }
    };
}

const counter = createCounter(5);
console.log(counter.increment()); // 6
console.log(counter.increment()); // 7
console.log(counter.decrement()); // 6
console.log(counter.getValue()); // 6
```

**Closure in Loops (Common Pitfall):**

```javascript
// Problem: All functions reference the same variable
function createFunctions() {
    let functions = [];
    for (var i = 0; i < 3; i++) {
        functions.push(function() {
            return i; // All return 3 (final value of i)
        });
    }
    return functions;
}

let funcs = createFunctions();
console.log(funcs[0]()); // 3
console.log(funcs[1]()); // 3
console.log(funcs[2]()); // 3

// Solution 1: Use let instead of var
function createFunctionsFixed1() {
    let functions = [];
    for (let i = 0; i < 3; i++) {
        functions.push(function() {
            return i; // Each has its own i
        });
    }
    return functions;
}

// Solution 2: Use IIFE (Immediately Invoked Function Expression)
function createFunctionsFixed2() {
    let functions = [];
    for (var i = 0; i < 3; i++) {
        functions.push((function(index) {
            return function() {
                return index;
            };
        })(i));
    }
    return functions;
}
```

**Practical Closure Examples:**

```javascript
// Module pattern using closure
const calculator = (function() {
    let result = 0;
    
    return {
        add: function(x) {
            result += x;
            return this;
        },
        subtract: function(x) {
            result -= x;
            return this;
        },
        multiply: function(x) {
            result *= x;
            return this;
        },
        getResult: function() {
            return result;
        },
        reset: function() {
            result = 0;
            return this;
        }
    };
})();

calculator.add(5).multiply(3).subtract(2);
console.log(calculator.getResult()); // 13
```

**Closure for Private Variables:**

```javascript
function createBankAccount(initialBalance) {
    let balance = initialBalance;
    
    return {
        deposit: function(amount) {
            if (amount > 0) {
                balance += amount;
                return `Deposited ${amount}. New balance: ${balance}`;
            }
            return "Invalid deposit amount";
        },
        withdraw: function(amount) {
            if (amount > 0 && amount <= balance) {
                balance -= amount;
                return `Withdrew ${amount}. New balance: ${balance}`;
            }
            return "Invalid withdrawal amount";
        },
        getBalance: function() {
            return balance;
        }
    };
}

const account = createBankAccount(100);
console.log(account.deposit(50)); // "Deposited 50. New balance: 150"
console.log(account.withdraw(30)); // "Withdrew 30. New balance: 120"
console.log(account.getBalance()); // 120
```

### 27. What is the difference between call, apply, and bind?
**Answer:**
All three methods allow you to set the `this` context:
- `call()`: Invokes function with given `this` and arguments
- `apply()`: Similar to call but takes arguments as array
- `bind()`: Returns new function with bound `this`

**Detailed Explanation:**
These methods are used to explicitly set the `this` value when calling functions. They're essential for borrowing methods and controlling function context.

**Call Method Examples:**

```javascript
// Basic call usage
function greet(greeting, punctuation) {
    return `${greeting} ${this.name}${punctuation}`;
}

const person = { name: "John" };
const result = greet.call(person, "Hello", "!");
console.log(result); // "Hello John!"

// Call with different contexts
const person1 = { name: "Alice" };
const person2 = { name: "Bob" };

console.log(greet.call(person1, "Hi", ".")); // "Hi Alice."
console.log(greet.call(person2, "Hey", "?")); // "Hey Bob?"
```

**Apply Method Examples:**

```javascript
// Basic apply usage
function introduce(greeting, age, city) {
    return `${greeting}, I'm ${this.name}, ${age} years old, from ${city}`;
}

const person = { name: "John" };
const args = ["Hello", 30, "NYC"];
const result = introduce.apply(person, args);
console.log(result); // "Hello, I'm John, 30 years old, from NYC"

// Apply with array methods
const numbers = [1, 2, 3, 4, 5];
const max = Math.max.apply(null, numbers);
console.log(max); // 5

const min = Math.min.apply(null, numbers);
console.log(min); // 1
```

**Bind Method Examples:**

```javascript
// Basic bind usage
function greet(greeting) {
    return `${greeting} ${this.name}`;
}

const person = { name: "John" };
const boundGreet = greet.bind(person);
console.log(boundGreet("Hello")); // "Hello John"

// Bind with partial arguments
const greetWithHello = greet.bind(person, "Hello");
console.log(greetWithHello()); // "Hello John"

// Bind for event handlers
const button = document.getElementById('myButton');
const handler = {
    name: "Button Handler",
    handleClick: function(event) {
        console.log(`${this.name} clicked!`);
    }
};

button.addEventListener('click', handler.handleClick.bind(handler));
```

**Practical Examples:**

```javascript
// Method borrowing
const arrayLike = {
    0: "a",
    1: "b",
    2: "c",
    length: 3
};

// Borrow Array.prototype.push
Array.prototype.push.call(arrayLike, "d");
console.log(arrayLike); // { 0: "a", 1: "b", 2: "c", 3: "d", length: 4 }

// Borrow Array.prototype.slice
const realArray = Array.prototype.slice.call(arrayLike);
console.log(realArray); // ["a", "b", "c", "d"]

// Function currying with bind
function multiply(a, b) {
    return a * b;
}

const double = multiply.bind(null, 2);
const triple = multiply.bind(null, 3);

console.log(double(5)); // 10
console.log(triple(4)); // 12
```

**Comparison Examples:**

```javascript
function calculate(a, b, c) {
    return `${this.operation}: ${a + b + c}`;
}

const calculator = { operation: "Addition" };

// Using call
const result1 = calculate.call(calculator, 1, 2, 3);
console.log(result1); // "Addition: 6"

// Using apply
const result2 = calculate.apply(calculator, [1, 2, 3]);
console.log(result2); // "Addition: 6"

// Using bind
const boundCalculate = calculate.bind(calculator);
const result3 = boundCalculate(1, 2, 3);
console.log(result3); // "Addition: 6"
```

### 28. What are JavaScript modules and how do you use them?
**Answer:**
Modules allow code organization with import/export syntax for splitting code into separate files.

**Detailed Explanation:**
Modules are a way to organize code into separate files that can be imported and exported. This helps with code organization, reusability, and avoiding global namespace pollution.

**Export Examples:**

```javascript
// math.js - Named exports
export const PI = 3.14159;
export const E = 2.71828;

export function add(a, b) {
    return a + b;
}

export function subtract(a, b) {
    return a - b;
}

export function multiply(a, b) {
    return a * b;
}

// Default export
export default function divide(a, b) {
    return a / b;
}

// Class export
export class Calculator {
    constructor() {
        this.result = 0;
    }
    
    calculate(operation, a, b) {
        switch(operation) {
            case 'add': return a + b;
            case 'subtract': return a - b;
            case 'multiply': return a * b;
            case 'divide': return a / b;
            default: return 0;
        }
    }
}
```

**Import Examples:**

```javascript
// main.js - Importing from math.js

// Named imports
import { add, subtract, multiply, PI } from './math.js';

console.log(add(5, 3)); // 8
console.log(subtract(10, 4)); // 6
console.log(multiply(2, 3)); // 6
console.log(PI); // 3.14159

// Default import
import divide from './math.js';
console.log(divide(10, 2)); // 5

// Import all as namespace
import * as MathUtils from './math.js';
console.log(MathUtils.add(1, 2)); // 3
console.log(MathUtils.PI); // 3.14159

// Import with alias
import { add as addition } from './math.js';
console.log(addition(1, 2)); // 3

// Import class
import { Calculator } from './math.js';
const calc = new Calculator();
console.log(calc.calculate('add', 5, 3)); // 8
```

**Module Patterns:**

```javascript
// user.js - User module
let users = [];
let currentUser = null;

export function addUser(user) {
    users.push(user);
}

export function getUsers() {
    return [...users]; // Return copy to prevent external modification
}

export function setCurrentUser(user) {
    currentUser = user;
}

export function getCurrentUser() {
    return currentUser;
}

export function removeUser(userId) {
    users = users.filter(user => user.id !== userId);
}

// Private function (not exported)
function validateUser(user) {
    return user && user.name && user.email;
}
```

**CommonJS vs ES6 Modules:**

```javascript
// CommonJS (Node.js style)
// math.js
const PI = 3.14159;
function add(a, b) {
    return a + b;
}
module.exports = { PI, add };

// main.js
const { PI, add } = require('./math.js');
console.log(add(2, 3)); // 5

// ES6 Modules (Browser/Modern Node.js)
// math.js
export const PI = 3.14159;
export function add(a, b) {
    return a + b;
}

// main.js
import { PI, add } from './math.js';
console.log(add(2, 3)); // 5
```

**Dynamic Imports:**

```javascript
// Dynamic import (async)
async function loadModule() {
    try {
        const mathModule = await import('./math.js');
        console.log(mathModule.add(2, 3)); // 5
    } catch (error) {
        console.error('Failed to load module:', error);
    }
}

// Conditional loading
if (userNeedsAdvancedFeatures) {
    const advancedModule = await import('./advanced.js');
    advancedModule.initialize();
}

// Lazy loading
const button = document.getElementById('loadFeature');
button.addEventListener('click', async () => {
    const feature = await import('./feature.js');
    feature.run();
});
```

### 29. What is the difference between forEach, map, filter, and reduce?
**Answer:**
- `forEach()`: Executes function for each array element
- `map()`: Creates new array with transformed elements
- `filter()`: Creates new array with elements that pass test
- `reduce()`: Reduces array to single value

**Detailed Explanation:**
These are the most commonly used array methods for iteration and transformation. Each serves a specific purpose and returns different results.

**forEach Examples:**

```javascript
const numbers = [1, 2, 3, 4, 5];

// Basic forEach
numbers.forEach(function(number) {
    console.log(number * 2);
});
// Output: 2, 4, 6, 8, 10

// forEach with index
numbers.forEach(function(number, index) {
    console.log(`Index ${index}: ${number}`);
});
// Output: Index 0: 1, Index 1: 2, etc.

// forEach with arrow function
numbers.forEach(num => console.log(num * num));
// Output: 1, 4, 9, 16, 25

// forEach doesn't return anything
const result = numbers.forEach(num => num * 2);
console.log(result); // undefined
```

**map Examples:**

```javascript
const numbers = [1, 2, 3, 4, 5];

// Basic map
const doubled = numbers.map(function(number) {
    return number * 2;
});
console.log(doubled); // [2, 4, 6, 8, 10]

// Map with arrow function
const squared = numbers.map(num => num * num);
console.log(squared); // [1, 4, 9, 16, 25]

// Map with objects
const users = [
    { name: "John", age: 30 },
    { name: "Jane", age: 25 },
    { name: "Bob", age: 35 }
];

const names = users.map(user => user.name);
console.log(names); // ["John", "Jane", "Bob"]

const ages = users.map(user => user.age);
console.log(ages); // [30, 25, 35]

// Map with index
const indexed = numbers.map((num, index) => `${index}: ${num}`);
console.log(indexed); // ["0: 1", "1: 2", "2: 3", "3: 4", "4: 5"]
```

**filter Examples:**

```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// Filter even numbers
const evens = numbers.filter(function(number) {
    return number % 2 === 0;
});
console.log(evens); // [2, 4, 6, 8, 10]

// Filter with arrow function
const odds = numbers.filter(num => num % 2 !== 0);
console.log(odds); // [1, 3, 5, 7, 9]

// Filter objects
const users = [
    { name: "John", age: 30, active: true },
    { name: "Jane", age: 25, active: false },
    { name: "Bob", age: 35, active: true }
];

const activeUsers = users.filter(user => user.active);
console.log(activeUsers); // [{ name: "John", age: 30, active: true }, { name: "Bob", age: 35, active: true }]

const adults = users.filter(user => user.age >= 30);
console.log(adults); // [{ name: "John", age: 30, active: true }, { name: "Bob", age: 35, active: true }]

// Filter with index
const firstHalf = numbers.filter((num, index) => index < 5);
console.log(firstHalf); // [1, 2, 3, 4, 5]
```

**reduce Examples:**

```javascript
const numbers = [1, 2, 3, 4, 5];

// Basic reduce
const sum = numbers.reduce(function(accumulator, currentValue) {
    return accumulator + currentValue;
}, 0);
console.log(sum); // 15

// Reduce with arrow function
const product = numbers.reduce((acc, curr) => acc * curr, 1);
console.log(product); // 120

// Reduce to find maximum
const max = numbers.reduce((acc, curr) => Math.max(acc, curr));
console.log(max); // 5

// Reduce to count occurrences
const words = ['apple', 'banana', 'apple', 'orange', 'banana', 'apple'];
const wordCount = words.reduce((acc, word) => {
    acc[word] = (acc[word] || 0) + 1;
    return acc;
}, {});
console.log(wordCount); // { apple: 3, banana: 2, orange: 1 }

// Reduce to group by property
const users = [
    { name: "John", department: "IT" },
    { name: "Jane", department: "HR" },
    { name: "Bob", department: "IT" }
];

const groupedByDept = users.reduce((acc, user) => {
    const dept = user.department;
    if (!acc[dept]) {
        acc[dept] = [];
    }
    acc[dept].push(user);
    return acc;
}, {});
console.log(groupedByDept);
// { IT: [{ name: "John", department: "IT" }, { name: "Bob", department: "IT" }], HR: [{ name: "Jane", department: "HR" }] }
```

**Chaining Methods:**

```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// Chain multiple methods
const result = numbers
    .filter(num => num % 2 === 0)  // [2, 4, 6, 8, 10]
    .map(num => num * num)          // [4, 16, 36, 64, 100]
    .reduce((acc, curr) => acc + curr, 0); // 220

console.log(result); // 220

// Complex chaining
const users = [
    { name: "John", age: 30, salary: 50000 },
    { name: "Jane", age: 25, salary: 60000 },
    { name: "Bob", age: 35, salary: 45000 },
    { name: "Alice", age: 28, salary: 70000 }
];

const highEarners = users
    .filter(user => user.salary > 50000)
    .map(user => ({ ...user, bonus: user.salary * 0.1 }))
    .sort((a, b) => b.salary - a.salary);

console.log(highEarners);
// [{ name: "Alice", age: 28, salary: 70000, bonus: 7000 }, { name: "Jane", age: 25, salary: 60000, bonus: 6000 }]
```

### 30. What are JavaScript Promises and how do you handle them?
**Answer:**
Promises represent eventual completion of asynchronous operations. Handled with `.then()`, `.catch()`, `.finally()`.

**Detailed Explanation:**
Promises are objects that represent the eventual completion or failure of an asynchronous operation. They provide a cleaner way to handle asynchronous code compared to callbacks.

**Basic Promise Examples:**

```javascript
// Creating a Promise
const myPromise = new Promise((resolve, reject) => {
    const success = true;
    
    if (success) {
        resolve("Operation completed successfully");
    } else {
        reject("Operation failed");
    }
});

// Using the Promise
myPromise
    .then(result => {
        console.log(result); // "Operation completed successfully"
    })
    .catch(error => {
        console.log(error); // "Operation failed"
    });
```

**Promise with setTimeout:**

```javascript
function delay(ms) {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve(`Completed after ${ms}ms`);
        }, ms);
    });
}

delay(1000)
    .then(result => {
        console.log(result); // "Completed after 1000ms"
    });

// Chaining promises
delay(500)
    .then(result => {
        console.log("First:", result);
        return delay(300);
    })
    .then(result => {
        console.log("Second:", result);
    });
```

**Promise Methods:**

```javascript
// Promise.resolve() - Creates resolved promise
const resolvedPromise = Promise.resolve("Immediate value");
resolvedPromise.then(value => console.log(value)); // "Immediate value"

// Promise.reject() - Creates rejected promise
const rejectedPromise = Promise.reject("Error occurred");
rejectedPromise.catch(error => console.log(error)); // "Error occurred"

// Promise.all() - Waits for all promises to resolve
const promise1 = delay(1000);
const promise2 = delay(2000);
const promise3 = delay(500);

Promise.all([promise1, promise2, promise3])
    .then(results => {
        console.log("All completed:", results);
    });

// Promise.race() - Returns first resolved/rejected promise
Promise.race([promise1, promise2, promise3])
    .then(result => {
        console.log("First to complete:", result);
    });
```

**Error Handling:**

```javascript
// Basic error handling
function fetchData(url) {
    return new Promise((resolve, reject) => {
        // Simulate API call
        setTimeout(() => {
            if (url.includes("error")) {
                reject(new Error("Failed to fetch data"));
            } else {
                resolve({ data: "Some data", url: url });
            }
        }, 1000);
    });
}

fetchData("https://api.example.com/data")
    .then(response => {
        console.log("Success:", response);
    })
    .catch(error => {
        console.log("Error:", error.message);
    })
    .finally(() => {
        console.log("Request completed");
    });

// Multiple catch blocks
fetchData("https://api.example.com/error")
    .then(response => {
        console.log("Success:", response);
        return processData(response);
    })
    .then(processedData => {
        console.log("Processed:", processedData);
    })
    .catch(error => {
        console.log("Error occurred:", error.message);
    });
```

**Async/Await (Modern Promise Handling):**

```javascript
// Using async/await
async function fetchUserData(userId) {
    try {
        const user = await fetchData(`/users/${userId}`);
        const posts = await fetchData(`/users/${userId}/posts`);
        return { user, posts };
    } catch (error) {
        console.log("Error fetching user data:", error.message);
        throw error;
    }
}

// Using the async function
fetchUserData(123)
    .then(data => {
        console.log("User data:", data);
    })
    .catch(error => {
        console.log("Failed to fetch user data");
    });

// Parallel async operations
async function fetchMultipleData() {
    try {
        const [users, posts, comments] = await Promise.all([
            fetchData("/users"),
            fetchData("/posts"),
            fetchData("/comments")
        ]);
        
        return { users, posts, comments };
    } catch (error) {
        console.log("Error fetching data:", error.message);
    }
}
```

**Real-world Promise Examples:**

```javascript
// Fetch API with Promises
function fetchUser(id) {
    return fetch(`https://jsonplaceholder.typicode.com/users/${id}`)
        .then(response => {
            if (!response.ok) {
                throw new Error(`HTTP error! status: ${response.status}`);
            }
            return response.json();
        });
}

fetchUser(1)
    .then(user => {
        console.log("User:", user);
    })
    .catch(error => {
        console.log("Error:", error.message);
    });

// File reading with Promises (Node.js)
const fs = require('fs').promises;

function readFileAsync(filename) {
    return fs.readFile(filename, 'utf8')
        .then(data => {
            console.log("File content:", data);
            return data;
        })
        .catch(error => {
            console.log("Error reading file:", error.message);
            throw error;
        });
}
```

### 31. What is async/await in JavaScript?
**Answer:**
Modern syntax for handling asynchronous operations, making code look synchronous.

**Detailed Explanation:**
`async/await` is a syntactic sugar built on top of Promises that makes asynchronous code easier to write and read. It allows you to write asynchronous code that looks and behaves like synchronous code, eliminating the need for callback chains and `.then()` methods.

**Key Concepts:**

1. **async function:**
```javascript
async function fetchData() {
    // This function always returns a Promise
    return "Hello World";
}

// Even though we return a string, it's wrapped in a Promise
fetchData().then(result => console.log(result)); // "Hello World"
```

2. **await keyword:**
```javascript
async function fetchUserData() {
    try {
        const response = await fetch('/api/user');
        const data = await response.json();
        return data;
    } catch (error) {
        console.error('Error fetching user data:', error);
    }
}
```

3. **Error handling with try-catch:**
```javascript
async function processData() {
    try {
        const result1 = await asyncOperation1();
        const result2 = await asyncOperation2(result1);
        return result2;
    } catch (error) {
        console.error('Error in processData:', error);
        throw error; // Re-throw if needed
    }
}
```

4. **Parallel execution with Promise.all:**
```javascript
async function fetchMultipleData() {
    try {
        const [users, posts, comments] = await Promise.all([
            fetch('/api/users').then(res => res.json()),
            fetch('/api/posts').then(res => res.json()),
            fetch('/api/comments').then(res => res.json())
        ]);
        
        return { users, posts, comments };
    } catch (error) {
        console.error('Error fetching data:', error);
    }
}
```

5. **Sequential vs Parallel execution:**
```javascript
// Sequential (slower)
async function sequential() {
    const user = await fetchUser();
    const posts = await fetchUserPosts(user.id);
    const comments = await fetchPostComments(posts[0].id);
    return { user, posts, comments };
}

// Parallel (faster)
async function parallel() {
    const user = await fetchUser();
    const [posts, comments] = await Promise.all([
        fetchUserPosts(user.id),
        fetchPostComments(user.id)
    ]);
    return { user, posts, comments };
}
```

**Benefits:**
- Cleaner, more readable code
- Better error handling with try-catch
- Easier debugging
- Natural flow control
- Works with any Promise-based API

**Common Patterns:**
```javascript
// Async function expression
const fetchData = async () => {
    const response = await fetch('/api/data');
    return response.json();
};

// Async method in class
class ApiService {
    async getData() {
        const response = await fetch('/api/data');
        return response.json();
    }
}

// Async IIFE (Immediately Invoked Function Expression)
(async () => {
    try {
        const data = await fetchData();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
})();
```

### 32. What is the difference between let and const in loops?
**Answer:**
`let` creates new binding for each iteration, `const` creates constant binding.

**Detailed Explanation:**
The difference between `let` and `const` in loops relates to how they handle variable binding and scope. Both create block-scoped variables, but they behave differently in terms of reassignment and iteration binding.

**Key Differences:**

1. **Variable Reassignment:**
```javascript
// Using let - can be reassigned
for (let i = 0; i < 3; i++) {
    i = i + 1; // This works
    console.log(i); // 1, 3, 5
}

// Using const - cannot be reassigned
for (const i = 0; i < 3; i++) {
    // i = i + 1; // Error: Assignment to constant variable
    console.log(i); // 0, 1, 2
}
```

2. **Loop Variable Binding:**
```javascript
// let creates new binding for each iteration
const functions = [];
for (let i = 0; i < 3; i++) {
    functions.push(() => console.log(i));
}
functions[0](); // 0
functions[1](); // 1
functions[2](); // 2

// const also creates new binding for each iteration
const functions2 = [];
for (const i of [0, 1, 2]) {
    functions2.push(() => console.log(i));
}
functions2[0](); // 0
functions2[1](); // 1
functions2[2](); // 2
```

3. **For-in and For-of loops:**
```javascript
const obj = { a: 1, b: 2, c: 3 };
const arr = [1, 2, 3];

// Using let in for-in loop
for (let key in obj) {
    console.log(key); // a, b, c
    // key = 'newKey'; // This works with let
}

// Using const in for-in loop
for (const key in obj) {
    console.log(key); // a, b, c
    // key = 'newKey'; // Error: Assignment to constant variable
}

// Using let in for-of loop
for (let value of arr) {
    console.log(value); // 1, 2, 3
    // value = 999; // This works with let
}

// Using const in for-of loop
for (const value of arr) {
    console.log(value); // 1, 2, 3
    // value = 999; // Error: Assignment to constant variable
}
```

4. **Practical Examples:**
```javascript
// Object iteration with const (recommended)
const user = { name: 'John', age: 30, city: 'New York' };
for (const [key, value] of Object.entries(user)) {
    console.log(`${key}: ${value}`);
    // key and value are const, cannot be reassigned
}

// Array iteration with const (recommended)
const numbers = [1, 2, 3, 4, 5];
for (const num of numbers) {
    console.log(num * 2);
    // num is const, cannot be reassigned
}

// Traditional for loop with let (when you need to modify the variable)
for (let i = 0; i < 5; i++) {
    if (i === 2) {
        i++; // Skip next iteration
        continue;
    }
    console.log(i); // 0, 1, 3, 4
}
```

5. **Closure and Scope:**
```javascript
// Both let and const create proper closures
const callbacks = [];

// Using let
for (let i = 0; i < 3; i++) {
    callbacks.push(() => console.log('let:', i));
}

// Using const in for-of
for (const i of [0, 1, 2]) {
    callbacks.push(() => console.log('const:', i));
}

callbacks.forEach(cb => cb());
// Output:
// let: 0
// let: 1
// let: 2
// const: 0
// const: 1
// const: 2
```

**Best Practices:**
- Use `const` when you don't need to reassign the variable
- Use `let` when you need to modify the variable during iteration
- Prefer `const` for for-of and for-in loops when possible
- Use `let` for traditional for loops where you need to modify the counter

### 33. What are JavaScript classes and how do you use them?
**Answer:**
Classes are templates for creating objects with constructor, methods, and inheritance.

**Detailed Explanation:**
JavaScript classes, introduced in ES6, provide a cleaner syntax for creating objects and implementing inheritance. They are syntactic sugar over JavaScript's existing prototype-based inheritance, making object-oriented programming more intuitive and similar to other programming languages.

**Basic Class Syntax:**

1. **Class Declaration:**
```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    
    greet() {
        return `Hello, I'm ${this.name} and I'm ${this.age} years old.`;
    }
    
    getInfo() {
        return {
            name: this.name,
            age: this.age
        };
    }
}

const john = new Person('John', 30);
console.log(john.greet()); // "Hello, I'm John and I'm 30 years old."
```

2. **Class Expression:**
```javascript
const Animal = class {
    constructor(name, species) {
        this.name = name;
        this.species = species;
    }
    
    makeSound() {
        return `${this.name} makes a sound`;
    }
};

const dog = new Animal('Buddy', 'Dog');
console.log(dog.makeSound()); // "Buddy makes a sound"
```

**Advanced Class Features:**

3. **Static Methods:**
```javascript
class MathUtils {
    static add(a, b) {
        return a + b;
    }
    
    static multiply(a, b) {
        return a * b;
    }
    
    static PI = 3.14159;
}

console.log(MathUtils.add(5, 3)); // 8
console.log(MathUtils.PI); // 3.14159
```

4. **Getters and Setters:**
```javascript
class Rectangle {
    constructor(width, height) {
        this._width = width;
        this._height = height;
    }
    
    get area() {
        return this._width * this._height;
    }
    
    get width() {
        return this._width;
    }
    
    set width(value) {
        if (value > 0) {
            this._width = value;
        } else {
            throw new Error('Width must be positive');
        }
    }
    
    get height() {
        return this._height;
    }
    
    set height(value) {
        if (value > 0) {
            this._height = value;
        } else {
            throw new Error('Height must be positive');
        }
    }
}

const rect = new Rectangle(5, 10);
console.log(rect.area); // 50
rect.width = 8;
console.log(rect.area); // 80
```

5. **Private Fields (ES2022):**
```javascript
class BankAccount {
    #balance = 0;
    #accountNumber;
    
    constructor(accountNumber, initialBalance = 0) {
        this.#accountNumber = accountNumber;
        this.#balance = initialBalance;
    }
    
    deposit(amount) {
        if (amount > 0) {
            this.#balance += amount;
            return this.#balance;
        }
        throw new Error('Amount must be positive');
    }
    
    withdraw(amount) {
        if (amount > 0 && amount <= this.#balance) {
            this.#balance -= amount;
            return this.#balance;
        }
        throw new Error('Invalid amount or insufficient funds');
    }
    
    getBalance() {
        return this.#balance;
    }
}

const account = new BankAccount('12345', 1000);
console.log(account.getBalance()); // 1000
account.deposit(500);
console.log(account.getBalance()); // 1500
// console.log(account.#balance); // Error: Private field
```

**Inheritance:**

6. **Basic Inheritance:**
```javascript
class Vehicle {
    constructor(make, model, year) {
        this.make = make;
        this.model = model;
        this.year = year;
    }
    
    start() {
        return `${this.make} ${this.model} is starting...`;
    }
    
    stop() {
        return `${this.make} ${this.model} has stopped.`;
    }
}

class Car extends Vehicle {
    constructor(make, model, year, doors) {
        super(make, model, year); // Call parent constructor
        this.doors = doors;
    }
    
    honk() {
        return `${this.make} ${this.model} goes beep beep!`;
    }
    
    // Override parent method
    start() {
        return `The ${this.doors}-door ${this.make} ${this.model} is starting...`;
    }
}

const myCar = new Car('Toyota', 'Camry', 2023, 4);
console.log(myCar.start()); // "The 4-door Toyota Camry is starting..."
console.log(myCar.honk()); // "Toyota Camry goes beep beep!"
```

7. **Advanced Inheritance with Abstract Classes:**
```javascript
class Shape {
    constructor(color) {
        this.color = color;
    }
    
    // Abstract method (convention)
    getArea() {
        throw new Error('getArea() must be implemented by subclass');
    }
    
    getColor() {
        return this.color;
    }
}

class Circle extends Shape {
    constructor(color, radius) {
        super(color);
        this.radius = radius;
    }
    
    getArea() {
        return Math.PI * this.radius * this.radius;
    }
}

class Rectangle extends Shape {
    constructor(color, width, height) {
        super(color);
        this.width = width;
        this.height = height;
    }
    
    getArea() {
        return this.width * this.height;
    }
}

const circle = new Circle('red', 5);
const rectangle = new Rectangle('blue', 4, 6);
console.log(circle.getArea()); // 78.54
console.log(rectangle.getArea()); // 24
```

**Class vs Function Constructor:**

8. **Comparison:**
```javascript
// Function Constructor (ES5)
function PersonFunction(name, age) {
    this.name = name;
    this.age = age;
}

PersonFunction.prototype.greet = function() {
    return `Hello, I'm ${this.name}`;
};

// Class (ES6+)
class PersonClass {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    
    greet() {
        return `Hello, I'm ${this.name}`;
    }
}

// Both work the same way
const person1 = new PersonFunction('John', 30);
const person2 = new PersonClass('Jane', 25);
console.log(person1.greet()); // "Hello, I'm John"
console.log(person2.greet()); // "Hello, I'm Jane"
```

**Best Practices:**
- Use classes for complex object hierarchies
- Prefer composition over inheritance when possible
- Use private fields for encapsulation
- Implement proper error handling in constructors
- Use static methods for utility functions
- Override methods carefully to maintain expected behavior

### 34. What is the difference between function and arrow function?
**Answer:**
Arrow functions don't have their own `this`, `arguments`, and cannot be used as constructors.

**Detailed Explanation:**
Arrow functions, introduced in ES6, provide a more concise syntax for writing functions but behave differently from regular functions in several important ways.

**Key Differences:**

1. **Syntax Comparison:**
```javascript
// Regular function
function add(a, b) {
    return a + b;
}

// Arrow function
const add = (a, b) => a + b;

// Multiple lines
const processData = (data) => {
    const processed = data.map(item => item * 2);
    return processed.filter(item => item > 10);
};
```

2. **`this` Binding:**
```javascript
// Regular function - has its own `this`
const obj = {
    name: 'John',
    regularFunction: function() {
        console.log(this.name); // 'John'
    },
    arrowFunction: () => {
        console.log(this.name); // undefined (or global object)
    }
};

obj.regularFunction(); // 'John'
obj.arrowFunction(); // undefined
```

3. **Lexical `this` Binding:**
```javascript
class Timer {
    constructor() {
        this.seconds = 0;
    }
    
    start() {
        // Regular function - loses `this` context
        setInterval(function() {
            this.seconds++; // Error: this is undefined
            console.log(this.seconds);
        }, 1000);
        
        // Arrow function - preserves `this` context
        setInterval(() => {
            this.seconds++; // Works correctly
            console.log(this.seconds);
        }, 1000);
    }
}
```

4. **Arguments Object:**
```javascript
// Regular function - has `arguments` object
function regularFunction() {
    console.log(arguments); // [1, 2, 3]
    console.log(arguments.length); // 3
}

// Arrow function - no `arguments` object
const arrowFunction = () => {
    console.log(arguments); // Error: arguments is not defined
};

// Use rest parameters instead
const arrowWithRest = (...args) => {
    console.log(args); // [1, 2, 3]
    console.log(args.length); // 3
};

regularFunction(1, 2, 3);
arrowWithRest(1, 2, 3);
```

5. **Constructor Usage:**
```javascript
// Regular function - can be used as constructor
function Person(name) {
    this.name = name;
}

const person1 = new Person('John');
console.log(person1.name); // 'John'

// Arrow function - cannot be used as constructor
const PersonArrow = (name) => {
    this.name = name;
};

// const person2 = new PersonArrow('Jane'); // Error: PersonArrow is not a constructor
```

6. **Hoisting Behavior:**
```javascript
// Regular function - hoisted
console.log(regularFunc()); // 'Hello' (works)

function regularFunc() {
    return 'Hello';
}

// Arrow function - not hoisted
// console.log(arrowFunc()); // Error: Cannot access before initialization

const arrowFunc = () => {
    return 'Hello';
};
```

7. **Method vs Property:**
```javascript
const obj = {
    name: 'Test',
    
    // Regular function as method
    regularMethod: function() {
        return this.name;
    },
    
    // Arrow function as property
    arrowMethod: () => {
        return this.name; // undefined
    },
    
    // Arrow function in method
    regularMethodWithArrow: function() {
        const innerArrow = () => {
            return this.name; // 'Test' (lexical this)
        };
        return innerArrow();
    }
};

console.log(obj.regularMethod()); // 'Test'
console.log(obj.arrowMethod()); // undefined
console.log(obj.regularMethodWithArrow()); // 'Test'
```

**When to Use Each:**

**Use Arrow Functions for:**
- Array methods (map, filter, reduce)
- Callbacks and event handlers
- Short, simple functions
- When you want lexical `this` binding

```javascript
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(n => n * 2);
const evens = numbers.filter(n => n % 2 === 0);
const sum = numbers.reduce((acc, n) => acc + n, 0);
```

**Use Regular Functions for:**
- Object methods
- Constructor functions
- When you need `arguments` object
- When you need function hoisting
- When you need to change `this` context

```javascript
const calculator = {
    value: 0,
    add: function(num) {
        this.value += num;
        return this;
    },
    multiply: function(num) {
        this.value *= num;
        return this;
    }
};

calculator.add(5).multiply(2);
console.log(calculator.value); // 10
```

### 35. What are JavaScript destructuring assignments?
**Answer:**
Syntax for extracting values from arrays or properties from objects into distinct variables.

**Detailed Explanation:**
Destructuring assignment is a JavaScript expression that allows you to unpack values from arrays or properties from objects into distinct variables. It provides a clean and concise way to extract data from complex structures.

**Array Destructuring:**

1. **Basic Array Destructuring:**
```javascript
const colors = ['red', 'green', 'blue'];
const [first, second, third] = colors;
console.log(first); // 'red'
console.log(second); // 'green'
console.log(third); // 'blue'
```

2. **Skipping Elements:**
```javascript
const numbers = [1, 2, 3, 4, 5];
const [first, , third, , fifth] = numbers;
console.log(first, third, fifth); // 1, 3, 5
```

3. **Default Values:**
```javascript
const arr = [1, 2];
const [a, b, c = 3, d = 4] = arr;
console.log(a, b, c, d); // 1, 2, 3, 4
```

4. **Rest Pattern:**
```javascript
const numbers = [1, 2, 3, 4, 5];
const [first, second, ...rest] = numbers;
console.log(first); // 1
console.log(second); // 2
console.log(rest); // [3, 4, 5]
```

5. **Swapping Variables:**
```javascript
let a = 1;
let b = 2;
[a, b] = [b, a];
console.log(a, b); // 2, 1
```

**Object Destructuring:**

6. **Basic Object Destructuring:**
```javascript
const person = {
    name: 'John',
    age: 30,
    city: 'New York'
};

const { name, age, city } = person;
console.log(name, age, city); // 'John', 30, 'New York'
```

7. **Renaming Variables:**
```javascript
const user = {
    firstName: 'Jane',
    lastName: 'Doe',
    email: 'jane@example.com'
};

const { firstName: fName, lastName: lName, email } = user;
console.log(fName, lName, email); // 'Jane', 'Doe', 'jane@example.com'
```

8. **Default Values:**
```javascript
const config = {
    apiUrl: 'https://api.example.com',
    timeout: 5000
};

const { apiUrl, timeout = 10000, retries = 3 } = config;
console.log(apiUrl, timeout, retries); // 'https://api.example.com', 5000, 3
```

9. **Nested Destructuring:**
```javascript
const user = {
    name: 'John',
    address: {
        street: '123 Main St',
        city: 'New York',
        coordinates: {
            lat: 40.7128,
            lng: -74.0060
        }
    }
};

const {
    name,
    address: {
        street,
        coordinates: { lat, lng }
    }
} = user;

console.log(name, street, lat, lng); // 'John', '123 Main St', 40.7128, -74.0060
```

10. **Function Parameters:**
```javascript
// Destructuring in function parameters
function greetUser({ name, age = 0 }) {
    return `Hello ${name}, you are ${age} years old`;
}

const user = { name: 'Alice', age: 25 };
console.log(greetUser(user)); // 'Hello Alice, you are 25 years old'

// With default values
function createUser({ name, email, role = 'user' }) {
    return { name, email, role };
}

const newUser = createUser({ name: 'Bob', email: 'bob@example.com' });
console.log(newUser); // { name: 'Bob', email: 'bob@example.com', role: 'user' }
```

**Advanced Patterns:**

11. **Computed Property Names:**
```javascript
const prop = 'name';
const obj = { name: 'John', age: 30 };
const { [prop]: value } = obj;
console.log(value); // 'John'
```

12. **Destructuring with Rest:**
```javascript
const person = {
    name: 'John',
    age: 30,
    city: 'New York',
    country: 'USA',
    occupation: 'Developer'
};

const { name, age, ...details } = person;
console.log(name, age); // 'John', 30
console.log(details); // { city: 'New York', country: 'USA', occupation: 'Developer' }
```

13. **Mixed Array and Object Destructuring:**
```javascript
const data = [
    { name: 'John', age: 30 },
    { name: 'Jane', age: 25 }
];

const [firstPerson, { name: secondName }] = data;
console.log(firstPerson); // { name: 'John', age: 30 }
console.log(secondName); // 'Jane'
```

**Practical Use Cases:**

14. **API Response Handling:**
```javascript
// Simulating API response
const apiResponse = {
    status: 'success',
    data: {
        users: [
            { id: 1, name: 'John', email: 'john@example.com' },
            { id: 2, name: 'Jane', email: 'jane@example.com' }
        ],
        pagination: {
            page: 1,
            total: 2
        }
    }
};

const {
    status,
    data: {
        users,
        pagination: { page, total }
    }
} = apiResponse;

console.log(`Status: ${status}, Users: ${users.length}, Page: ${page}/${total}`);
```

15. **Configuration Objects:**
```javascript
const config = {
    database: {
        host: 'localhost',
        port: 5432,
        credentials: {
            username: 'admin',
            password: 'secret'
        }
    },
    server: {
        port: 3000,
        environment: 'development'
    }
};

const {
    database: {
        host: dbHost,
        port: dbPort,
        credentials: { username, password }
    },
    server: { port: serverPort, environment }
} = config;

console.log(`DB: ${dbHost}:${dbPort}, Server: ${serverPort}, Env: ${environment}`);
```

**Best Practices:**
- Use destructuring for cleaner, more readable code
- Provide default values for optional properties
- Use meaningful variable names when renaming
- Combine with rest operator for flexible parameter handling
- Use nested destructuring carefully to avoid over-complexity

### 36. What is the spread operator in JavaScript?
**Answer:**
`...` operator allows expansion of arrays or objects in places where multiple elements are expected.

**Detailed Explanation:**
The spread operator (`...`) is a powerful ES6 feature that allows you to expand iterables (arrays, objects, strings) into individual elements. It provides a clean and concise way to copy, merge, and manipulate data structures.

**Array Spread:**

1. **Basic Array Spreading:**
```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combined = [...arr1, ...arr2];
console.log(combined); // [1, 2, 3, 4, 5, 6]
```

2. **Array Copying:**
```javascript
const original = [1, 2, 3, 4, 5];
const copy = [...original];
console.log(copy); // [1, 2, 3, 4, 5]
console.log(copy === original); // false (different references)
```

3. **Adding Elements:**
```javascript
const numbers = [1, 2, 3];
const withNewElements = [0, ...numbers, 4, 5];
console.log(withNewElements); // [0, 1, 2, 3, 4, 5]
```

4. **Function Arguments:**
```javascript
function sum(a, b, c) {
    return a + b + c;
}

const numbers = [1, 2, 3];
console.log(sum(...numbers)); // 6

// Math.max with spread
const values = [10, 5, 8, 3, 12];
console.log(Math.max(...values)); // 12
```

5. **Array Methods:**
```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

// Concatenation
const concatenated = [...arr1, ...arr2];

// Inserting elements
const inserted = [...arr1.slice(0, 2), 99, ...arr1.slice(2)];
console.log(inserted); // [1, 2, 99, 3]

// Removing elements
const removed = [...arr1.slice(0, 1), ...arr1.slice(2)];
console.log(removed); // [1, 3]
```

**Object Spread:**

6. **Basic Object Spreading:**
```javascript
const obj1 = { a: 1, b: 2 };
const obj2 = { c: 3, d: 4 };
const combined = { ...obj1, ...obj2 };
console.log(combined); // { a: 1, b: 2, c: 3, d: 4 }
```

7. **Object Copying:**
```javascript
const original = { name: 'John', age: 30 };
const copy = { ...original };
console.log(copy); // { name: 'John', age: 30 }
console.log(copy === original); // false (different references)
```

8. **Property Overriding:**
```javascript
const user = { name: 'John', age: 30, city: 'New York' };
const updatedUser = { ...user, age: 31, country: 'USA' };
console.log(updatedUser); // { name: 'John', age: 31, city: 'New York', country: 'USA' }
```

9. **Nested Object Spreading:**
```javascript
const user = {
    name: 'John',
    address: {
        street: '123 Main St',
        city: 'New York'
    }
};

// Shallow copy - nested objects are still referenced
const shallowCopy = { ...user };
shallowCopy.address.city = 'Boston';
console.log(user.address.city); // 'Boston' (original is modified)

// Deep copy using JSON (for simple objects)
const deepCopy = JSON.parse(JSON.stringify(user));
```

**String Spread:**

10. **String to Array:**
```javascript
const str = 'hello';
const chars = [...str];
console.log(chars); // ['h', 'e', 'l', 'l', 'o']

// Useful for string manipulation
const reversed = [...str].reverse().join('');
console.log(reversed); // 'olleh'
```

**Advanced Use Cases:**

11. **Rest Parameters:**
```javascript
function processItems(first, second, ...rest) {
    console.log('First:', first);
    console.log('Second:', second);
    console.log('Rest:', rest);
}

processItems(1, 2, 3, 4, 5);
// First: 1
// Second: 2
// Rest: [3, 4, 5]
```

12. **Dynamic Function Calls:**
```javascript
function createUser(name, email, ...roles) {
    return {
        name,
        email,
        roles: [...roles]
    };
}

const user = createUser('John', 'john@example.com', 'admin', 'user', 'moderator');
console.log(user); // { name: 'John', email: 'john@example.com', roles: ['admin', 'user', 'moderator'] }
```

13. **Array Destructuring with Spread:**
```javascript
const numbers = [1, 2, 3, 4, 5];
const [first, second, ...rest] = numbers;
console.log(first, second, rest); // 1, 2, [3, 4, 5]
```

14. **Object Destructuring with Spread:**
```javascript
const user = {
    id: 1,
    name: 'John',
    email: 'john@example.com',
    age: 30,
    city: 'New York'
};

const { id, name, ...profile } = user;
console.log(id, name); // 1, 'John'
console.log(profile); // { email: 'john@example.com', age: 30, city: 'New York' }
```

**Practical Examples:**

15. **State Management (React-like):**
```javascript
const initialState = {
    user: null,
    loading: false,
    error: null
};

// Updating state immutably
const setUser = (state, user) => ({
    ...state,
    user,
    loading: false,
    error: null
});

const setLoading = (state, loading) => ({
    ...state,
    loading
});

let state = initialState;
state = setLoading(state, true);
state = setUser(state, { name: 'John', age: 30 });
console.log(state); // { user: { name: 'John', age: 30 }, loading: false, error: null }
```

16. **Array Manipulation:**
```javascript
// Removing duplicates
const numbers = [1, 2, 2, 3, 3, 3, 4];
const unique = [...new Set(numbers)];
console.log(unique); // [1, 2, 3, 4]

// Flattening arrays
const nested = [[1, 2], [3, 4], [5, 6]];
const flattened = [].concat(...nested);
console.log(flattened); // [1, 2, 3, 4, 5, 6]
```

17. **Function Composition:**
```javascript
const add = (x, y) => x + y;
const multiply = (x, y) => x * y;

const numbers = [1, 2, 3, 4, 5];
const result = numbers.reduce((acc, num) => add(acc, num), 0);
console.log(result); // 15

// Using spread for multiple arguments
const calculate = (...args) => args.reduce((acc, num) => add(acc, num), 0);
console.log(calculate(...numbers)); // 15
```

**Performance Considerations:**
- Spread operator creates new objects/arrays (shallow copy)
- Use sparingly with large datasets
- Consider alternatives like `Object.assign()` for objects
- Use `Array.from()` for array-like objects when needed

**Best Practices:**
- Use for immutable updates
- Prefer spread over `Object.assign()` for objects
- Use with destructuring for clean parameter handling
- Be mindful of performance with large datasets
- Use for creating new arrays/objects rather than mutating existing ones

### 37. What are JavaScript template literals?
**Answer:**
String literals allowing embedded expressions using backticks and `${}` syntax.

**Detailed Explanation:**
Template literals, introduced in ES6, provide an enhanced way to work with strings. They use backticks (`) instead of quotes and allow for multi-line strings, embedded expressions, and tagged templates.

**Basic Syntax:**

1. **Simple Template Literals:**
```javascript
const name = 'John';
const age = 30;
const message = `Hello, my name is ${name} and I'm ${age} years old.`;
console.log(message); // 'Hello, my name is John and I'm 30 years old.'
```

2. **Multi-line Strings:**
```javascript
// Traditional way (requires concatenation)
const oldWay = 'This is line 1\n' +
               'This is line 2\n' +
               'This is line 3';

// Template literal way
const newWay = `This is line 1
This is line 2
This is line 3`;

console.log(oldWay === newWay); // true
```

3. **Expression Evaluation:**
```javascript
const a = 10;
const b = 20;
const result = `The sum of ${a} and ${b} is ${a + b}`;
console.log(result); // 'The sum of 10 and 20 is 30'
```

**Advanced Features:**

4. **Nested Template Literals:**
```javascript
const items = ['apple', 'banana', 'orange'];
const html = `
  <ul>
    ${items.map(item => `<li>${item}</li>`).join('')}
  </ul>
`;
console.log(html);
// <ul>
//   <li>apple</li>
//   <li>banana</li>
//   <li>orange</li>
// </ul>
```

5. **Conditional Expressions:**
```javascript
const user = { name: 'John', isAdmin: true };
const message = `Welcome ${user.isAdmin ? 'Admin' : 'User'} ${user.name}!`;
console.log(message); // 'Welcome Admin John!'
```

6. **Function Calls:**
```javascript
function formatCurrency(amount) {
    return `$${amount.toFixed(2)}`;
}

const price = 19.99;
const display = `Total: ${formatCurrency(price)}`;
console.log(display); // 'Total: $19.99'
```

**Tagged Template Literals:**

7. **Basic Tagged Template:**
```javascript
function highlight(strings, ...values) {
    return strings.reduce((result, string, i) => {
        const value = values[i] ? `<mark>${values[i]}</mark>` : '';
        return result + string + value;
    }, '');
}

const name = 'John';
const age = 30;
const html = highlight`Hello ${name}, you are ${age} years old.`;
console.log(html); // 'Hello <mark>John</mark>, you are <mark>30</mark> years old.'
```

8. **SQL Query Builder:**
```javascript
function sql(strings, ...values) {
    return {
        query: strings.join('?'),
        params: values
    };
}

const userId = 123;
const status = 'active';
const { query, params } = sql`SELECT * FROM users WHERE id = ${userId} AND status = ${status}`;
console.log(query); // 'SELECT * FROM users WHERE id = ? AND status = ?'
console.log(params); // [123, 'active']
```

9. **i18n (Internationalization):**
```javascript
function translate(strings, ...values) {
    const translations = {
        'Hello': 'Hola',
        'Goodbye': 'Adiós',
        'Thank you': 'Gracias'
    };
    
    return strings.reduce((result, string, i) => {
        const translated = translations[string.trim()] || string;
        const value = values[i] || '';
        return result + translated + value;
    }, '');
}

const name = 'Juan';
const message = translate`Hello ${name}!`;
console.log(message); // 'Hola Juan!'
```

**Practical Examples:**

10. **HTML Generation:**
```javascript
function createCard({ title, content, author, date }) {
    return `
        <div class="card">
            <h2>${title}</h2>
            <p>${content}</p>
            <div class="meta">
                <span>By ${author}</span>
                <span>${new Date(date).toLocaleDateString()}</span>
            </div>
        </div>
    `;
}

const card = createCard({
    title: 'JavaScript Tips',
    content: 'Template literals are awesome!',
    author: 'John Doe',
    date: '2023-12-01'
});
console.log(card);
```

11. **Configuration Objects:**
```javascript
const config = {
    apiUrl: 'https://api.example.com',
    version: 'v1',
    timeout: 5000
};

const apiCall = `
    fetch('${config.apiUrl}/${config.version}/users')
        .then(response => response.json())
        .catch(error => console.error('Error:', error));
`;
console.log(apiCall);
```

12. **Dynamic CSS:**
```javascript
function createStyles(theme) {
    return `
        .container {
            background-color: ${theme.background};
            color: ${theme.text};
            padding: ${theme.padding}px;
        }
        .button {
            background-color: ${theme.primary};
            border-radius: ${theme.borderRadius}px;
        }
    `;
}

const darkTheme = {
    background: '#333',
    text: '#fff',
    primary: '#007bff',
    padding: 20,
    borderRadius: 5
};

const css = createStyles(darkTheme);
console.log(css);
```

**Escape Sequences:**

13. **Escaping in Template Literals:**
```javascript
// Escaping backticks
const message = `This is a backtick: \``;
console.log(message); // 'This is a backtick: `'

// Escaping dollar signs
const price = 100;
const text = `The price is \$${price}`;
console.log(text); // 'The price is $100'

// Raw strings
function raw(strings, ...values) {
    return strings.raw[0];
}
const rawString = raw`This is a raw string with \n newline`;
console.log(rawString); // 'This is a raw string with \n newline'
```

**Performance Considerations:**

14. **Template Literal Performance:**
```javascript
// Template literals are generally faster than string concatenation
const name = 'John';
const age = 30;

// Slower (creates intermediate strings)
const oldWay = 'Hello ' + name + ', you are ' + age + ' years old.';

// Faster (single expression evaluation)
const newWay = `Hello ${name}, you are ${age} years old.`;
```

**Best Practices:**
- Use template literals for multi-line strings
- Prefer template literals over string concatenation
- Use tagged templates for complex string processing
- Be careful with user input in template literals (security)
- Use template literals for dynamic HTML generation
- Consider performance for frequently called functions

### 38. What is the difference between shallow and deep copy?
**Answer:**
Shallow copy copies only first level, deep copy copies all nested levels.

**Detailed Explanation:**
Understanding the difference between shallow and deep copying is crucial for working with objects and arrays in JavaScript. The choice between them affects how changes to copied data impact the original data.

**Shallow Copy:**

1. **What is Shallow Copy:**
```javascript
const original = {
    name: 'John',
    age: 30,
    address: {
        street: '123 Main St',
        city: 'New York'
    },
    hobbies: ['reading', 'gaming']
};

// Shallow copy using spread operator
const shallowCopy = { ...original };

// Modifying primitive properties (safe)
shallowCopy.name = 'Jane';
shallowCopy.age = 25;
console.log(original.name); // 'John' (unchanged)
console.log(original.age); // 30 (unchanged)

// Modifying nested objects (DANGEROUS!)
shallowCopy.address.city = 'Boston';
console.log(original.address.city); // 'Boston' (original is modified!)

// Modifying nested arrays (DANGEROUS!)
shallowCopy.hobbies.push('cooking');
console.log(original.hobbies); // ['reading', 'gaming', 'cooking'] (original is modified!)
```

2. **Shallow Copy Methods:**
```javascript
const arr = [1, 2, 3, { a: 1 }];

// Array spread
const copy1 = [...arr];

// Array.slice()
const copy2 = arr.slice();

// Array.from()
const copy3 = Array.from(arr);

// Object.assign()
const obj = { a: 1, b: { c: 2 } };
const copy4 = Object.assign({}, obj);

// All create shallow copies
console.log(copy1 === arr); // false (different references)
console.log(copy1[3] === arr[3]); // true (same nested object reference)
```

**Deep Copy:**

3. **What is Deep Copy:**
```javascript
const original = {
    name: 'John',
    address: {
        street: '123 Main St',
        city: 'New York',
        coordinates: {
            lat: 40.7128,
            lng: -74.0060
        }
    },
    hobbies: ['reading', 'gaming']
};

// Deep copy using JSON methods (limited)
const deepCopy = JSON.parse(JSON.stringify(original));

// Modifying nested properties (safe)
deepCopy.address.city = 'Boston';
deepCopy.hobbies.push('cooking');

console.log(original.address.city); // 'New York' (unchanged)
console.log(original.hobbies); // ['reading', 'gaming'] (unchanged)
```

4. **Deep Copy Methods:**
```javascript
// Method 1: JSON.parse(JSON.stringify()) - Limited
function deepCopyJSON(obj) {
    return JSON.parse(JSON.stringify(obj));
}

// Method 2: Recursive function
function deepCopy(obj) {
    if (obj === null || typeof obj !== 'object') {
        return obj;
    }
    
    if (obj instanceof Date) {
        return new Date(obj.getTime());
    }
    
    if (obj instanceof Array) {
        return obj.map(item => deepCopy(item));
    }
    
    if (typeof obj === 'object') {
        const copy = {};
        Object.keys(obj).forEach(key => {
            copy[key] = deepCopy(obj[key]);
        });
        return copy;
    }
}

// Method 3: Using structuredClone (modern browsers)
function deepCopyStructured(obj) {
    return structuredClone(obj);
}
```

**Comparison Examples:**

5. **Shallow vs Deep Copy Comparison:**
```javascript
const original = {
    name: 'John',
    nested: {
        value: 42,
        array: [1, 2, 3]
    }
};

// Shallow copy
const shallow = { ...original };
shallow.nested.value = 100;
shallow.nested.array.push(4);

console.log(original.nested.value); // 100 (modified!)
console.log(original.nested.array); // [1, 2, 3, 4] (modified!)

// Reset original
original.nested.value = 42;
original.nested.array = [1, 2, 3];

// Deep copy
const deep = JSON.parse(JSON.stringify(original));
deep.nested.value = 200;
deep.nested.array.push(5);

console.log(original.nested.value); // 42 (unchanged)
console.log(original.nested.array); // [1, 2, 3] (unchanged)
```

**Advanced Deep Copy:**

6. **Handling Special Cases:**
```javascript
function advancedDeepCopy(obj) {
    const seen = new WeakMap();
    
    function copy(value) {
        // Handle primitives
        if (value === null || typeof value !== 'object') {
            return value;
        }
        
        // Handle circular references
        if (seen.has(value)) {
            return seen.get(value);
        }
        
        // Handle Date
        if (value instanceof Date) {
            return new Date(value.getTime());
        }
        
        // Handle RegExp
        if (value instanceof RegExp) {
            return new RegExp(value.source, value.flags);
        }
        
        // Handle Array
        if (Array.isArray(value)) {
            const copy = [];
            seen.set(value, copy);
            value.forEach((item, index) => {
                copy[index] = copy(item);
            });
            return copy;
        }
        
        // Handle Object
        if (typeof value === 'object') {
            const copy = {};
            seen.set(value, copy);
            Object.keys(value).forEach(key => {
                copy[key] = copy(value[key]);
            });
            return copy;
        }
    }
    
    return copy(obj);
}

// Test with circular reference
const obj = { name: 'John' };
obj.self = obj;

const deepCopy = advancedDeepCopy(obj);
console.log(deepCopy.self === deepCopy); // true (circular reference preserved)
```

**Performance Considerations:**

7. **Performance Comparison:**
```javascript
const largeObject = {
    data: new Array(10000).fill(0).map((_, i) => ({
        id: i,
        nested: { value: i * 2 }
    }))
};

// Shallow copy (fast)
console.time('Shallow Copy');
const shallow = { ...largeObject };
console.timeEnd('Shallow Copy');

// Deep copy (slower)
console.time('Deep Copy');
const deep = JSON.parse(JSON.stringify(largeObject));
console.timeEnd('Deep Copy');
```

**Use Cases:**

8. **When to Use Shallow Copy:**
```javascript
// State management (React)
const updateUser = (state, updates) => ({
    ...state,
    ...updates
});

// Function parameters
function processData({ name, age, ...rest }) {
    // rest is a shallow copy of remaining properties
    return { name, age, processed: true, ...rest };
}
```

9. **When to Use Deep Copy:**
```javascript
// Configuration objects
const defaultConfig = {
    api: {
        url: 'https://api.example.com',
        timeout: 5000
    },
    features: {
        enabled: true,
        options: ['feature1', 'feature2']
    }
};

// Create user-specific config without affecting default
const userConfig = JSON.parse(JSON.stringify(defaultConfig));
userConfig.api.url = 'https://user-api.example.com';
userConfig.features.options.push('feature3');
```

**Best Practices:**
- Use shallow copy for simple objects with primitive values
- Use deep copy when working with nested objects/arrays
- Be aware of performance implications of deep copying
- Consider using libraries like Lodash for complex deep copying
- Use `structuredClone()` for modern browsers when available
- Handle circular references appropriately
- Consider immutable data structures for complex state management

### 39. What are JavaScript getters and setters?
**Answer:**
Special methods that provide access to object properties with custom logic.

**Detailed Explanation:**
Getters and setters are special methods in JavaScript that allow you to define custom behavior when accessing or modifying object properties. They provide a way to add validation, computation, or side effects to property access.

**Basic Syntax:**

1. **Object Literal Getters and Setters:**
```javascript
const person = {
    _firstName: 'John',
    _lastName: 'Doe',
    
    // Getter
    get fullName() {
        return `${this._firstName} ${this._lastName}`;
    },
    
    // Setter
    set fullName(value) {
        const parts = value.split(' ');
        this._firstName = parts[0];
        this._lastName = parts[1] || '';
    },
    
    get firstName() {
        return this._firstName;
    },
    
    set firstName(value) {
        if (typeof value === 'string' && value.length > 0) {
            this._firstName = value;
        } else {
            throw new Error('First name must be a non-empty string');
        }
    }
};

console.log(person.fullName); // 'John Doe'
person.fullName = 'Jane Smith';
console.log(person.firstName); // 'Jane'
console.log(person.lastName); // 'Smith'
```

2. **Class Getters and Setters:**
```javascript
class Rectangle {
    constructor(width, height) {
        this._width = width;
        this._height = height;
    }
    
    get width() {
        return this._width;
    }
    
    set width(value) {
        if (value > 0) {
            this._width = value;
        } else {
            throw new Error('Width must be positive');
        }
    }
    
    get height() {
        return this._height;
    }
    
    set height(value) {
        if (value > 0) {
            this._height = value;
        } else {
            throw new Error('Height must be positive');
        }
    }
    
    get area() {
        return this._width * this._height;
    }
    
    get perimeter() {
        return 2 * (this._width + this._height);
    }
}

const rect = new Rectangle(5, 10);
console.log(rect.area); // 50
console.log(rect.perimeter); // 30
rect.width = 8;
console.log(rect.area); // 80
```

**Advanced Use Cases:**

3. **Computed Properties:**
```javascript
class Temperature {
    constructor(celsius) {
        this._celsius = celsius;
    }
    
    get celsius() {
        return this._celsius;
    }
    
    set celsius(value) {
        this._celsius = value;
    }
    
    get fahrenheit() {
        return (this._celsius * 9/5) + 32;
    }
    
    set fahrenheit(value) {
        this._celsius = (value - 32) * 5/9;
    }
    
    get kelvin() {
        return this._celsius + 273.15;
    }
    
    set kelvin(value) {
        this._celsius = value - 273.15;
    }
}

const temp = new Temperature(25);
console.log(temp.celsius); // 25
console.log(temp.fahrenheit); // 77
console.log(temp.kelvin); // 298.15

temp.fahrenheit = 86;
console.log(temp.celsius); // 30
```

4. **Lazy Loading:**
```javascript
class DataManager {
    constructor() {
        this._data = null;
        this._isLoaded = false;
    }
    
    get data() {
        if (!this._isLoaded) {
            console.log('Loading data...');
            this._data = this.loadData();
            this._isLoaded = true;
        }
        return this._data;
    }
    
    loadData() {
        // Simulate expensive operation
        return {
            users: ['John', 'Jane', 'Bob'],
            timestamp: new Date()
        };
    }
}

const manager = new DataManager();
// Data is not loaded yet
console.log(manager.data); // 'Loading data...' then returns data
console.log(manager.data); // Returns cached data (no loading message)
```

5. **Validation and Side Effects:**
```javascript
class User {
    constructor() {
        this._email = '';
        this._password = '';
        this._loginAttempts = 0;
    }
    
    get email() {
        return this._email;
    }
    
    set email(value) {
        const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        if (emailRegex.test(value)) {
            this._email = value.toLowerCase();
        } else {
            throw new Error('Invalid email format');
        }
    }
    
    get password() {
        return '***'; // Never return actual password
    }
    
    set password(value) {
        if (value.length < 8) {
            throw new Error('Password must be at least 8 characters');
        }
        this._password = this.hashPassword(value);
    }
    
    hashPassword(password) {
        // Simple hash simulation
        return btoa(password);
    }
    
    get isLocked() {
        return this._loginAttempts >= 3;
    }
}

const user = new User();
user.email = 'john@example.com';
user.password = 'securepass123';
console.log(user.email); // 'john@example.com'
console.log(user.password); // '***'
```

**Dynamic Getters and Setters:**

6. **Using Object.defineProperty:**
```javascript
const obj = {};

Object.defineProperty(obj, 'dynamicProp', {
    get() {
        return this._value || 'default';
    },
    set(value) {
        this._value = value;
        console.log(`Property set to: ${value}`);
    },
    enumerable: true,
    configurable: true
});

obj.dynamicProp = 'Hello';
console.log(obj.dynamicProp); // 'Hello'
```

7. **Multiple Properties:**
```javascript
class Config {
    constructor() {
        this._values = {};
    }
    
    // Dynamic getter for any property
    get(prop) {
        return this._values[prop];
    }
    
    set(prop, value) {
        this._values[prop] = value;
    }
}

// Create dynamic getters/setters
const config = new Config();
['apiUrl', 'timeout', 'retries'].forEach(prop => {
    Object.defineProperty(config, prop, {
        get() {
            return this.get(prop);
        },
        set(value) {
            this.set(prop, value);
        },
        enumerable: true
    });
});

config.apiUrl = 'https://api.example.com';
config.timeout = 5000;
console.log(config.apiUrl); // 'https://api.example.com'
```

**Getter/Setter Patterns:**

8. **Proxy-like Behavior:**
```javascript
class Observable {
    constructor() {
        this._data = {};
        this._listeners = {};
    }
    
    get(prop) {
        return this._data[prop];
    }
    
    set(prop, value) {
        const oldValue = this._data[prop];
        this._data[prop] = value;
        
        // Notify listeners
        if (this._listeners[prop]) {
            this._listeners[prop].forEach(callback => {
                callback(value, oldValue);
            });
        }
    }
    
    observe(prop, callback) {
        if (!this._listeners[prop]) {
            this._listeners[prop] = [];
        }
        this._listeners[prop].push(callback);
    }
}

const observable = new Observable();
observable.observe('name', (newValue, oldValue) => {
    console.log(`Name changed from ${oldValue} to ${newValue}`);
});

observable.set('name', 'John'); // 'Name changed from undefined to John'
observable.set('name', 'Jane'); // 'Name changed from John to Jane'
```

**Best Practices:**
- Use getters for computed properties
- Use setters for validation and side effects
- Keep getters pure (no side effects)
- Use private fields (underscore prefix) for internal state
- Consider performance implications of complex getters
- Use getters/setters for API consistency
- Document the behavior of custom getters/setters

### 40. What is the difference between Object.freeze() and Object.seal()?
**Answer:**
- `Object.freeze()`: Makes object immutable
- `Object.seal()`: Prevents adding/removing properties but allows modification

**Detailed Explanation:**
Both `Object.freeze()` and `Object.seal()` are methods that restrict object modification, but they operate at different levels of restriction. Understanding their differences is crucial for object immutability and data protection.

**Object.freeze() - Complete Immutability:**

1. **Basic Usage:**
```javascript
const obj = {
    name: 'John',
    age: 30,
    address: {
        city: 'New York'
    }
};

Object.freeze(obj);

// These operations will fail silently or throw errors
obj.name = 'Jane'; // No effect (in strict mode: TypeError)
obj.newProp = 'value'; // No effect
delete obj.age; // No effect

console.log(obj); // { name: 'John', age: 30, address: { city: 'New York' } }
```

2. **Shallow Freeze (Nested Objects Not Frozen):**
```javascript
const obj = {
    name: 'John',
    address: {
        city: 'New York',
        country: 'USA'
    }
};

Object.freeze(obj);

// This will work (nested object not frozen)
obj.address.city = 'Boston';
obj.address.zipCode = '02101';

console.log(obj.address); // { city: 'Boston', country: 'USA', zipCode: '02101' }
```

3. **Deep Freeze Implementation:**
```javascript
function deepFreeze(obj) {
    // Get property names
    const propNames = Object.getOwnPropertyNames(obj);
    
    // Freeze properties before freezing self
    propNames.forEach(name => {
        const prop = obj[name];
        if (prop !== null && (typeof prop === 'object' || typeof prop === 'function')) {
            deepFreeze(prop);
        }
    });
    
    return Object.freeze(obj);
}

const obj = {
    name: 'John',
    address: {
        city: 'New York',
        coordinates: {
            lat: 40.7128,
            lng: -74.0060
        }
    }
};

deepFreeze(obj);

// Now nested objects are also frozen
obj.address.city = 'Boston'; // No effect
obj.address.coordinates.lat = 42.3601; // No effect

console.log(obj.address.city); // 'New York'
console.log(obj.address.coordinates.lat); // 40.7128
```

**Object.seal() - Partial Immutability:**

4. **Basic Usage:**
```javascript
const obj = {
    name: 'John',
    age: 30
};

Object.seal(obj);

// These operations will fail
obj.newProp = 'value'; // No effect
delete obj.name; // No effect

// This will work (existing properties can be modified)
obj.name = 'Jane';
obj.age = 25;

console.log(obj); // { name: 'Jane', age: 25 }
```

5. **Property Descriptor Changes:**
```javascript
const obj = {
    name: 'John'
};

Object.seal(obj);

// Check property descriptors
const descriptor = Object.getOwnPropertyDescriptor(obj, 'name');
console.log(descriptor.configurable); // false (cannot be deleted or reconfigured)
console.log(descriptor.writable); // true (can still be modified)

// Try to reconfigure property
Object.defineProperty(obj, 'name', {
    writable: false
}); // TypeError: Cannot redefine property
```

**Comparison Examples:**

6. **Side-by-Side Comparison:**
```javascript
// Original object
const original = {
    name: 'John',
    age: 30,
    address: {
        city: 'New York'
    }
};

// Freeze example
const frozen = { ...original };
Object.freeze(frozen);

// Seal example
const sealed = { ...original };
Object.seal(sealed);

// Test operations
console.log('=== FROZEN OBJECT ===');
try {
    frozen.name = 'Jane'; // Fails silently
    frozen.newProp = 'value'; // Fails silently
    delete frozen.age; // Fails silently
    console.log('Frozen object:', frozen); // Unchanged
} catch (error) {
    console.log('Error:', error.message);
}

console.log('\n=== SEALED OBJECT ===');
try {
    sealed.name = 'Jane'; // Works
    sealed.newProp = 'value'; // Fails silently
    delete sealed.age; // Fails silently
    console.log('Sealed object:', sealed); // { name: 'Jane', age: 30, address: { city: 'New York' } }
} catch (error) {
    console.log('Error:', error.message);
}
```

**Advanced Use Cases:**

7. **Configuration Objects:**
```javascript
// Application configuration
const config = {
    apiUrl: 'https://api.example.com',
    timeout: 5000,
    retries: 3,
    features: {
        logging: true,
        caching: false
    }
};

// Seal to prevent adding new properties but allow modification
Object.seal(config);

// This works (modifying existing properties)
config.timeout = 10000;
config.features.logging = false;

// This fails (adding new properties)
config.newFeature = true; // No effect

console.log(config); // Modified but no new properties
```

8. **Constants with Sealed Objects:**
```javascript
// Create a constants object
const CONSTANTS = {
    API_VERSION: 'v1',
    MAX_RETRIES: 3,
    TIMEOUT: 5000
};

// Freeze to make it truly constant
Object.freeze(CONSTANTS);

// These will fail
CONSTANTS.API_VERSION = 'v2'; // No effect
CONSTANTS.NEW_CONSTANT = 'value'; // No effect

console.log(CONSTANTS); // Unchanged
```

9. **Immutable State Management:**
```javascript
class StateManager {
    constructor(initialState) {
        this._state = deepFreeze(initialState);
    }
    
    getState() {
        return this._state;
    }
    
    updateState(updates) {
        // Create new state with updates
        const newState = { ...this._state, ...updates };
        this._state = deepFreeze(newState);
        return this._state;
    }
}

const stateManager = new StateManager({
    user: { name: 'John', age: 30 },
    settings: { theme: 'dark' }
});

// State is frozen
const state = stateManager.getState();
// state.user.name = 'Jane'; // Would fail in strict mode

// Update through proper method
const newState = stateManager.updateState({
    user: { ...state.user, name: 'Jane' }
});
console.log(newState.user.name); // 'Jane'
```

**Checking Object Status:**

10. **Object.isFrozen() and Object.isSealed():**
```javascript
const obj1 = { name: 'John' };
const obj2 = { name: 'Jane' };
const obj3 = { name: 'Bob' };

Object.freeze(obj1);
Object.seal(obj2);
// obj3 remains normal

console.log(Object.isFrozen(obj1)); // true
console.log(Object.isFrozen(obj2)); // false
console.log(Object.isFrozen(obj3)); // false

console.log(Object.isSealed(obj1)); // true (frozen objects are also sealed)
console.log(Object.isSealed(obj2)); // true
console.log(Object.isSealed(obj3)); // false

console.log(Object.isExtensible(obj1)); // false
console.log(Object.isExtensible(obj2)); // false
console.log(Object.isExtensible(obj3)); // true
```

**Performance Considerations:**

11. **Performance Impact:**
```javascript
const largeObject = {};
for (let i = 0; i < 10000; i++) {
    largeObject[`prop${i}`] = i;
}

// Measure freeze performance
console.time('Freeze');
Object.freeze(largeObject);
console.timeEnd('Freeze');

// Measure seal performance
const largeObject2 = { ...largeObject };
console.time('Seal');
Object.seal(largeObject2);
console.timeEnd('Seal');
```

**Best Practices:**
- Use `Object.freeze()` for truly immutable data
- Use `Object.seal()` when you want to prevent structural changes but allow value changes
- Remember that `freeze()` and `seal()` are shallow operations
- Implement deep freeze for nested objects when needed
- Use these methods for configuration objects and constants
- Consider performance implications with large objects
- Combine with `Object.isFrozen()` and `Object.isSealed()` for runtime checks

### 41. What are JavaScript iterators and iterables?
**Answer:**
Iterators are objects that define a sequence and return value on each call. Iterables are objects that can be iterated over.

**Detailed Explanation:**
Iterators and iterables are fundamental concepts in JavaScript that enable custom iteration behavior. They form the foundation for the `for...of` loop and many built-in methods like `Array.from()`, spread operator, and destructuring.

**Iterator Protocol:**

1. **Basic Iterator Implementation:**
```javascript
// Simple iterator
function createIterator(items) {
    let index = 0;
    
    return {
        next() {
            if (index < items.length) {
                return {
                    value: items[index++],
                    done: false
                };
            } else {
                return {
                    done: true
                };
            }
        }
    };
}

const iterator = createIterator([1, 2, 3]);
console.log(iterator.next()); // { value: 1, done: false }
console.log(iterator.next()); // { value: 2, done: false }
console.log(iterator.next()); // { value: 3, done: false }
console.log(iterator.next()); // { done: true }
```

2. **Iterable Protocol:**
```javascript
// Custom iterable object
const myIterable = {
    items: ['a', 'b', 'c'],
    
    [Symbol.iterator]() {
        let index = 0;
        const items = this.items;
        
        return {
            next() {
                if (index < items.length) {
                    return {
                        value: items[index++],
                        done: false
                    };
                } else {
                    return { done: true };
                }
            }
        };
    }
};

// Now it can be used with for...of
for (const item of myIterable) {
    console.log(item); // 'a', 'b', 'c'
}

// And with spread operator
console.log([...myIterable]); // ['a', 'b', 'c']
```

**Advanced Iterator Examples:**

3. **Range Iterator:**
```javascript
class Range {
    constructor(start, end, step = 1) {
        this.start = start;
        this.end = end;
        this.step = step;
    }
    
    [Symbol.iterator]() {
        let current = this.start;
        const end = this.end;
        const step = this.step;
        
        return {
            next() {
                if (current < end) {
                    const value = current;
                    current += step;
                    return { value, done: false };
                } else {
                    return { done: true };
                }
            }
        };
    }
}

const range = new Range(1, 10, 2);
console.log([...range]); // [1, 3, 5, 7, 9]

for (const num of range) {
    console.log(num); // 1, 3, 5, 7, 9
}
```

4. **Fibonacci Iterator:**
```javascript
class Fibonacci {
    constructor(max = Infinity) {
        this.max = max;
    }
    
    [Symbol.iterator]() {
        let prev = 0;
        let curr = 1;
        const max = this.max;
        
        return {
            next() {
                if (curr <= max) {
                    const value = curr;
                    const next = prev + curr;
                    prev = curr;
                    curr = next;
                    return { value, done: false };
                } else {
                    return { done: true };
                }
            }
        };
    }
}

const fib = new Fibonacci(100);
console.log([...fib]); // [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
```

**Generator Functions as Iterators:**

5. **Using Generators:**
```javascript
function* numberGenerator(start, end) {
    for (let i = start; i <= end; i++) {
        yield i;
    }
}

const numbers = numberGenerator(1, 5);
console.log([...numbers]); // [1, 2, 3, 4, 5]

// Generator with custom logic
function* fibonacci(max = Infinity) {
    let prev = 0;
    let curr = 1;
    
    while (curr <= max) {
        yield curr;
        const next = prev + curr;
        prev = curr;
        curr = next;
    }
}

const fib = fibonacci(50);
console.log([...fib]); // [1, 1, 2, 3, 5, 8, 13, 21, 34]
```

**Built-in Iterables:**

6. **Array Iteration:**
```javascript
const arr = [1, 2, 3, 4, 5];
const iterator = arr[Symbol.iterator]();

console.log(iterator.next()); // { value: 1, done: false }
console.log(iterator.next()); // { value: 2, done: false }

// Using for...of
for (const item of arr) {
    console.log(item); // 1, 2, 3, 4, 5
}
```

7. **String Iteration:**
```javascript
const str = 'hello';
const iterator = str[Symbol.iterator]();

console.log([...str]); // ['h', 'e', 'l', 'l', 'o']

for (const char of str) {
    console.log(char); // 'h', 'e', 'l', 'l', 'o'
}
```

**Custom Data Structure with Iteration:**

8. **Linked List Iterator:**
```javascript
class Node {
    constructor(value, next = null) {
        this.value = value;
        this.next = next;
    }
}

class LinkedList {
    constructor() {
        this.head = null;
        this.size = 0;
    }
    
    add(value) {
        const node = new Node(value, this.head);
        this.head = node;
        this.size++;
    }
    
    [Symbol.iterator]() {
        let current = this.head;
        
        return {
            next() {
                if (current) {
                    const value = current.value;
                    current = current.next;
                    return { value, done: false };
                } else {
                    return { done: true };
                }
            }
        };
    }
}

const list = new LinkedList();
list.add(3);
list.add(2);
list.add(1);

console.log([...list]); // [1, 2, 3]
```

**Iterator Methods:**

9. **Custom Iterator Methods:**
```javascript
class Collection {
    constructor(items = []) {
        this.items = items;
    }
    
    add(item) {
        this.items.push(item);
    }
    
    [Symbol.iterator]() {
        let index = 0;
        const items = this.items;
        
        return {
            next() {
                if (index < items.length) {
                    return {
                        value: items[index++],
                        done: false
                    };
                } else {
                    return { done: true };
                }
            },
            
            // Optional: return method for cleanup
            return() {
                console.log('Iterator cleanup');
                return { done: true };
            }
        };
    }
}

const collection = new Collection([1, 2, 3]);

// Using with for...of
for (const item of collection) {
    console.log(item);
    if (item === 2) break; // Triggers return() method
}
```

**Advanced Patterns:**

10. **Async Iterators:**
```javascript
class AsyncDataProvider {
    constructor(data) {
        this.data = data;
    }
    
    async [Symbol.asyncIterator]() {
        let index = 0;
        const data = this.data;
        
        return {
            async next() {
                if (index < data.length) {
                    // Simulate async operation
                    await new Promise(resolve => setTimeout(resolve, 100));
                    return {
                        value: data[index++],
                        done: false
                    };
                } else {
                    return { done: true };
                }
            }
        };
    }
}

const asyncProvider = new AsyncDataProvider([1, 2, 3, 4, 5]);

// Using with for await...of
(async () => {
    for await (const item of asyncProvider) {
        console.log(item); // 1, 2, 3, 4, 5 (with delays)
    }
})();
```

**Best Practices:**
- Use `Symbol.iterator` for custom iterables
- Implement proper cleanup in iterator methods
- Consider performance implications for large datasets
- Use generators for complex iteration logic
- Handle edge cases in iterator implementations
- Use async iterators for asynchronous data sources
- Test iterator behavior thoroughly

### 42. What is the difference between for-in and for-of loops?
**Answer:**
- `for-in`: Iterates over object keys
- `for-of`: Iterates over iterable values

**Detailed Explanation:**
Both `for...in` and `for...of` are iteration constructs in JavaScript, but they serve different purposes and work with different types of data structures. Understanding their differences is crucial for effective JavaScript programming.

**for...in Loop:**

1. **Basic Object Iteration:**
```javascript
const person = {
    name: 'John',
    age: 30,
    city: 'New York'
};

for (const key in person) {
    console.log(key, person[key]);
}
// Output:
// name John
// age 30
// city New York
```

2. **Array Iteration (Not Recommended):**
```javascript
const arr = ['a', 'b', 'c'];

for (const index in arr) {
    console.log(index, arr[index]);
}
// Output:
// 0 a
// 1 b
// 2 c

// Problem: includes inherited properties
Array.prototype.customMethod = function() {};
for (const index in arr) {
    console.log(index); // 0, 1, 2, customMethod
}
```

3. **Safe Object Iteration:**
```javascript
const obj = {
    name: 'John',
    age: 30,
    city: 'New York'
};

// Add a method to prototype
Object.prototype.toString = function() { return 'object'; };

// Unsafe iteration (includes inherited properties)
console.log('Unsafe:');
for (const key in obj) {
    console.log(key); // name, age, city, toString
}

// Safe iteration (only own properties)
console.log('Safe:');
for (const key in obj) {
    if (obj.hasOwnProperty(key)) {
        console.log(key); // name, age, city
    }
}

// Modern safe iteration
console.log('Modern safe:');
for (const key in obj) {
    if (Object.prototype.hasOwnProperty.call(obj, key)) {
        console.log(key); // name, age, city
    }
}
```

**for...of Loop:**

4. **Array Iteration:**
```javascript
const arr = ['a', 'b', 'c'];

for (const value of arr) {
    console.log(value);
}
// Output: a, b, c

// Works with any iterable
const set = new Set([1, 2, 3]);
for (const value of set) {
    console.log(value); // 1, 2, 3
}
```

5. **String Iteration:**
```javascript
const str = 'hello';

for (const char of str) {
    console.log(char);
}
// Output: h, e, l, l, o
```

6. **Map Iteration:**
```javascript
const map = new Map([
    ['name', 'John'],
    ['age', 30],
    ['city', 'New York']
]);

for (const [key, value] of map) {
    console.log(key, value);
}
// Output:
// name John
// age 30
// city New York
```

**Key Differences:**

7. **Performance Comparison:**
```javascript
const arr = new Array(1000000).fill(0).map((_, i) => i);

// for...of (faster for arrays)
console.time('for...of');
let sum1 = 0;
for (const value of arr) {
    sum1 += value;
}
console.timeEnd('for...of');

// for...in (slower for arrays)
console.time('for...in');
let sum2 = 0;
for (const index in arr) {
    sum2 += arr[index];
}
console.timeEnd('for...in');

// Traditional for loop (fastest)
console.time('for loop');
let sum3 = 0;
for (let i = 0; i < arr.length; i++) {
    sum3 += arr[i];
}
console.timeEnd('for loop');
```

8. **Object vs Iterable:**
```javascript
// Object (not iterable by default)
const obj = { a: 1, b: 2, c: 3 };

// for...in works
for (const key in obj) {
    console.log(key); // a, b, c
}

// for...of doesn't work (TypeError)
try {
    for (const value of obj) {
        console.log(value);
    }
} catch (error) {
    console.log('Error:', error.message); // obj is not iterable
}

// Make object iterable
obj[Symbol.iterator] = function* () {
    for (const key in this) {
        yield this[key];
    }
};

// Now for...of works
for (const value of obj) {
    console.log(value); // 1, 2, 3
}
```

**Practical Use Cases:**

9. **Object Processing:**
```javascript
const user = {
    name: 'John',
    email: 'john@example.com',
    age: 30,
    city: 'New York'
};

// Process object properties
const processedUser = {};
for (const key in user) {
    if (user.hasOwnProperty(key)) {
        processedUser[key] = user[key].toString().toUpperCase();
    }
}
console.log(processedUser);
// { name: 'JOHN', email: 'JOHN@EXAMPLE.COM', age: '30', city: 'NEW YORK' }
```

10. **Array Processing:**
```javascript
const numbers = [1, 2, 3, 4, 5];

// Using for...of (recommended)
let sum = 0;
for (const num of numbers) {
    sum += num;
}
console.log(sum); // 15

// Using for...in (not recommended for arrays)
let sum2 = 0;
for (const index in numbers) {
    sum2 += numbers[index];
}
console.log(sum2); // 15
```

**Advanced Examples:**

11. **Custom Iterable with for...of:**
```javascript
class NumberRange {
    constructor(start, end) {
        this.start = start;
        this.end = end;
    }
    
    [Symbol.iterator]() {
        let current = this.start;
        const end = this.end;
        
        return {
            next() {
                if (current <= end) {
                    return { value: current++, done: false };
                } else {
                    return { done: true };
                }
            }
        };
    }
}

const range = new NumberRange(1, 5);
for (const num of range) {
    console.log(num); // 1, 2, 3, 4, 5
}
```

12. **NodeList Iteration:**
```javascript
// HTML elements (in browser)
const elements = document.querySelectorAll('.item');

// for...of works with NodeList
for (const element of elements) {
    console.log(element.textContent);
}

// for...in would give indices, not elements
for (const index in elements) {
    console.log(index, elements[index]); // 0 [object HTMLElement], 1 [object HTMLElement]
}
```

**Best Practices:**

13. **When to Use Each:**
```javascript
// Use for...in for objects
const obj = { a: 1, b: 2, c: 3 };
for (const key in obj) {
    if (obj.hasOwnProperty(key)) {
        console.log(key, obj[key]);
    }
}

// Use for...of for arrays and iterables
const arr = [1, 2, 3, 4, 5];
for (const value of arr) {
    console.log(value);
}

// Use for...of for strings
const str = 'hello';
for (const char of str) {
    console.log(char);
}

// Use for...of for Sets and Maps
const set = new Set([1, 2, 3]);
for (const value of set) {
    console.log(value);
}

const map = new Map([['a', 1], ['b', 2]]);
for (const [key, value] of map) {
    console.log(key, value);
}
```

**Summary:**
- **for...in**: Use for object properties, returns keys, includes inherited properties
- **for...of**: Use for iterables (arrays, strings, Sets, Maps), returns values, only iterates over values
- **Performance**: for...of is generally faster for arrays
- **Safety**: Always check hasOwnProperty() with for...in
- **Modern**: Prefer for...of for most iteration needs

### 43. What are JavaScript symbols and how do you use them?
**Answer:**
Symbols are unique identifiers used as object property keys to avoid naming conflicts.

**Detailed Explanation:**
Symbols are a primitive data type introduced in ES6 that provide a way to create unique identifiers. They are guaranteed to be unique and are primarily used as object property keys to avoid naming conflicts.

**Basic Symbol Usage:**

1. **Creating Symbols:**
```javascript
// Basic symbol creation
const sym1 = Symbol();
const sym2 = Symbol();
console.log(sym1 === sym2); // false (always unique)

// Symbols with descriptions
const sym3 = Symbol('description');
const sym4 = Symbol('description');
console.log(sym3 === sym4); // false (still unique)
console.log(sym3.toString()); // 'Symbol(description)'
```

2. **Using Symbols as Object Keys:**
```javascript
const id = Symbol('id');
const name = Symbol('name');

const person = {
    [id]: 123,
    [name]: 'John',
    age: 30
};

console.log(person[id]); // 123
console.log(person[name]); // 'John'
console.log(person.age); // 30

// Symbols don't appear in normal iteration
for (const key in person) {
    console.log(key); // only 'age'
}

console.log(Object.keys(person)); // ['age']
console.log(Object.getOwnPropertySymbols(person)); // [Symbol(id), Symbol(name)]
```

**Well-Known Symbols:**

3. **Symbol.iterator:**
```javascript
class NumberRange {
    constructor(start, end) {
        this.start = start;
        this.end = end;
    }
    
    [Symbol.iterator]() {
        let current = this.start;
        const end = this.end;
        
        return {
            next() {
                if (current <= end) {
                    return { value: current++, done: false };
                } else {
                    return { done: true };
                }
            }
        };
    }
}

const range = new NumberRange(1, 5);
console.log([...range]); // [1, 2, 3, 4, 5]
```

4. **Symbol.toPrimitive:**
```javascript
class Temperature {
    constructor(celsius) {
        this.celsius = celsius;
    }
    
    [Symbol.toPrimitive](hint) {
        if (hint === 'number') {
            return this.celsius;
        } else if (hint === 'string') {
            return `${this.celsius}°C`;
        } else {
            return this.celsius;
        }
    }
}

const temp = new Temperature(25);
console.log(+temp); // 25 (number conversion)
console.log(String(temp)); // '25°C' (string conversion)
console.log(temp + 5); // 30 (number conversion)
```

5. **Symbol.toStringTag:**
```javascript
class CustomArray {
    constructor(...items) {
        this.items = items;
    }
    
    get [Symbol.toStringTag]() {
        return 'CustomArray';
    }
    
    [Symbol.iterator]() {
        return this.items[Symbol.iterator]();
    }
}

const customArr = new CustomArray(1, 2, 3);
console.log(Object.prototype.toString.call(customArr)); // '[object CustomArray]'
console.log([...customArr]); // [1, 2, 3]
```

**Symbol Registry:**

6. **Global Symbol Registry:**
```javascript
// Creating symbols in global registry
const sym1 = Symbol.for('mySymbol');
const sym2 = Symbol.for('mySymbol');
console.log(sym1 === sym2); // true (same symbol)

// Getting symbol from registry
const sym3 = Symbol.keyFor(sym1);
console.log(sym3); // 'mySymbol'

// Symbol not in registry
const sym4 = Symbol('notInRegistry');
console.log(Symbol.keyFor(sym4)); // undefined
```

**Advanced Symbol Usage:**

7. **Private Properties with Symbols:**
```javascript
const _private = Symbol('private');
const _secret = Symbol('secret');

class BankAccount {
    constructor(initialBalance) {
        this[_private] = initialBalance;
        this[_secret] = 'secretKey';
        this.publicInfo = 'This is public';
    }
    
    getBalance() {
        return this[_private];
    }
    
    deposit(amount) {
        this[_private] += amount;
    }
    
    getSecret() {
        return this[_secret];
    }
}

const account = new BankAccount(1000);
console.log(account.getBalance()); // 1000
console.log(account.publicInfo); // 'This is public'

// Private properties are not accessible without the symbol
console.log(account[_private]); // undefined (symbol not accessible)
console.log(Object.keys(account)); // ['publicInfo']
```

8. **Symbol-based Enumeration:**
```javascript
const Status = {
    PENDING: Symbol('PENDING'),
    APPROVED: Symbol('APPROVED'),
    REJECTED: Symbol('REJECTED')
};

class Application {
    constructor() {
        this.status = Status.PENDING;
    }
    
    approve() {
        this.status = Status.APPROVED;
    }
    
    reject() {
        this.status = Status.REJECTED;
    }
    
    isPending() {
        return this.status === Status.PENDING;
    }
}

const app = new Application();
console.log(app.isPending()); // true
app.approve();
console.log(app.status === Status.APPROVED); // true
```

**Symbol Methods:**

9. **Symbol Methods and Properties:**
```javascript
const sym = Symbol('test');

// Symbol properties
console.log(sym.description); // 'test'
console.log(sym.toString()); // 'Symbol(test)'
console.log(sym.valueOf()); // Symbol(test)

// Type checking
console.log(typeof sym); // 'symbol'
console.log(sym instanceof Symbol); // false (Symbols are primitives)
```

10. **Symbol-based Mixins:**
```javascript
const mixinSymbol = Symbol('mixin');

function withLogging(target) {
    target[mixinSymbol] = {
        log(message) {
            console.log(`[${target.constructor.name}] ${message}`);
        }
    };
    return target;
}

class User {
    constructor(name) {
        this.name = name;
    }
}

const LoggedUser = withLogging(User);
const user = new LoggedUser('John');
user[mixinSymbol].log('User created'); // '[User] User created'
```

**Symbol Iteration:**

11. **Iterating Over Symbol Properties:**
```javascript
const obj = {
    name: 'John',
    age: 30
};

const sym1 = Symbol('id');
const sym2 = Symbol('secret');

obj[sym1] = 123;
obj[sym2] = 'secretValue';

// Get all symbol properties
const symbols = Object.getOwnPropertySymbols(obj);
console.log(symbols); // [Symbol(id), Symbol(secret)]

// Get all properties (including symbols)
const allProps = Reflect.ownKeys(obj);
console.log(allProps); // ['name', 'age', Symbol(id), Symbol(secret)]

// Iterate over symbol properties
symbols.forEach(sym => {
    console.log(sym.toString(), obj[sym]);
});
```

**Practical Use Cases:**

12. **Event System with Symbols:**
```javascript
const EVENT_SYMBOL = Symbol('events');

class EventEmitter {
    constructor() {
        this[EVENT_SYMBOL] = new Map();
    }
    
    on(event, callback) {
        if (!this[EVENT_SYMBOL].has(event)) {
            this[EVENT_SYMBOL].set(event, []);
        }
        this[EVENT_SYMBOL].get(event).push(callback);
    }
    
    emit(event, data) {
        if (this[EVENT_SYMBOL].has(event)) {
            this[EVENT_SYMBOL].get(event).forEach(callback => callback(data));
        }
    }
}

const emitter = new EventEmitter();
emitter.on('test', data => console.log('Received:', data));
emitter.emit('test', 'Hello World'); // 'Received: Hello World'
```

13. **Symbol-based Plugin System:**
```javascript
const PLUGIN_SYMBOL = Symbol('plugin');

class PluginManager {
    constructor() {
        this[PLUGIN_SYMBOL] = new Map();
    }
    
    register(name, plugin) {
        this[PLUGIN_SYMBOL].set(name, plugin);
    }
    
    get(name) {
        return this[PLUGIN_SYMBOL].get(name);
    }
    
    list() {
        return Array.from(this[PLUGIN_SYMBOL].keys());
    }
}

const manager = new PluginManager();
manager.register('logger', { log: msg => console.log(msg) });
manager.register('validator', { validate: data => !!data });

console.log(manager.list()); // ['logger', 'validator']
manager.get('logger').log('Hello'); // 'Hello'
```

**Best Practices:**
- Use symbols for truly private properties
- Use Symbol.for() for global symbols that need to be shared
- Use well-known symbols for custom behavior
- Prefer symbols over string keys for internal properties
- Use symbols to avoid naming conflicts in libraries
- Consider performance implications of symbol property access
- Use Object.getOwnPropertySymbols() to access symbol properties

### 44. What is the difference between Object.keys(), Object.values(), and Object.entries()?
**Answer:**
- `Object.keys()`: Returns array of object keys
- `Object.values()`: Returns array of object values
- `Object.entries()`: Returns array of key-value pairs

**Detailed Explanation:**
These three methods are essential for working with objects in JavaScript. They provide different ways to extract information from objects, each serving specific use cases in object manipulation and iteration.

**Object.keys() - Getting Object Keys:**

1. **Basic Usage:**
```javascript
const person = {
    name: 'John',
    age: 30,
    city: 'New York',
    occupation: 'Developer'
};

const keys = Object.keys(person);
console.log(keys); // ['name', 'age', 'city', 'occupation']
```

2. **Iterating Over Keys:**
```javascript
const config = {
    apiUrl: 'https://api.example.com',
    timeout: 5000,
    retries: 3,
    timeout: 10000 // This overwrites the previous timeout
};

Object.keys(config).forEach(key => {
    console.log(`${key}: ${config[key]}`);
});
// Output:
// apiUrl: https://api.example.com
// timeout: 10000
// retries: 3
```

3. **Filtering Object Properties:**
```javascript
const user = {
    id: 1,
    name: 'John',
    email: 'john@example.com',
    password: 'secret123',
    age: 30,
    city: 'New York'
};

// Get only public properties (exclude sensitive data)
const publicKeys = Object.keys(user).filter(key => 
    !['password', 'id'].includes(key)
);

const publicUser = {};
publicKeys.forEach(key => {
    publicUser[key] = user[key];
});

console.log(publicUser); // { name: 'John', email: 'john@example.com', age: 30, city: 'New York' }
```

**Object.values() - Getting Object Values:**

4. **Basic Usage:**
```javascript
const scores = {
    math: 95,
    science: 87,
    english: 92,
    history: 78
};

const values = Object.values(scores);
console.log(values); // [95, 87, 92, 78]

// Calculate average score
const average = values.reduce((sum, score) => sum + score, 0) / values.length;
console.log(average); // 87.5
```

5. **Working with Values:**
```javascript
const inventory = {
    apples: 50,
    bananas: 30,
    oranges: 25,
    grapes: 40
};

// Find total items
const totalItems = Object.values(inventory).reduce((sum, count) => sum + count, 0);
console.log(totalItems); // 145

// Find items with low stock
const lowStock = Object.values(inventory).filter(count => count < 35);
console.log(lowStock); // [30, 25]
```

**Object.entries() - Getting Key-Value Pairs:**

6. **Basic Usage:**
```javascript
const person = {
    name: 'John',
    age: 30,
    city: 'New York'
};

const entries = Object.entries(person);
console.log(entries); // [['name', 'John'], ['age', 30], ['city', 'New York']]
```

7. **Iterating Over Entries:**
```javascript
const settings = {
    theme: 'dark',
    language: 'en',
    notifications: true,
    autoSave: false
};

Object.entries(settings).forEach(([key, value]) => {
    console.log(`${key}: ${value}`);
});
// Output:
// theme: dark
// language: en
// notifications: true
// autoSave: false
```

8. **Transforming Objects:**
```javascript
const data = {
    firstName: 'John',
    lastName: 'Doe',
    email: 'john@example.com'
};

// Transform to different format
const transformed = Object.entries(data).map(([key, value]) => ({
    field: key,
    value: value,
    type: typeof value
}));

console.log(transformed);
// [
//   { field: 'firstName', value: 'John', type: 'string' },
//   { field: 'lastName', value: 'Doe', type: 'string' },
//   { field: 'email', value: 'john@example.com', type: 'string' }
// ]
```

**Advanced Use Cases:**

9. **Object Manipulation:**
```javascript
const original = {
    a: 1,
    b: 2,
    c: 3
};

// Create new object with transformed values
const doubled = Object.fromEntries(
    Object.entries(original).map(([key, value]) => [key, value * 2])
);
console.log(doubled); // { a: 2, b: 4, c: 6 }

// Filter object properties
const filtered = Object.fromEntries(
    Object.entries(original).filter(([key, value]) => value > 1)
);
console.log(filtered); // { b: 2, c: 3 }
```

10. **Object Comparison:**
```javascript
function shallowEqual(obj1, obj2) {
    const keys1 = Object.keys(obj1);
    const keys2 = Object.keys(obj2);
    
    if (keys1.length !== keys2.length) {
        return false;
    }
    
    return keys1.every(key => obj1[key] === obj2[key]);
}

const obj1 = { a: 1, b: 2 };
const obj2 = { a: 1, b: 2 };
const obj3 = { a: 1, b: 3 };

console.log(shallowEqual(obj1, obj2)); // true
console.log(shallowEqual(obj1, obj3)); // false
```

11. **Object Validation:**
```javascript
function validateObject(obj, schema) {
    const errors = [];
    
    Object.entries(schema).forEach(([key, validator]) => {
        const value = obj[key];
        if (!validator(value)) {
            errors.push(`${key} is invalid`);
        }
    });
    
    return {
        isValid: errors.length === 0,
        errors
    };
}

const userSchema = {
    name: value => typeof value === 'string' && value.length > 0,
    age: value => typeof value === 'number' && value > 0,
    email: value => typeof value === 'string' && value.includes('@')
};

const user = { name: 'John', age: 30, email: 'john@example.com' };
const result = validateObject(user, userSchema);
console.log(result); // { isValid: true, errors: [] }
```

**Performance Considerations:**

12. **Performance Comparison:**
```javascript
const largeObject = {};
for (let i = 0; i < 10000; i++) {
    largeObject[`key${i}`] = i;
}

// Measure performance
console.time('Object.keys()');
const keys = Object.keys(largeObject);
console.timeEnd('Object.keys()');

console.time('Object.values()');
const values = Object.values(largeObject);
console.timeEnd('Object.values()');

console.time('Object.entries()');
const entries = Object.entries(largeObject);
console.timeEnd('Object.entries()');
```

**Practical Examples:**

13. **API Response Processing:**
```javascript
const apiResponse = {
    status: 'success',
    data: {
        users: [
            { id: 1, name: 'John', email: 'john@example.com' },
            { id: 2, name: 'Jane', email: 'jane@example.com' }
        ],
        pagination: {
            page: 1,
            total: 2
        }
    },
    timestamp: '2023-12-01T10:00:00Z'
};

// Extract all keys for debugging
const allKeys = Object.keys(apiResponse);
console.log('Response keys:', allKeys); // ['status', 'data', 'timestamp']

// Extract all values for analysis
const allValues = Object.values(apiResponse);
console.log('Response values:', allValues);

// Process key-value pairs
Object.entries(apiResponse).forEach(([key, value]) => {
    console.log(`${key}: ${typeof value}`);
});
```

14. **Object Cloning and Merging:**
```javascript
function mergeObjects(...objects) {
    const result = {};
    
    objects.forEach(obj => {
        Object.entries(obj).forEach(([key, value]) => {
            result[key] = value;
        });
    });
    
    return result;
}

const obj1 = { a: 1, b: 2 };
const obj2 = { b: 3, c: 4 };
const obj3 = { d: 5 };

const merged = mergeObjects(obj1, obj2, obj3);
console.log(merged); // { a: 1, b: 3, c: 4, d: 5 }
```

**Best Practices:**
- Use `Object.keys()` for iterating over object properties
- Use `Object.values()` for working with object values
- Use `Object.entries()` for transforming objects
- Consider performance with large objects
- Use these methods for object validation and manipulation
- Combine with array methods for powerful transformations
- Use `Object.fromEntries()` to convert back to objects

### 45. What are JavaScript regular expressions?
**Answer:**
Patterns used to match character combinations in strings, created with `/pattern/flags` or `new RegExp()`.

**Detailed Explanation:**
Regular expressions (regex) are powerful patterns used to match, search, and manipulate text. They provide a concise way to describe complex string patterns and are essential for text processing, validation, and data extraction.

**Basic Syntax:**

1. **Creating Regular Expressions:**
```javascript
// Literal syntax
const pattern1 = /hello/;
const pattern2 = /hello/i; // case insensitive

// Constructor syntax
const pattern3 = new RegExp('hello');
const pattern4 = new RegExp('hello', 'i');

// Dynamic patterns
const searchTerm = 'world';
const pattern5 = new RegExp(searchTerm, 'gi');
```

2. **Basic Matching:**
```javascript
const text = 'Hello World! Hello JavaScript!';
const pattern = /hello/i;

console.log(pattern.test(text)); // true
console.log(pattern.exec(text)); // ['Hello', index: 0, input: 'Hello World! Hello JavaScript!']
```

**Common Patterns:**

3. **Character Classes:**
```javascript
const text = 'The quick brown fox jumps over the lazy dog';

// Match any digit
const digitPattern = /\d/;
console.log(digitPattern.test('abc123')); // true

// Match any word character
const wordPattern = /\w/;
console.log(wordPattern.test('hello')); // true

// Match any whitespace
const spacePattern = /\s/;
console.log(spacePattern.test('hello world')); // true

// Match specific characters
const vowelPattern = /[aeiou]/i;
console.log(vowelPattern.test('hello')); // true
```

4. **Quantifiers:**
```javascript
const text = 'aaabbbccc';

// Match one or more
const oneOrMore = /a+/;
console.log(oneOrMore.test(text)); // true

// Match zero or more
const zeroOrMore = /a*/;
console.log(zeroOrMore.test('')); // true

// Match exactly n times
const exactlyThree = /a{3}/;
console.log(exactlyThree.test(text)); // true

// Match between n and m times
const betweenTwoAndFour = /a{2,4}/;
console.log(betweenTwoAndFour.test(text)); // true
```

**Advanced Patterns:**

5. **Groups and Capturing:**
```javascript
const text = 'John Doe, Jane Smith, Bob Johnson';

// Capture groups
const namePattern = /(\w+)\s+(\w+)/g;
let match;
while ((match = namePattern.exec(text)) !== null) {
    console.log(`First: ${match[1]}, Last: ${match[2]}`);
}
// Output:
// First: John, Last: Doe
// First: Jane, Last: Smith
// First: Bob, Last: Johnson
```

6. **Non-capturing Groups:**
```javascript
const text = 'color: red; background: blue; border: green';

// Non-capturing group
const colorPattern = /(?:color|background):\s*(\w+)/g;
let match;
while ((match = colorPattern.exec(text)) !== null) {
    console.log(match[1]); // red, blue
}
```

7. **Lookahead and Lookbehind:**
```javascript
const text = 'password123 secret456 token789';

// Positive lookahead
const passwordPattern = /\w+(?=\d{3})/g;
console.log(text.match(passwordPattern)); // ['password', 'secret', 'token']

// Negative lookahead
const nonPasswordPattern = /\w+(?!\d{3})/g;
console.log(text.match(nonPasswordPattern)); // ['password123', 'secret456', 'token789']
```

**String Methods with Regex:**

8. **String Methods:**
```javascript
const text = 'Hello World! Hello JavaScript!';

// search() - returns index or -1
console.log(text.search(/world/i)); // 6

// match() - returns array or null
console.log(text.match(/hello/gi)); // ['Hello', 'Hello']

// replace() - replaces matches
console.log(text.replace(/hello/gi, 'Hi')); // 'Hi World! Hi JavaScript!'

// split() - splits on pattern
console.log('a,b,c'.split(/,/)); // ['a', 'b', 'c']
```

**Practical Examples:**

9. **Email Validation:**
```javascript
function validateEmail(email) {
    const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return emailPattern.test(email);
}

console.log(validateEmail('user@example.com')); // true
console.log(validateEmail('invalid-email')); // false
```

10. **Phone Number Validation:**
```javascript
function validatePhone(phone) {
    const phonePattern = /^\+?1?\s?(\(\d{3}\)|\d{3})[-.\s]?\d{3}[-.\s]?\d{4}$/;
    return phonePattern.test(phone);
}

console.log(validatePhone('(555) 123-4567')); // true
console.log(validatePhone('555-123-4567')); // true
console.log(validatePhone('555.123.4567')); // true
```

11. **URL Parsing:**
```javascript
function parseURL(url) {
    const urlPattern = /^(https?:\/\/)?([^\/]+)(\/.*)?$/;
    const match = url.match(urlPattern);
    
    if (match) {
        return {
            protocol: match[1] || 'https:',
            domain: match[2],
            path: match[3] || '/'
        };
    }
    return null;
}

console.log(parseURL('https://example.com/path'));
// { protocol: 'https:', domain: 'example.com', path: '/path' }
```

12. **Text Processing:**
```javascript
function extractNumbers(text) {
    const numberPattern = /\d+/g;
    return text.match(numberPattern) || [];
}

console.log(extractNumbers('I have 5 apples and 3 oranges')); // ['5', '3']

function extractWords(text) {
    const wordPattern = /\b\w+\b/g;
    return text.match(wordPattern) || [];
}

console.log(extractWords('Hello, world! How are you?')); // ['Hello', 'world', 'How', 'are', 'you']
```

**Advanced Techniques:**

13. **Named Groups (ES2018):**
```javascript
const text = 'John Doe, 30, john@example.com';
const personPattern = /(?<name>\w+\s+\w+),\s*(?<age>\d+),\s*(?<email>[^\s]+)/;
const match = text.match(personPattern);

if (match) {
    console.log(match.groups); // { name: 'John Doe', age: '30', email: 'john@example.com' }
}
```

14. **Unicode Support:**
```javascript
const text = 'Hello 世界 🌍';

// Match Unicode characters
const unicodePattern = /[\u4e00-\u9fff]/g;
console.log(text.match(unicodePattern)); // ['世', '界']

// Match emojis
const emojiPattern = /[\u{1F600}-\u{1F64F}]/gu;
console.log(text.match(emojiPattern)); // ['🌍']
```

15. **Performance Optimization:**
```javascript
// Compile regex once for better performance
const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

function validateEmails(emails) {
    return emails.filter(email => emailPattern.test(email));
}

const emails = ['user@example.com', 'invalid', 'test@domain.org'];
console.log(validateEmails(emails)); // ['user@example.com', 'test@domain.org']
```

**Common Regex Patterns:**

16. **Useful Patterns:**
```javascript
// Common patterns
const patterns = {
    // Email
    email: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
    
    // URL
    url: /^https?:\/\/\S+$/,
    
    // Phone (US)
    phone: /^\+?1?\s?(\(\d{3}\)|\d{3})[-.\s]?\d{3}[-.\s]?\d{4}$/,
    
    // Credit card
    creditCard: /^\d{4}[\s-]?\d{4}[\s-]?\d{4}[\s-]?\d{4}$/,
    
    // Password (8+ chars, at least one letter and one number)
    password: /^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d@$!%*#?&]{8,}$/,
    
    // IPv4 address
    ipv4: /^(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$/,
    
    // HTML tags
    htmlTags: /<[^>]+>/g,
    
    // Numbers
    numbers: /\d+/g,
    
    // Words
    words: /\b\w+\b/g
};

// Test patterns
console.log(patterns.email.test('user@example.com')); // true
console.log(patterns.phone.test('(555) 123-4567')); // true
console.log(patterns.password.test('Password123')); // true
```

**Best Practices:**
- Use literal syntax for static patterns
- Use constructor syntax for dynamic patterns
- Test regex patterns thoroughly
- Consider performance with large texts
- Use appropriate flags (i, g, m, u)
- Escape special characters when needed
- Use online regex testers for complex patterns
- Document complex regex patterns
- Consider using libraries for complex validation

### 46. What is the difference between setTimeout and setInterval?
**Answer:**
- `setTimeout()`: Executes function once after delay
- `setInterval()`: Executes function repeatedly at intervals

**Detailed Explanation:**
Both `setTimeout` and `setInterval` are JavaScript timing functions that allow you to execute code asynchronously after a specified delay. They are essential for creating time-based functionality, animations, and asynchronous operations.

**setTimeout() - One-time Execution:**

1. **Basic Usage:**
```javascript
// Execute function after 2 seconds
setTimeout(() => {
    console.log('Hello after 2 seconds!');
}, 2000);

// Execute function with parameters
setTimeout((name, age) => {
    console.log(`Hello ${name}, you are ${age} years old!`);
}, 1000, 'John', 30);
```

2. **Return Value and Clearing:**
```javascript
// setTimeout returns a timer ID
const timerId = setTimeout(() => {
    console.log('This will not execute');
}, 5000);

// Clear the timeout before it executes
clearTimeout(timerId);
console.log('Timeout cleared');
```

3. **Practical Examples:**
```javascript
// Debouncing function
function debounce(func, delay) {
    let timeoutId;
    return function(...args) {
        clearTimeout(timeoutId);
        timeoutId = setTimeout(() => func.apply(this, args), delay);
    };
}

const debouncedSearch = debounce((query) => {
    console.log('Searching for:', query);
}, 300);

// Simulate user typing
setTimeout(() => debouncedSearch('a'), 100);
setTimeout(() => debouncedSearch('ab'), 200);
setTimeout(() => debouncedSearch('abc'), 300);
// Only 'abc' will be searched after 300ms delay
```

**setInterval() - Repeated Execution:**

4. **Basic Usage:**
```javascript
// Execute function every 1 second
const intervalId = setInterval(() => {
    console.log('Tick tock!');
}, 1000);

// Stop after 5 seconds
setTimeout(() => {
    clearInterval(intervalId);
    console.log('Interval stopped');
}, 5000);
```

5. **Clock Implementation:**
```javascript
function startClock() {
    const clockElement = document.getElementById('clock');
    
    const intervalId = setInterval(() => {
        const now = new Date();
        clockElement.textContent = now.toLocaleTimeString();
    }, 1000);
    
    // Return function to stop clock
    return () => clearInterval(intervalId);
}

// Start clock
const stopClock = startClock();

// Stop clock after 10 seconds
setTimeout(stopClock, 10000);
```

**Advanced Patterns:**

6. **Recursive setTimeout vs setInterval:**
```javascript
// Using setInterval (can drift)
let count1 = 0;
const intervalId = setInterval(() => {
    count1++;
    console.log(`Interval count: ${count1}`);
    if (count1 >= 5) {
        clearInterval(intervalId);
    }
}, 1000);

// Using recursive setTimeout (more accurate)
let count2 = 0;
function recursiveTimeout() {
    count2++;
    console.log(`Timeout count: ${count2}`);
    if (count2 < 5) {
        setTimeout(recursiveTimeout, 1000);
    }
}

setTimeout(recursiveTimeout, 1000);
```

7. **Animation with setTimeout:**
```javascript
function animateElement(element, start, end, duration) {
    const startTime = performance.now();
    
    function animate(currentTime) {
        const elapsed = currentTime - startTime;
        const progress = Math.min(elapsed / duration, 1);
        
        // Easing function (ease-out)
        const easeOut = 1 - Math.pow(1 - progress, 3);
        const current = start + (end - start) * easeOut;
        
        element.style.left = current + 'px';
        
        if (progress < 1) {
            requestAnimationFrame(animate);
        }
    }
    
    requestAnimationFrame(animate);
}

// Usage
const element = document.getElementById('animated');
animateElement(element, 0, 300, 1000);
```

**Error Handling and Best Practices:**

8. **Error Handling:**
```javascript
function safeTimeout(callback, delay, ...args) {
    const timeoutId = setTimeout(() => {
        try {
            callback(...args);
        } catch (error) {
            console.error('Error in timeout callback:', error);
        }
    }, delay);
    
    return timeoutId;
}

// Usage
safeTimeout((x, y) => {
    console.log(x + y);
    throw new Error('Something went wrong!');
}, 1000, 5, 3);
```

9. **Memory Management:**
```javascript
class TimerManager {
    constructor() {
        this.timers = new Set();
    }
    
    setTimeout(callback, delay, ...args) {
        const timeoutId = setTimeout(() => {
            this.timers.delete(timeoutId);
            callback(...args);
        }, delay);
        
        this.timers.add(timeoutId);
        return timeoutId;
    }
    
    setInterval(callback, interval, ...args) {
        const intervalId = setInterval(callback, interval, ...args);
        this.timers.add(intervalId);
        return intervalId;
    }
    
    clearTimeout(timeoutId) {
        clearTimeout(timeoutId);
        this.timers.delete(timeoutId);
    }
    
    clearInterval(intervalId) {
        clearInterval(intervalId);
        this.timers.delete(intervalId);
    }
    
    clearAll() {
        this.timers.forEach(id => {
            clearTimeout(id);
            clearInterval(id);
        });
        this.timers.clear();
    }
}

const timerManager = new TimerManager();

// Use timers
const timeoutId = timerManager.setTimeout(() => console.log('Timeout!'), 1000);
const intervalId = timerManager.setInterval(() => console.log('Interval!'), 2000);

// Clear all timers
setTimeout(() => timerManager.clearAll(), 5000);
```

**Performance Considerations:**

10. **Performance Optimization:**
```javascript
// Throttling function
function throttle(func, limit) {
    let inThrottle;
    return function(...args) {
        if (!inThrottle) {
            func.apply(this, args);
            inThrottle = true;
            setTimeout(() => inThrottle = false, limit);
        }
    };
}

// Usage
const throttledScroll = throttle(() => {
    console.log('Scroll event handled');
}, 100);

window.addEventListener('scroll', throttledScroll);
```

11. **Request Animation Frame Alternative:**
```javascript
function smoothAnimation(element, property, start, end, duration) {
    const startTime = performance.now();
    
    function animate(currentTime) {
        const elapsed = currentTime - startTime;
        const progress = Math.min(elapsed / duration, 1);
        
        const current = start + (end - start) * progress;
        element.style[property] = current + 'px';
        
        if (progress < 1) {
            requestAnimationFrame(animate);
        }
    }
    
    requestAnimationFrame(animate);
}

// Usage
const element = document.getElementById('box');
smoothAnimation(element, 'left', 0, 300, 1000);
```

**Common Use Cases:**

12. **Polling:**
```javascript
function pollServer(url, callback, interval = 5000) {
    const poll = async () => {
        try {
            const response = await fetch(url);
            const data = await response.json();
            callback(data);
        } catch (error) {
            console.error('Polling error:', error);
        }
    };
    
    // Initial poll
    poll();
    
    // Set up interval
    return setInterval(poll, interval);
}

// Usage
const pollId = pollServer('/api/status', (data) => {
    console.log('Server status:', data);
}, 3000);

// Stop polling after 30 seconds
setTimeout(() => clearInterval(pollId), 30000);
```

13. **Retry Mechanism:**
```javascript
function retryWithBackoff(func, maxRetries = 3, baseDelay = 1000) {
    let retries = 0;
    
    function attempt() {
        func()
            .then(result => {
                console.log('Success:', result);
            })
            .catch(error => {
                if (retries < maxRetries) {
                    retries++;
                    const delay = baseDelay * Math.pow(2, retries - 1);
                    console.log(`Retry ${retries} in ${delay}ms`);
                    setTimeout(attempt, delay);
                } else {
                    console.error('Max retries exceeded:', error);
                }
            });
    }
    
    attempt();
}

// Usage
retryWithBackoff(() => {
    return fetch('/api/data')
        .then(response => response.json());
}, 3, 1000);
```

**Best Practices:**
- Use `setTimeout` for one-time delays
- Use `setInterval` for repeated operations
- Always clear timers when no longer needed
- Use `clearTimeout` and `clearInterval` to prevent memory leaks
- Consider using `requestAnimationFrame` for animations
- Use recursive `setTimeout` for more accurate timing
- Handle errors in timer callbacks
- Use debouncing and throttling for performance
- Consider using Web Workers for heavy computations
- Test timer behavior in different browsers

### 47. What are JavaScript error handling mechanisms?
**Answer:**
try-catch-finally blocks for handling errors and exceptions.

**Detailed Explanation:**
Error handling in JavaScript is crucial for building robust applications. JavaScript provides several mechanisms to handle errors gracefully, including try-catch blocks, error objects, and various error handling patterns.

**Basic Error Handling:**

1. **try-catch-finally Blocks:**
```javascript
function divideNumbers(a, b) {
    try {
        if (b === 0) {
            throw new Error('Division by zero is not allowed');
        }
        return a / b;
    } catch (error) {
        console.error('Error occurred:', error.message);
        return null;
    } finally {
        console.log('Division operation completed');
    }
}

console.log(divideNumbers(10, 2)); // 5
console.log(divideNumbers(10, 0)); // null
```

2. **Error Types:**
```javascript
// SyntaxError
try {
    eval('invalid syntax');
} catch (error) {
    console.log('SyntaxError:', error.message);
}

// TypeError
try {
    null.someMethod();
} catch (error) {
    console.log('TypeError:', error.message);
}

// ReferenceError
try {
    console.log(undefinedVariable);
} catch (error) {
    console.log('ReferenceError:', error.message);
}

// RangeError
try {
    new Array(-1);
} catch (error) {
    console.log('RangeError:', error.message);
}
```

**Custom Error Classes:**

3. **Creating Custom Errors:**
```javascript
class ValidationError extends Error {
    constructor(message, field) {
        super(message);
        this.name = 'ValidationError';
        this.field = field;
    }
}

class NetworkError extends Error {
    constructor(message, statusCode) {
        super(message);
        this.name = 'NetworkError';
        this.statusCode = statusCode;
    }
}

function validateUser(user) {
    if (!user.name) {
        throw new ValidationError('Name is required', 'name');
    }
    if (!user.email) {
        throw new ValidationError('Email is required', 'email');
    }
    if (!user.email.includes('@')) {
        throw new ValidationError('Invalid email format', 'email');
    }
    return true;
}

// Usage
try {
    validateUser({ name: '', email: 'invalid' });
} catch (error) {
    if (error instanceof ValidationError) {
        console.log(`Validation error in ${error.field}: ${error.message}`);
    }
}
```

**Async Error Handling:**

4. **Promise Error Handling:**
```javascript
function fetchUserData(userId) {
    return fetch(`/api/users/${userId}`)
        .then(response => {
            if (!response.ok) {
                throw new NetworkError(`HTTP ${response.status}`, response.status);
            }
            return response.json();
        })
        .catch(error => {
            console.error('Failed to fetch user data:', error);
            throw error;
        });
}

// Using with async/await
try {
    const userData = await fetchUserData(123);
    console.log('User data:', userData);
} catch (error) {
    if (error instanceof NetworkError) {
        console.log('Network error:', error.statusCode);
    } else {
        console.log('Unexpected error:', error.message);
    }
}
```

5. **Promise.all Error Handling:**
```javascript
async function fetchMultipleUsers(userIds) {
    try {
        const promises = userIds.map(id => fetchUserData(id));
        const users = await Promise.all(promises);
        return users;
    } catch (error) {
        console.error('Failed to fetch users:', error);
        return [];
    }
}

// Alternative: Promise.allSettled
async function fetchMultipleUsersSafe(userIds) {
    const promises = userIds.map(id => fetchUserData(id));
    const results = await Promise.allSettled(promises);
    
    const successful = results
        .filter(result => result.status === 'fulfilled')
        .map(result => result.value);
    
    const failed = results
        .filter(result => result.status === 'rejected')
        .map(result => result.reason);
    
    console.log('Successful:', successful.length);
    console.log('Failed:', failed.length);
    
    return successful;
}
```

**Global Error Handling:**

6. **Window Error Handler:**
```javascript
// Global error handler
window.addEventListener('error', (event) => {
    console.error('Global error:', event.error);
    
    // Send error to logging service
    logError(event.error, {
        filename: event.filename,
        lineno: event.lineno,
        colno: event.colno
    });
});

// Unhandled promise rejection handler
window.addEventListener('unhandledrejection', (event) => {
    console.error('Unhandled promise rejection:', event.reason);
    
    // Prevent default behavior
    event.preventDefault();
    
    // Log the error
    logError(event.reason);
});

function logError(error, context = {}) {
    // Send to logging service
    fetch('/api/logs', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
            error: error.message,
            stack: error.stack,
            context,
            timestamp: new Date().toISOString()
        })
    }).catch(console.error);
}
```

**Error Boundaries (React-style):**

7. **Error Boundary Implementation:**
```javascript
class ErrorBoundary {
    constructor() {
        this.error = null;
        this.errorInfo = null;
    }
    
    componentDidCatch(error, errorInfo) {
        this.error = error;
        this.errorInfo = errorInfo;
        
        // Log error
        console.error('Error boundary caught:', error, errorInfo);
    }
    
    render() {
        if (this.error) {
            return {
                type: 'div',
                props: {
                    className: 'error-boundary'
                },
                children: 'Something went wrong. Please refresh the page.'
            };
        }
        
        return this.children;
    }
}
```

**Advanced Error Handling Patterns:**

8. **Retry with Exponential Backoff:**
```javascript
async function retryWithBackoff(fn, maxRetries = 3, baseDelay = 1000) {
    let lastError;
    
    for (let attempt = 1; attempt <= maxRetries; attempt++) {
        try {
            return await fn();
        } catch (error) {
            lastError = error;
            
            if (attempt === maxRetries) {
                throw error;
            }
            
            const delay = baseDelay * Math.pow(2, attempt - 1);
            console.log(`Attempt ${attempt} failed, retrying in ${delay}ms`);
            
            await new Promise(resolve => setTimeout(resolve, delay));
        }
    }
    
    throw lastError;
}

// Usage
async function fetchData() {
    const response = await fetch('/api/data');
    if (!response.ok) {
        throw new Error(`HTTP ${response.status}`);
    }
    return response.json();
}

try {
    const data = await retryWithBackoff(fetchData, 3, 1000);
    console.log('Data fetched:', data);
} catch (error) {
    console.error('Failed after retries:', error);
}
```

9. **Circuit Breaker Pattern:**
```javascript
class CircuitBreaker {
    constructor(threshold = 5, timeout = 60000) {
        this.threshold = threshold;
        this.timeout = timeout;
        this.failureCount = 0;
        this.lastFailureTime = null;
        this.state = 'CLOSED'; // CLOSED, OPEN, HALF_OPEN
    }
    
    async execute(fn) {
        if (this.state === 'OPEN') {
            if (Date.now() - this.lastFailureTime > this.timeout) {
                this.state = 'HALF_OPEN';
            } else {
                throw new Error('Circuit breaker is OPEN');
            }
        }
        
        try {
            const result = await fn();
            this.onSuccess();
            return result;
        } catch (error) {
            this.onFailure();
            throw error;
        }
    }
    
    onSuccess() {
        this.failureCount = 0;
        this.state = 'CLOSED';
    }
    
    onFailure() {
        this.failureCount++;
        this.lastFailureTime = Date.now();
        
        if (this.failureCount >= this.threshold) {
            this.state = 'OPEN';
        }
    }
}

// Usage
const circuitBreaker = new CircuitBreaker(3, 30000);

async function callAPI() {
    return circuitBreaker.execute(async () => {
        const response = await fetch('/api/data');
        if (!response.ok) {
            throw new Error(`HTTP ${response.status}`);
        }
        return response.json();
    });
}
```

**Error Handling Best Practices:**

10. **Comprehensive Error Handling:**
```javascript
class ErrorHandler {
    static handle(error, context = {}) {
        const errorInfo = {
            message: error.message,
            stack: error.stack,
            name: error.name,
            context,
            timestamp: new Date().toISOString(),
            userAgent: navigator.userAgent,
            url: window.location.href
        };
        
        // Log to console in development
        if (process.env.NODE_ENV === 'development') {
            console.error('Error:', errorInfo);
        }
        
        // Send to logging service
        this.logError(errorInfo);
        
        // Show user-friendly message
        this.showUserMessage(error);
    }
    
    static logError(errorInfo) {
        // Send to logging service
        fetch('/api/errors', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(errorInfo)
        }).catch(console.error);
    }
    
    static showUserMessage(error) {
        let message = 'An unexpected error occurred. Please try again.';
        
        if (error instanceof NetworkError) {
            message = 'Network error. Please check your connection.';
        } else if (error instanceof ValidationError) {
            message = error.message;
        }
        
        // Show notification to user
        this.showNotification(message, 'error');
    }
    
    static showNotification(message, type = 'info') {
        // Implementation for showing notifications
        console.log(`${type.toUpperCase()}: ${message}`);
    }
}

// Usage
try {
    // Some operation that might fail
    await riskyOperation();
} catch (error) {
    ErrorHandler.handle(error, { operation: 'riskyOperation' });
}
```

**Best Practices:**
- Always handle errors gracefully
- Use specific error types for different scenarios
- Log errors for debugging and monitoring
- Provide user-friendly error messages
- Use try-catch for synchronous code
- Use try-catch with async/await for asynchronous code
- Implement retry mechanisms for transient errors
- Use circuit breakers for external service calls
- Set up global error handlers
- Test error scenarios thoroughly
- Document error handling strategies
- Use error boundaries for UI components

### 48. What is the difference between local and global variables?
**Answer:**
Local variables are accessible within their scope, global variables are accessible throughout the program.

**Detailed Explanation:**
Understanding the difference between local and global variables is fundamental to JavaScript programming. The scope of variables determines where they can be accessed and how they interact with other parts of your code.

**Global Variables:**

1. **Global Scope Variables:**
```javascript
// Global variables
var globalVar = 'I am global';
let globalLet = 'I am also global';
const globalConst = 'I am global too';

function testFunction() {
    console.log(globalVar); // 'I am global'
    console.log(globalLet); // 'I am also global'
    console.log(globalConst); // 'I am global too'
}

testFunction();

// Global variables are accessible everywhere
console.log(globalVar); // 'I am global'
```

2. **Global Object Properties:**
```javascript
// Variables declared without var, let, or const become global
function createGlobal() {
    globalVariable = 'I am global'; // No declaration keyword
    window.browserGlobal = 'I am on window object';
}

createGlobal();
console.log(globalVariable); // 'I am global'
console.log(window.browserGlobal); // 'I am on window object'
console.log(window.globalVariable); // 'I am global'
```

3. **Global Variable Issues:**
```javascript
// Problem: Global variables can be modified anywhere
var counter = 0;

function increment() {
    counter++; // Modifies global variable
    console.log(counter);
}

function decrement() {
    counter--; // Modifies same global variable
    console.log(counter);
}

increment(); // 1
increment(); // 2
decrement(); // 1

// Problem: Name conflicts
var name = 'John';

function processUser() {
    var name = 'Jane'; // Shadows global variable
    console.log(name); // 'Jane' (local)
    console.log(window.name); // 'John' (global)
}

processUser();
```

**Local Variables:**

4. **Function Scope (var):**
```javascript
function demonstrateVarScope() {
    if (true) {
        var localVar = 'I am local to function';
    }
    
    console.log(localVar); // 'I am local to function' (accessible)
    
    function innerFunction() {
        console.log(localVar); // 'I am local to function' (accessible)
    }
    
    innerFunction();
}

demonstrateVarScope();
// console.log(localVar); // ReferenceError: localVar is not defined
```

5. **Block Scope (let and const):**
```javascript
function demonstrateBlockScope() {
    if (true) {
        let blockLet = 'I am block scoped';
        const blockConst = 'I am also block scoped';
        
        console.log(blockLet); // 'I am block scoped'
        console.log(blockConst); // 'I am also block scoped'
    }
    
    // console.log(blockLet); // ReferenceError: blockLet is not defined
    // console.log(blockConst); // ReferenceError: blockConst is not defined
}

demonstrateBlockScope();
```

6. **Nested Scope:**
```javascript
function outerFunction() {
    const outerVar = 'I am in outer function';
    
    function innerFunction() {
        const innerVar = 'I am in inner function';
        
        console.log(outerVar); // 'I am in outer function' (accessible)
        console.log(innerVar); // 'I am in inner function' (accessible)
        
        function deepestFunction() {
            const deepestVar = 'I am in deepest function';
            
            console.log(outerVar); // 'I am in outer function' (accessible)
            console.log(innerVar); // 'I am in inner function' (accessible)
            console.log(deepestVar); // 'I am in deepest function' (accessible)
        }
        
        deepestFunction();
    }
    
    innerFunction();
    // console.log(innerVar); // ReferenceError: innerVar is not defined
    // console.log(deepestVar); // ReferenceError: deepestVar is not defined
}

outerFunction();
```

**Scope Chain and Closures:**

7. **Scope Chain Example:**
```javascript
const globalVar = 'I am global';

function outerFunction() {
    const outerVar = 'I am in outer function';
    
    function innerFunction() {
        const innerVar = 'I am in inner function';
        
        // JavaScript looks for variables in this order:
        // 1. innerFunction scope (innerVar)
        // 2. outerFunction scope (outerVar)
        // 3. global scope (globalVar)
        
        console.log(innerVar); // Found in innerFunction scope
        console.log(outerVar); // Found in outerFunction scope
        console.log(globalVar); // Found in global scope
    }
    
    innerFunction();
}

outerFunction();
```

8. **Closure Example:**
```javascript
function createCounter() {
    let count = 0; // Local variable in createCounter
    
    return function() {
        count++; // Access to local variable from outer function
        return count;
    };
}

const counter1 = createCounter();
const counter2 = createCounter();

console.log(counter1()); // 1
console.log(counter1()); // 2
console.log(counter2()); // 1 (separate closure)
console.log(counter1()); // 3
```

**Variable Hoisting:**

9. **Hoisting Behavior:**
```javascript
// var hoisting
console.log(hoistedVar); // undefined (not ReferenceError)
var hoistedVar = 'I am hoisted';

// let and const hoisting (Temporal Dead Zone)
// console.log(hoistedLet); // ReferenceError: Cannot access before initialization
let hoistedLet = 'I am hoisted but in TDZ';

// Function hoisting
console.log(hoistedFunction()); // 'I am hoisted' (works)
function hoistedFunction() {
    return 'I am hoisted';
}
```

**Best Practices:**

10. **Avoiding Global Variables:**
```javascript
// Bad: Global variables
var globalCounter = 0;
var globalName = 'John';

function badIncrement() {
    globalCounter++;
    console.log(globalCounter);
}

// Good: Encapsulation
const Counter = (function() {
    let count = 0; // Private variable
    
    return {
        increment() {
            count++;
            return count;
        },
        decrement() {
            count--;
            return count;
        },
        getCount() {
            return count;
        }
    };
})();

console.log(Counter.increment()); // 1
console.log(Counter.increment()); // 2
console.log(Counter.getCount()); // 2
```

11. **Module Pattern:**
```javascript
const UserModule = (function() {
    // Private variables
    let users = [];
    let currentUser = null;
    
    // Private functions
    function validateUser(user) {
        return user && user.name && user.email;
    }
    
    // Public API
    return {
        addUser(user) {
            if (validateUser(user)) {
                users.push(user);
                return true;
            }
            return false;
        },
        
        getUsers() {
            return [...users]; // Return copy, not reference
        },
        
        setCurrentUser(user) {
            if (validateUser(user)) {
                currentUser = user;
                return true;
            }
            return false;
        },
        
        getCurrentUser() {
            return currentUser;
        }
    };
})();

// Usage
UserModule.addUser({ name: 'John', email: 'john@example.com' });
UserModule.addUser({ name: 'Jane', email: 'jane@example.com' });
console.log(UserModule.getUsers()); // Array of users
```

**Modern JavaScript (ES6+):**

12. **ES6 Modules:**
```javascript
// user.js (module)
export const users = [];
export function addUser(user) {
    users.push(user);
}

export function getUsers() {
    return [...users];
}

// main.js
import { addUser, getUsers } from './user.js';

addUser({ name: 'John', email: 'john@example.com' });
console.log(getUsers());
```

13. **Block Scope Best Practices:**
```javascript
// Use block scope for temporary variables
function processData(data) {
    for (let i = 0; i < data.length; i++) {
        const item = data[i]; // Block scoped
        
        if (item.type === 'special') {
            const specialData = processSpecialItem(item); // Block scoped
            console.log(specialData);
        }
    }
    
    // i and item are not accessible here
}

function processSpecialItem(item) {
    return { ...item, processed: true };
}
```

**Summary:**
- **Global variables**: Accessible everywhere, can cause conflicts
- **Local variables**: Accessible only within their scope
- **var**: Function-scoped, hoisted
- **let/const**: Block-scoped, hoisted but in Temporal Dead Zone
- **Best practice**: Minimize global variables, use local scope
- **Use modules**: For better code organization and encapsulation
- **Use closures**: For private variables and state management

### 49. What are JavaScript event listeners?
**Answer:**
Functions that respond to specific events on DOM elements using `addEventListener()`.

**Detailed Explanation:**
Event listeners are functions that wait for and respond to specific events that occur in the browser. They are essential for creating interactive web applications and handling user interactions, system events, and custom events.

**Basic Event Listener Syntax:**

1. **addEventListener() Method:**
```javascript
// Basic event listener
const button = document.getElementById('myButton');

button.addEventListener('click', function(event) {
    console.log('Button clicked!');
    console.log('Event:', event);
});

// Arrow function syntax
button.addEventListener('click', (event) => {
    console.log('Button clicked with arrow function!');
});

// Named function
function handleClick(event) {
    console.log('Button clicked with named function!');
}
button.addEventListener('click', handleClick);
```

2. **Event Listener Options:**
```javascript
const button = document.getElementById('myButton');

// Basic listener
button.addEventListener('click', handleClick);

// With options object
button.addEventListener('click', handleClick, {
    once: true,        // Remove listener after first execution
    passive: true,     // Listener will never call preventDefault()
    capture: false     // Use bubbling phase (default)
});

// Legacy boolean syntax (deprecated)
button.addEventListener('click', handleClick, false); // capture = false
button.addEventListener('click', handleClick, true);  // capture = true
```

**Common Event Types:**

3. **Mouse Events:**
```javascript
const element = document.getElementById('myElement');

// Click events
element.addEventListener('click', (e) => {
    console.log('Element clicked');
});

element.addEventListener('dblclick', (e) => {
    console.log('Element double-clicked');
});

// Mouse movement events
element.addEventListener('mousemove', (e) => {
    console.log(`Mouse at: ${e.clientX}, ${e.clientY}`);
});

element.addEventListener('mouseenter', (e) => {
    console.log('Mouse entered element');
});

element.addEventListener('mouseleave', (e) => {
    console.log('Mouse left element');
});

// Mouse button events
element.addEventListener('mousedown', (e) => {
    console.log(`Mouse button ${e.button} pressed`);
});

element.addEventListener('mouseup', (e) => {
    console.log(`Mouse button ${e.button} released`);
});
```

4. **Keyboard Events:**
```javascript
const input = document.getElementById('myInput');

input.addEventListener('keydown', (e) => {
    console.log(`Key pressed: ${e.key} (code: ${e.code})`);
    
    // Prevent default behavior for specific keys
    if (e.key === 'Enter') {
        e.preventDefault();
        console.log('Enter key prevented');
    }
});

input.addEventListener('keyup', (e) => {
    console.log(`Key released: ${e.key}`);
});

input.addEventListener('keypress', (e) => {
    console.log(`Character typed: ${e.key}`);
});

// Global keyboard events
document.addEventListener('keydown', (e) => {
    if (e.ctrlKey && e.key === 's') {
        e.preventDefault();
        console.log('Ctrl+S pressed - saving...');
    }
});
```

5. **Form Events:**
```javascript
const form = document.getElementById('myForm');
const input = document.getElementById('myInput');

// Form submission
form.addEventListener('submit', (e) => {
    e.preventDefault(); // Prevent default form submission
    console.log('Form submitted');
    
    // Get form data
    const formData = new FormData(form);
    console.log('Form data:', Object.fromEntries(formData));
});

// Input events
input.addEventListener('input', (e) => {
    console.log('Input value changed:', e.target.value);
});

input.addEventListener('change', (e) => {
    console.log('Input value changed and lost focus:', e.target.value);
});

input.addEventListener('focus', (e) => {
    console.log('Input focused');
});

input.addEventListener('blur', (e) => {
    console.log('Input lost focus');
});
```

**Event Object Properties:**

6. **Event Object Methods:**
```javascript
const button = document.getElementById('myButton');

button.addEventListener('click', (e) => {
    // Event properties
    console.log('Event type:', e.type);
    console.log('Target element:', e.target);
    console.log('Current target:', e.currentTarget);
    console.log('Event phase:', e.eventPhase);
    
    // Mouse properties
    console.log('Mouse position:', e.clientX, e.clientY);
    console.log('Mouse buttons:', e.buttons);
    
    // Keyboard properties
    console.log('Key pressed:', e.key);
    console.log('Ctrl key:', e.ctrlKey);
    console.log('Shift key:', e.shiftKey);
    console.log('Alt key:', e.altKey);
    
    // Event methods
    e.preventDefault(); // Prevent default behavior
    e.stopPropagation(); // Stop event bubbling
    e.stopImmediatePropagation(); // Stop all listeners on this element
});
```

**Event Delegation:**

7. **Event Delegation Pattern:**
```javascript
// Instead of adding listeners to each item
const list = document.getElementById('myList');

// Add listener to parent element
list.addEventListener('click', (e) => {
    // Check if clicked element is a list item
    if (e.target.tagName === 'LI') {
        console.log('List item clicked:', e.target.textContent);
        
        // Add visual feedback
        e.target.classList.toggle('selected');
    }
});

// Dynamic content example
function addListItem(text) {
    const li = document.createElement('li');
    li.textContent = text;
    list.appendChild(li);
    // No need to add event listener - delegation handles it
}

// Add items dynamically
addListItem('Dynamic item 1');
addListItem('Dynamic item 2');
```

8. **Advanced Event Delegation:**
```javascript
// Handle multiple event types with delegation
const container = document.getElementById('container');

container.addEventListener('click', (e) => {
    const target = e.target;
    
    // Handle different element types
    if (target.classList.contains('button')) {
        handleButtonClick(e);
    } else if (target.classList.contains('link')) {
        handleLinkClick(e);
    } else if (target.classList.contains('input')) {
        handleInputClick(e);
    }
});

function handleButtonClick(e) {
    console.log('Button clicked:', e.target.textContent);
}

function handleLinkClick(e) {
    e.preventDefault();
    console.log('Link clicked:', e.target.href);
}

function handleInputClick(e) {
    console.log('Input clicked:', e.target.value);
}
```

**Custom Events:**

9. **Creating and Dispatching Custom Events:**
```javascript
// Create custom event
const customEvent = new CustomEvent('myCustomEvent', {
    detail: {
        message: 'Hello from custom event!',
        timestamp: Date.now()
    },
    bubbles: true,
    cancelable: true
});

// Listen for custom event
const element = document.getElementById('myElement');
element.addEventListener('myCustomEvent', (e) => {
    console.log('Custom event received:', e.detail);
});

// Dispatch custom event
element.dispatchEvent(customEvent);
```

10. **Event-driven Architecture:**
```javascript
class EventEmitter {
    constructor() {
        this.events = {};
    }
    
    on(event, callback) {
        if (!this.events[event]) {
            this.events[event] = [];
        }
        this.events[event].push(callback);
    }
    
    off(event, callback) {
        if (this.events[event]) {
            this.events[event] = this.events[event].filter(cb => cb !== callback);
        }
    }
    
    emit(event, data) {
        if (this.events[event]) {
            this.events[event].forEach(callback => callback(data));
        }
    }
}

// Usage
const emitter = new EventEmitter();

emitter.on('userLogin', (user) => {
    console.log('User logged in:', user.name);
});

emitter.on('userLogout', (user) => {
    console.log('User logged out:', user.name);
});

// Simulate user actions
emitter.emit('userLogin', { name: 'John', id: 1 });
emitter.emit('userLogout', { name: 'John', id: 1 });
```

**Event Listener Management:**

11. **Removing Event Listeners:**
```javascript
const button = document.getElementById('myButton');

// Named function (required for removal)
function handleClick(e) {
    console.log('Button clicked!');
}

// Add listener
button.addEventListener('click', handleClick);

// Remove listener
button.removeEventListener('click', handleClick);

// Remove all listeners of a specific type
button.removeEventListener('click', handleClick);
```

12. **Event Listener Cleanup:**
```javascript
class Component {
    constructor(element) {
        this.element = element;
        this.listeners = [];
    }
    
    addEventListener(type, callback, options = {}) {
        this.element.addEventListener(type, callback, options);
        this.listeners.push({ type, callback, options });
    }
    
    removeEventListener(type, callback) {
        this.element.removeEventListener(type, callback);
        this.listeners = this.listeners.filter(
            listener => !(listener.type === type && listener.callback === callback)
        );
    }
    
    destroy() {
        // Remove all listeners
        this.listeners.forEach(({ type, callback }) => {
            this.element.removeEventListener(type, callback);
        });
        this.listeners = [];
    }
}

// Usage
const component = new Component(document.getElementById('myElement'));
component.addEventListener('click', () => console.log('Clicked!'));
component.addEventListener('mouseenter', () => console.log('Mouse entered!'));

// Clean up when component is destroyed
component.destroy();
```

**Performance Considerations:**

13. **Event Listener Performance:**
```javascript
// Debounced event listener
function debounce(func, wait) {
    let timeout;
    return function executedFunction(...args) {
        const later = () => {
            clearTimeout(timeout);
            func(...args);
        };
        clearTimeout(timeout);
        timeout = setTimeout(later, wait);
    };
}

// Throttled event listener
function throttle(func, limit) {
    let inThrottle;
    return function executedFunction(...args) {
        if (!inThrottle) {
            func.apply(this, args);
            inThrottle = true;
            setTimeout(() => inThrottle = false, limit);
        }
    };
}

// Usage
const input = document.getElementById('searchInput');
const debouncedSearch = debounce((e) => {
    console.log('Searching for:', e.target.value);
}, 300);

const throttledScroll = throttle(() => {
    console.log('Scroll event handled');
}, 100);

input.addEventListener('input', debouncedSearch);
window.addEventListener('scroll', throttledScroll);
```

**Best Practices:**
- Use `addEventListener()` instead of inline event handlers
- Remove event listeners when no longer needed
- Use event delegation for dynamic content
- Use named functions for event listeners that need to be removed
- Consider performance implications of frequent events
- Use debouncing and throttling for performance
- Use custom events for component communication
- Clean up event listeners in component destruction
- Use passive listeners for scroll events when possible
- Test event handling across different browsers

### 50. What is the difference between innerHTML and textContent?
**Answer:**
- `innerHTML`: Gets/sets HTML content including tags
- `textContent`: Gets/sets text content without HTML tags

**Detailed Explanation:**
Both `innerHTML` and `textContent` are properties used to get and set content in DOM elements, but they handle content differently. Understanding their differences is crucial for safe and effective DOM manipulation.

**Basic Differences:**

1. **Content Handling:**
```javascript
const element = document.getElementById('myElement');

// Set content with innerHTML
element.innerHTML = '<strong>Hello</strong> <em>World</em>!';
console.log(element.innerHTML); // '<strong>Hello</strong> <em>World</em>!'
console.log(element.textContent); // 'Hello World!'

// Set content with textContent
element.textContent = '<strong>Hello</strong> <em>World</em>!';
console.log(element.innerHTML); // '&lt;strong&gt;Hello&lt;/strong&gt; &lt;em&gt;World&lt;/em&gt;!'
console.log(element.textContent); // '<strong>Hello</strong> <em>World</em>!'
```

2. **HTML vs Text Content:**
```javascript
const div = document.createElement('div');
div.innerHTML = '<p>Hello <span>World</span>!</p>';

console.log('innerHTML:', div.innerHTML);
// '<p>Hello <span>World</span>!</p>'

console.log('textContent:', div.textContent);
// 'Hello World!'

console.log('outerHTML:', div.outerHTML);
// '<div><p>Hello <span>World</span>!</p></div>'
```

**Security Considerations:**

3. **XSS Vulnerability with innerHTML:**
```javascript
// DANGEROUS: innerHTML can execute scripts
const userInput = '<img src=x onerror=alert("XSS Attack!")>';
const element = document.getElementById('content');

element.innerHTML = userInput; // This will execute the script!

// SAFE: textContent escapes HTML
const safeElement = document.getElementById('safeContent');
safeElement.textContent = userInput; // This displays the text safely
```

4. **Safe HTML Insertion:**
```javascript
// Function to safely insert HTML
function safeInnerHTML(element, html) {
    // Create a temporary element
    const temp = document.createElement('div');
    temp.textContent = html; // This escapes the HTML
    
    // Then set the innerHTML
    element.innerHTML = temp.innerHTML;
}

// Usage
const element = document.getElementById('content');
const userInput = '<script>alert("XSS")</script><p>Hello World</p>';

// Dangerous way
element.innerHTML = userInput; // Executes script!

// Safe way
safeInnerHTML(element, userInput); // Displays safely
```

**Performance Considerations:**

5. **Performance Comparison:**
```javascript
const element = document.getElementById('testElement');
const largeText = 'Hello World! '.repeat(1000);

// Performance test for innerHTML
console.time('innerHTML');
element.innerHTML = largeText;
console.timeEnd('innerHTML');

// Performance test for textContent
console.time('textContent');
element.textContent = largeText;
console.timeEnd('textContent');

// Performance test for createTextNode
console.time('createTextNode');
element.textContent = '';
element.appendChild(document.createTextNode(largeText));
console.timeEnd('createTextNode');
```

**Use Cases:**

6. **When to Use innerHTML:**
```javascript
// Good use cases for innerHTML
const element = document.getElementById('content');

// Inserting HTML structure
element.innerHTML = `
    <div class="card">
        <h3>Title</h3>
        <p>Description</p>
        <button>Click me</button>
    </div>
`;

// Replacing entire content
element.innerHTML = '<p>New content</p>';

// Adding HTML from trusted sources
const trustedHTML = '<p>This is <strong>safe</strong> HTML</p>';
element.innerHTML = trustedHTML;
```

7. **When to Use textContent:**
```javascript
// Good use cases for textContent
const element = document.getElementById('content');

// Displaying user input safely
element.textContent = userInput;

// Setting plain text content
element.textContent = 'Hello World!';

// Getting text content without HTML
element.innerHTML = '<p>Hello <strong>World</strong>!</p>';
console.log(element.textContent); // 'Hello World!'

// Clearing content
element.textContent = '';
```

**Advanced Examples:**

8. **Dynamic Content Creation:**
```javascript
function createUserCard(user) {
    const card = document.createElement('div');
    card.className = 'user-card';
    
    // Safe way to create HTML structure
    card.innerHTML = `
        <h3>${escapeHTML(user.name)}</h3>
        <p>Email: ${escapeHTML(user.email)}</p>
        <p>Age: ${user.age}</p>
    `;
    
    return card;
}

function escapeHTML(text) {
    const div = document.createElement('div');
    div.textContent = text;
    return div.innerHTML;
}

// Usage
const user = {
    name: 'John Doe',
    email: 'john@example.com',
    age: 30
};

const userCard = createUserCard(user);
document.body.appendChild(userCard);
```

9. **Content Manipulation:**
```javascript
function updateContent(element, content, isHTML = false) {
    if (isHTML) {
        element.innerHTML = content;
    } else {
        element.textContent = content;
    }
}

// Usage
const element = document.getElementById('content');

// Update with HTML
updateContent(element, '<p>This is <strong>HTML</strong> content</p>', true);

// Update with text
updateContent(element, 'This is plain text content', false);
```

**Alternative Methods:**

10. **Other Content Properties:**
```javascript
const element = document.getElementById('myElement');

element.innerHTML = '<p>Hello <span>World</span>!</p>';

console.log('innerHTML:', element.innerHTML);
// '<p>Hello <span>World</span>!</p>'

console.log('textContent:', element.textContent);
// 'Hello World!'

console.log('innerText:', element.innerText);
// 'Hello World!' (similar to textContent but respects CSS)

console.log('outerHTML:', element.outerHTML);
// '<div id="myElement"><p>Hello <span>World</span>!</p></div>'
```

11. **innerText vs textContent:**
```javascript
const element = document.getElementById('myElement');
element.innerHTML = '<p>Hello <span style="display: none;">Hidden</span> World!</p>';

console.log('textContent:', element.textContent);
// 'Hello Hidden World!' (includes hidden content)

console.log('innerText:', element.innerText);
// 'Hello World!' (excludes hidden content)
```

**Best Practices:**

12. **Security Best Practices:**
```javascript
// NEVER use innerHTML with user input directly
function dangerousFunction(userInput) {
    const element = document.getElementById('content');
    element.innerHTML = userInput; // XSS vulnerability!
}

// ALWAYS sanitize user input
function safeFunction(userInput) {
    const element = document.getElementById('content');
    element.textContent = userInput; // Safe
}

// OR sanitize HTML input
function sanitizeHTML(html) {
    const div = document.createElement('div');
    div.textContent = html;
    return div.innerHTML;
}

function safeHTMLFunction(userInput) {
    const element = document.getElementById('content');
    element.innerHTML = sanitizeHTML(userInput); // Safe
}
```

**Summary:**
- **innerHTML**: Use for HTML content, be careful with user input
- **textContent**: Use for plain text, always safe
- **Security**: innerHTML can execute scripts, textContent cannot
- **Performance**: textContent is generally faster
- **Use cases**: innerHTML for HTML structure, textContent for plain text
- **Best practice**: Use textContent for user input, innerHTML for trusted HTML
- **Alternative**: Consider using DOM methods for complex HTML creation

---

## 🔴 ADVANCED LEVEL (Questions 51-70)

### 51. What are JavaScript design patterns and how do you implement them?
**Answer:**
Reusable solutions to common problems. Examples: Singleton, Factory, Observer, Module patterns.

**Detailed Explanation:**
Design patterns are proven solutions to common programming problems. They provide a blueprint for solving recurring issues in software design and help create more maintainable, scalable, and efficient code.

**Singleton Pattern:**

1. **Basic Singleton:**
```javascript
class DatabaseConnection {
    constructor() {
        if (DatabaseConnection.instance) {
            return DatabaseConnection.instance;
        }
        
        this.connection = 'Connected to database';
        DatabaseConnection.instance = this;
    }
    
    getConnection() {
        return this.connection;
    }
}

// Usage
const db1 = new DatabaseConnection();
const db2 = new DatabaseConnection();
console.log(db1 === db2); // true (same instance)
```

2. **Module Pattern Singleton:**
```javascript
const ConfigManager = (function() {
    let instance = null;
    let config = {};
    
    function createInstance() {
        return {
            set(key, value) {
                config[key] = value;
            },
            get(key) {
                return config[key];
            },
            getAll() {
                return { ...config };
            }
        };
    }
    
    return {
        getInstance() {
            if (!instance) {
                instance = createInstance();
            }
            return instance;
        }
    };
})();

// Usage
const config1 = ConfigManager.getInstance();
const config2 = ConfigManager.getInstance();
console.log(config1 === config2); // true
```

**Factory Pattern:**

3. **Simple Factory:**
```javascript
class VehicleFactory {
    static createVehicle(type, options) {
        switch (type) {
            case 'car':
                return new Car(options);
            case 'truck':
                return new Truck(options);
            case 'motorcycle':
                return new Motorcycle(options);
            default:
                throw new Error(`Unknown vehicle type: ${type}`);
        }
    }
}

class Car {
    constructor(options) {
        this.type = 'car';
        this.wheels = 4;
        this.color = options.color || 'white';
    }
}

class Truck {
    constructor(options) {
        this.type = 'truck';
        this.wheels = 6;
        this.capacity = options.capacity || 1000;
    }
}

class Motorcycle {
    constructor(options) {
        this.type = 'motorcycle';
        this.wheels = 2;
        this.engine = options.engine || '250cc';
    }
}

// Usage
const car = VehicleFactory.createVehicle('car', { color: 'red' });
const truck = VehicleFactory.createVehicle('truck', { capacity: 2000 });
console.log(car.type, car.color); // 'car', 'red'
```

4. **Abstract Factory:**
```javascript
class UIFactory {
    static createFactory(theme) {
        switch (theme) {
            case 'material':
                return new MaterialUIFactory();
            case 'bootstrap':
                return new BootstrapUIFactory();
            default:
                throw new Error(`Unknown theme: ${theme}`);
        }
    }
}

class MaterialUIFactory {
    createButton(text) {
        return new MaterialButton(text);
    }
    
    createInput(placeholder) {
        return new MaterialInput(placeholder);
    }
}

class BootstrapUIFactory {
    createButton(text) {
        return new BootstrapButton(text);
    }
    
    createInput(placeholder) {
        return new BootstrapInput(placeholder);
    }
}

class MaterialButton {
    constructor(text) {
        this.text = text;
        this.className = 'btn-material';
    }
}

class BootstrapButton {
    constructor(text) {
        this.text = text;
        this.className = 'btn btn-primary';
    }
}

// Usage
const materialFactory = UIFactory.createFactory('material');
const button = materialFactory.createButton('Click me');
console.log(button.className); // 'btn-material'
```

**Observer Pattern:**

5. **Event System:**
```javascript
class EventEmitter {
    constructor() {
        this.events = {};
    }
    
    on(event, callback) {
        if (!this.events[event]) {
            this.events[event] = [];
        }
        this.events[event].push(callback);
    }
    
    off(event, callback) {
        if (this.events[event]) {
            this.events[event] = this.events[event].filter(cb => cb !== callback);
        }
    }
    
    emit(event, data) {
        if (this.events[event]) {
            this.events[event].forEach(callback => callback(data));
        }
    }
}

// Usage
const emitter = new EventEmitter();

emitter.on('userLogin', (user) => {
    console.log(`User ${user.name} logged in`);
});

emitter.on('userLogin', (user) => {
    console.log(`Sending welcome email to ${user.email}`);
});

emitter.emit('userLogin', { name: 'John', email: 'john@example.com' });
```

6. **Subject-Observer Pattern:**
```javascript
class Subject {
    constructor() {
        this.observers = [];
    }
    
    addObserver(observer) {
        this.observers.push(observer);
    }
    
    removeObserver(observer) {
        this.observers = this.observers.filter(obs => obs !== observer);
    }
    
    notify(data) {
        this.observers.forEach(observer => observer.update(data));
    }
}

class Observer {
    constructor(name) {
        this.name = name;
    }
    
    update(data) {
        console.log(`${this.name} received:`, data);
    }
}

// Usage
const subject = new Subject();
const observer1 = new Observer('Observer 1');
const observer2 = new Observer('Observer 2');

subject.addObserver(observer1);
subject.addObserver(observer2);

subject.notify('Hello World!');
// Observer 1 received: Hello World!
// Observer 2 received: Hello World!
```

**Module Pattern:**

7. **Revealing Module Pattern:**
```javascript
const UserModule = (function() {
    // Private variables
    let users = [];
    let currentUser = null;
    
    // Private functions
    function validateUser(user) {
        return user && user.name && user.email;
    }
    
    function findUserById(id) {
        return users.find(user => user.id === id);
    }
    
    // Public API
    return {
        addUser(user) {
            if (validateUser(user)) {
                user.id = Date.now();
                users.push(user);
                return user;
            }
            throw new Error('Invalid user data');
        },
        
        getUser(id) {
            return findUserById(id);
        },
        
        getAllUsers() {
            return [...users];
        },
        
        setCurrentUser(user) {
            if (validateUser(user)) {
                currentUser = user;
            }
        },
        
        getCurrentUser() {
            return currentUser;
        }
    };
})();

// Usage
UserModule.addUser({ name: 'John', email: 'john@example.com' });
console.log(UserModule.getAllUsers());
```

**Strategy Pattern:**

8. **Payment Strategies:**
```javascript
class PaymentStrategy {
    pay(amount) {
        throw new Error('Payment method not implemented');
    }
}

class CreditCardPayment extends PaymentStrategy {
    constructor(cardNumber, cvv) {
        super();
        this.cardNumber = cardNumber;
        this.cvv = cvv;
    }
    
    pay(amount) {
        console.log(`Paying $${amount} with credit card ending in ${this.cardNumber.slice(-4)}`);
        return true;
    }
}

class PayPalPayment extends PaymentStrategy {
    constructor(email) {
        super();
        this.email = email;
    }
    
    pay(amount) {
        console.log(`Paying $${amount} with PayPal account ${this.email}`);
        return true;
    }
}

class PaymentProcessor {
    constructor() {
        this.strategy = null;
    }
    
    setStrategy(strategy) {
        this.strategy = strategy;
    }
    
    processPayment(amount) {
        if (!this.strategy) {
            throw new Error('Payment strategy not set');
        }
        return this.strategy.pay(amount);
    }
}

// Usage
const processor = new PaymentProcessor();
processor.setStrategy(new CreditCardPayment('1234567890123456', '123'));
processor.processPayment(100);

processor.setStrategy(new PayPalPayment('user@example.com'));
processor.processPayment(50);
```

**Decorator Pattern:**

9. **Function Decorators:**
```javascript
function withLogging(fn) {
    return function(...args) {
        console.log(`Calling ${fn.name} with args:`, args);
        const result = fn.apply(this, args);
        console.log(`${fn.name} returned:`, result);
        return result;
    };
}

function withTiming(fn) {
    return function(...args) {
        const start = performance.now();
        const result = fn.apply(this, args);
        const end = performance.now();
        console.log(`${fn.name} took ${end - start} milliseconds`);
        return result;
    };
}

function withRetry(fn, maxRetries = 3) {
    return function(...args) {
        let lastError;
        
        for (let i = 0; i < maxRetries; i++) {
            try {
                return fn.apply(this, args);
            } catch (error) {
                lastError = error;
                console.log(`Attempt ${i + 1} failed:`, error.message);
            }
        }
        
        throw lastError;
    };
}

// Usage
function fetchData(url) {
    return fetch(url).then(response => response.json());
}

const decoratedFetch = withLogging(withTiming(withRetry(fetchData)));
decoratedFetch('/api/data');
```

**Best Practices:**
- Choose patterns that solve your specific problem
- Don't over-engineer simple solutions
- Consider performance implications
- Use patterns consistently across your codebase
- Document pattern usage and rationale
- Consider modern alternatives (e.g., React hooks vs class patterns)
- Test pattern implementations thoroughly
- Keep patterns simple and readable

### 52. How do you optimize JavaScript performance?
**Answer:**
Techniques include debouncing, throttling, memoization, lazy loading, virtual scrolling, and code splitting.

**Detailed Explanation:**
JavaScript performance optimization is crucial for creating fast, responsive web applications. There are many techniques and strategies to improve performance, from simple optimizations to advanced patterns.

**Debouncing and Throttling:**

1. **Debouncing:**
```javascript
function debounce(func, wait, immediate = false) {
    let timeout;
    return function executedFunction(...args) {
        const later = () => {
            timeout = null;
            if (!immediate) func.apply(this, args);
        };
        
        const callNow = immediate && !timeout;
        clearTimeout(timeout);
        timeout = setTimeout(later, wait);
        
        if (callNow) func.apply(this, args);
    };
}

// Usage
const searchInput = document.getElementById('search');
const debouncedSearch = debounce((query) => {
    console.log('Searching for:', query);
    // Perform search
}, 300);

searchInput.addEventListener('input', (e) => {
    debouncedSearch(e.target.value);
});
```

2. **Throttling:**
```javascript
function throttle(func, limit) {
    let inThrottle;
    return function executedFunction(...args) {
        if (!inThrottle) {
            func.apply(this, args);
            inThrottle = true;
            setTimeout(() => inThrottle = false, limit);
        }
    };
}

// Usage
const scrollHandler = throttle(() => {
    console.log('Scroll event handled');
    // Handle scroll
}, 100);

window.addEventListener('scroll', scrollHandler);
```

**Memoization:**

3. **Basic Memoization:**
```javascript
function memoize(fn) {
    const cache = new Map();
    return function(...args) {
        const key = JSON.stringify(args);
        
        if (cache.has(key)) {
            return cache.get(key);
        }
        
        const result = fn.apply(this, args);
        cache.set(key, result);
        return result;
    };
}

// Usage
const expensiveCalculation = memoize((n) => {
    console.log('Calculating...');
    return n * n * n;
});

console.log(expensiveCalculation(5)); // Calculating... 125
console.log(expensiveCalculation(5)); // 125 (from cache)
```

4. **Advanced Memoization:**
```javascript
function memoizeWithOptions(fn, options = {}) {
    const { maxSize = 100, ttl = 0 } = options;
    const cache = new Map();
    const timestamps = new Map();
    
    return function(...args) {
        const key = JSON.stringify(args);
        const now = Date.now();
        
        // Check if cached and not expired
        if (cache.has(key)) {
            if (ttl === 0 || (now - timestamps.get(key)) < ttl) {
                return cache.get(key);
            } else {
                cache.delete(key);
                timestamps.delete(key);
            }
        }
        
        // Calculate result
        const result = fn.apply(this, args);
        
        // Check cache size
        if (cache.size >= maxSize) {
            const firstKey = cache.keys().next().value;
            cache.delete(firstKey);
            timestamps.delete(firstKey);
        }
        
        cache.set(key, result);
        timestamps.set(key, now);
        return result;
    };
}

// Usage
const fibonacci = memoizeWithOptions((n) => {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}, { maxSize: 50, ttl: 5000 });
```

**Lazy Loading:**

5. **Image Lazy Loading:**
```javascript
class LazyLoader {
    constructor() {
        this.observer = new IntersectionObserver(
            this.handleIntersection.bind(this),
            { rootMargin: '50px' }
        );
    }
    
    observe(element) {
        this.observer.observe(element);
    }
    
    handleIntersection(entries) {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                const img = entry.target;
                img.src = img.dataset.src;
                img.classList.remove('lazy');
                this.observer.unobserve(img);
            }
        });
    }
}

// Usage
const lazyLoader = new LazyLoader();
document.querySelectorAll('img[data-src]').forEach(img => {
    lazyLoader.observe(img);
});
```

6. **Component Lazy Loading:**
```javascript
// Lazy load components
const LazyComponent = React.lazy(() => import('./HeavyComponent'));

function App() {
    return (
        <Suspense fallback={<div>Loading...</div>}>
            <LazyComponent />
        </Suspense>
    );
}

// Dynamic imports
async function loadModule() {
    const module = await import('./heavyModule.js');
    return module.default;
}

// Usage
loadModule().then(module => {
    module.doSomething();
});
```

**Virtual Scrolling:**

7. **Virtual List Implementation:**
```javascript
class VirtualList {
    constructor(container, itemHeight, items) {
        this.container = container;
        this.itemHeight = itemHeight;
        this.items = items;
        this.visibleItems = [];
        this.scrollTop = 0;
        this.containerHeight = container.clientHeight;
        
        this.init();
    }
    
    init() {
        this.container.style.overflow = 'auto';
        this.container.style.height = `${this.containerHeight}px`;
        
        // Create virtual content
        this.virtualContent = document.createElement('div');
        this.virtualContent.style.height = `${this.items.length * this.itemHeight}px`;
        this.container.appendChild(this.virtualContent);
        
        this.container.addEventListener('scroll', this.handleScroll.bind(this));
        this.updateVisibleItems();
    }
    
    handleScroll() {
        this.scrollTop = this.container.scrollTop;
        this.updateVisibleItems();
    }
    
    updateVisibleItems() {
        const startIndex = Math.floor(this.scrollTop / this.itemHeight);
        const endIndex = Math.min(
            startIndex + Math.ceil(this.containerHeight / this.itemHeight) + 1,
            this.items.length
        );
        
        // Clear existing items
        this.virtualContent.innerHTML = '';
        
        // Create visible items
        for (let i = startIndex; i < endIndex; i++) {
            const item = document.createElement('div');
            item.style.position = 'absolute';
            item.style.top = `${i * this.itemHeight}px`;
            item.style.height = `${this.itemHeight}px`;
            item.textContent = this.items[i];
            this.virtualContent.appendChild(item);
        }
    }
}

// Usage
const container = document.getElementById('list-container');
const items = Array.from({ length: 10000 }, (_, i) => `Item ${i}`);
const virtualList = new VirtualList(container, 50, items);
```

**Code Splitting:**

8. **Dynamic Imports:**
```javascript
// Route-based code splitting
const routes = {
    '/home': () => import('./pages/Home'),
    '/about': () => import('./pages/About'),
    '/contact': () => import('./pages/Contact')
};

async function loadRoute(path) {
    const module = await routes[path]();
    return module.default;
}

// Usage
loadRoute('/home').then(Component => {
    // Render component
});
```

9. **Webpack Code Splitting:**
```javascript
// Dynamic imports with webpack
const loadComponent = (componentName) => {
    return import(`./components/${componentName}`)
        .then(module => module.default)
        .catch(error => {
            console.error('Failed to load component:', error);
            return null;
        });
};

// Usage
loadComponent('HeavyComponent').then(Component => {
    if (Component) {
        // Use component
    }
});
```

**Performance Monitoring:**

10. **Performance Observer:**
```javascript
class PerformanceMonitor {
    constructor() {
        this.observer = new PerformanceObserver((list) => {
            list.getEntries().forEach(entry => {
                this.handleEntry(entry);
            });
        });
        
        this.observer.observe({ entryTypes: ['measure', 'navigation', 'resource'] });
    }
    
    handleEntry(entry) {
        switch (entry.entryType) {
            case 'measure':
                console.log(`Custom measure: ${entry.name} - ${entry.duration}ms`);
                break;
            case 'navigation':
                console.log(`Page load: ${entry.loadEventEnd - entry.loadEventStart}ms`);
                break;
            case 'resource':
                console.log(`Resource loaded: ${entry.name} - ${entry.duration}ms`);
                break;
        }
    }
    
    measure(name, fn) {
        performance.mark(`${name}-start`);
        const result = fn();
        performance.mark(`${name}-end`);
        performance.measure(name, `${name}-start`, `${name}-end`);
        return result;
    }
}

// Usage
const monitor = new PerformanceMonitor();
monitor.measure('expensive-operation', () => {
    // Some expensive operation
    return Math.random();
});
```

**Memory Optimization:**

11. **Object Pool Pattern:**
```javascript
class ObjectPool {
    constructor(createFn, resetFn, initialSize = 10) {
        this.createFn = createFn;
        this.resetFn = resetFn;
        this.pool = [];
        
        // Pre-populate pool
        for (let i = 0; i < initialSize; i++) {
            this.pool.push(this.createFn());
        }
    }
    
    acquire() {
        if (this.pool.length > 0) {
            return this.pool.pop();
        }
        return this.createFn();
    }
    
    release(obj) {
        this.resetFn(obj);
        this.pool.push(obj);
    }
}

// Usage
const particlePool = new ObjectPool(
    () => ({ x: 0, y: 0, vx: 0, vy: 0, active: false }),
    (particle) => {
        particle.x = 0;
        particle.y = 0;
        particle.vx = 0;
        particle.vy = 0;
        particle.active = false;
    }
);

// Use particles
const particle = particlePool.acquire();
particle.x = 100;
particle.y = 100;
particle.active = true;

// Release when done
particlePool.release(particle);
```

**Best Practices:**
- Use performance profiling tools to identify bottlenecks
- Implement lazy loading for non-critical resources
- Use debouncing and throttling for frequent events
- Implement proper caching strategies
- Use virtual scrolling for large lists
- Split code into smaller, loadable chunks
- Monitor performance metrics in production
- Use Web Workers for CPU-intensive tasks
- Optimize images and assets
- Minimize DOM manipulations
- Use requestAnimationFrame for animations
- Implement proper error handling and fallbacks

### 53. What are JavaScript Proxies and how do you use them?
**Answer:**
Proxies allow interception and customization of operations on objects (get, set, has, deleteProperty).

**Detailed Explanation:**
Proxies are a powerful ES6 feature that allows you to intercept and customize operations performed on objects. They provide a way to define custom behavior for fundamental operations like property lookup, assignment, enumeration, function invocation, etc.

**Basic Proxy Syntax:**

1. **Simple Proxy:**
```javascript
const target = {
    name: 'John',
    age: 30
};

const proxy = new Proxy(target, {
    get(target, property, receiver) {
        console.log(`Getting property: ${property}`);
        return target[property];
    },
    
    set(target, property, value, receiver) {
        console.log(`Setting property: ${property} = ${value}`);
        target[property] = value;
        return true;
    }
});

// Usage
console.log(proxy.name); // Getting property: name, John
proxy.age = 31; // Setting property: age = 31
```

2. **Property Validation:**
```javascript
const user = {};

const userProxy = new Proxy(user, {
    set(target, property, value) {
        if (property === 'age' && (typeof value !== 'number' || value < 0)) {
            throw new Error('Age must be a positive number');
        }
        
        if (property === 'email' && !value.includes('@')) {
            throw new Error('Invalid email format');
        }
        
        target[property] = value;
        return true;
    }
});

// Usage
try {
    userProxy.age = 25; // Valid
    userProxy.email = 'john@example.com'; // Valid
    userProxy.age = -5; // Error: Age must be a positive number
} catch (error) {
    console.error(error.message);
}
```

**Advanced Proxy Patterns:**

3. **Reactive System:**
```javascript
class ReactiveSystem {
    constructor() {
        this.data = {};
        this.listeners = new Map();
        this.proxy = this.createProxy(this.data);
    }
    
    createProxy(obj) {
        return new Proxy(obj, {
            set(target, property, value) {
                const oldValue = target[property];
                target[property] = value;
                
                // Notify listeners
                if (oldValue !== value) {
                    this.notifyListeners(property, value, oldValue);
                }
                
                return true;
            }
        });
    }
    
    watch(property, callback) {
        if (!this.listeners.has(property)) {
            this.listeners.set(property, []);
        }
        this.listeners.get(property).push(callback);
    }
    
    notifyListeners(property, newValue, oldValue) {
        if (this.listeners.has(property)) {
            this.listeners.get(property).forEach(callback => {
                callback(newValue, oldValue);
            });
        }
    }
}

// Usage
const reactive = new ReactiveSystem();

reactive.watch('name', (newValue, oldValue) => {
    console.log(`Name changed from ${oldValue} to ${newValue}`);
});

reactive.proxy.name = 'John'; // Name changed from undefined to John
reactive.proxy.name = 'Jane'; // Name changed from John to Jane
```

4. **Virtual Properties:**
```javascript
const person = {
    firstName: 'John',
    lastName: 'Doe'
};

const personProxy = new Proxy(person, {
    get(target, property) {
        if (property === 'fullName') {
            return `${target.firstName} ${target.lastName}`;
        }
        
        if (property === 'initials') {
            return `${target.firstName[0]}${target.lastName[0]}`;
        }
        
        return target[property];
    },
    
    set(target, property, value) {
        if (property === 'fullName') {
            const [firstName, lastName] = value.split(' ');
            target.firstName = firstName;
            target.lastName = lastName;
            return true;
        }
        
        target[property] = value;
        return true;
    }
});

// Usage
console.log(personProxy.fullName); // John Doe
console.log(personProxy.initials); // JD
personProxy.fullName = 'Jane Smith';
console.log(personProxy.firstName); // Jane
```

**Proxy Traps:**

5. **Complete Proxy Example:**
```javascript
const target = {};

const proxy = new Proxy(target, {
    // Property access
    get(target, property, receiver) {
        console.log(`GET: ${property}`);
        return target[property];
    },
    
    // Property assignment
    set(target, property, value, receiver) {
        console.log(`SET: ${property} = ${value}`);
        target[property] = value;
        return true;
    },
    
    // Property existence check
    has(target, property) {
        console.log(`HAS: ${property}`);
        return property in target;
    },
    
    // Property deletion
    deleteProperty(target, property) {
        console.log(`DELETE: ${property}`);
        return delete target[property];
    },
    
    // Property enumeration
    ownKeys(target) {
        console.log('OWNKEYS');
        return Object.keys(target);
    },
    
    // Property descriptor
    getOwnPropertyDescriptor(target, property) {
        console.log(`GETOWNPROPERTYDESCRIPTOR: ${property}`);
        return Object.getOwnPropertyDescriptor(target, property);
    },
    
    // Define property
    defineProperty(target, property, descriptor) {
        console.log(`DEFINEPROPERTY: ${property}`);
        return Object.defineProperty(target, property, descriptor);
    }
});

// Usage
proxy.name = 'John'; // SET: name = John
console.log(proxy.name); // GET: name, John
console.log('name' in proxy); // HAS: name, true
delete proxy.name; // DELETE: name
```

**Practical Use Cases:**

6. **API Wrapper:**
```javascript
class APIWrapper {
    constructor(baseURL) {
        this.baseURL = baseURL;
        this.cache = new Map();
        this.proxy = this.createProxy();
    }
    
    createProxy() {
        return new Proxy(this, {
            get(target, property) {
                if (typeof property === 'string' && property.startsWith('get')) {
                    const endpoint = property.slice(3).toLowerCase();
                    return async (id) => {
                        const cacheKey = `${endpoint}-${id}`;
                        
                        if (target.cache.has(cacheKey)) {
                            console.log('Cache hit');
                            return target.cache.get(cacheKey);
                        }
                        
                        console.log('Fetching from API');
                        const response = await fetch(`${target.baseURL}/${endpoint}/${id}`);
                        const data = await response.json();
                        
                        target.cache.set(cacheKey, data);
                        return data;
                    };
                }
                
                return target[property];
            }
        });
    }
}

// Usage
const api = new APIWrapper('https://api.example.com');

// These will be intercepted
const user = await api.getUser(123);
const post = await api.getPost(456);
```

7. **Object Observer:**
```javascript
class ObjectObserver {
    constructor(obj) {
        this.original = obj;
        this.changes = [];
        this.proxy = this.createProxy(obj);
    }
    
    createProxy(obj) {
        return new Proxy(obj, {
            set(target, property, value) {
                const oldValue = target[property];
                target[property] = value;
                
                this.changes.push({
                    property,
                    oldValue,
                    newValue: value,
                    timestamp: Date.now()
                });
                
                return true;
            }
        });
    }
    
    getChanges() {
        return [...this.changes];
    }
    
    clearChanges() {
        this.changes = [];
    }
}

// Usage
const obj = { name: 'John', age: 30 };
const observer = new ObjectObserver(obj);

observer.proxy.name = 'Jane';
observer.proxy.age = 31;

console.log(observer.getChanges());
// [{ property: 'name', oldValue: 'John', newValue: 'Jane', timestamp: ... },
//  { property: 'age', oldValue: 30, newValue: 31, timestamp: ... }]
```

**Proxy Limitations and Considerations:**

8. **Proxy Limitations:**
```javascript
// Proxies cannot intercept certain operations
const target = {};
const proxy = new Proxy(target, {
    get(target, property) {
        console.log(`Getting: ${property}`);
        return target[property];
    }
});

// These won't trigger the proxy
console.log(Object.keys(proxy)); // Won't trigger get trap
console.log(proxy instanceof Object); // Won't trigger get trap
console.log(proxy.constructor); // Won't trigger get trap

// These will trigger the proxy
console.log(proxy.someProperty); // Will trigger get trap
```

9. **Performance Considerations:**
```javascript
// Proxy performance test
const obj = {};
const proxy = new Proxy(obj, {
    get(target, property) {
        return target[property];
    },
    set(target, property, value) {
        target[property] = value;
        return true;
    }
});

// Performance comparison
console.time('Direct access');
for (let i = 0; i < 1000000; i++) {
    obj[`prop${i}`] = i;
}
console.timeEnd('Direct access');

console.time('Proxy access');
for (let i = 0; i < 1000000; i++) {
    proxy[`prop${i}`] = i;
}
console.timeEnd('Proxy access');
```

**Best Practices:**
- Use proxies for cross-cutting concerns (logging, validation, caching)
- Be aware of performance implications
- Don't overuse proxies for simple operations
- Consider using Object.defineProperty for simple property interception
- Use proxies for creating domain-specific languages
- Implement proper error handling in proxy traps
- Test proxy behavior thoroughly
- Document proxy behavior and limitations
- Consider using libraries like MobX or Vue.js for reactive systems
- Use proxies for creating transparent wrappers around APIs

### 54. What is the difference between microtasks and macrotasks?
**Answer:**
Microtasks (Promises, queueMicrotask) have higher priority than macrotasks (setTimeout, setInterval).

**Detailed Explanation:**
Understanding the difference between microtasks and macrotasks is crucial for understanding JavaScript's event loop and asynchronous execution. The event loop processes these tasks in a specific order, which affects the execution sequence of your code.

**Event Loop Overview:**

1. **Basic Event Loop Structure:**
```javascript
console.log('1. Synchronous code');

setTimeout(() => console.log('2. Macrotask (setTimeout)'), 0);

Promise.resolve().then(() => console.log('3. Microtask (Promise)'));

queueMicrotask(() => console.log('4. Microtask (queueMicrotask)'));

console.log('5. Synchronous code');

// Output:
// 1. Synchronous code
// 5. Synchronous code
// 3. Microtask (Promise)
// 4. Microtask (queueMicrotask)
// 2. Macrotask (setTimeout)
```

2. **Event Loop Phases:**
```javascript
// 1. Execute synchronous code
console.log('Start');

// 2. Process microtasks
Promise.resolve().then(() => {
    console.log('Microtask 1');
    
    // This creates another microtask
    Promise.resolve().then(() => {
        console.log('Microtask 2');
    });
});

// 3. Process macrotasks
setTimeout(() => {
    console.log('Macrotask 1');
    
    // This creates a microtask
    Promise.resolve().then(() => {
        console.log('Microtask in macrotask');
    });
}, 0);

console.log('End');

// Output:
// Start
// End
// Microtask 1
// Microtask 2
// Macrotask 1
// Microtask in macrotask
```

**Microtasks:**

3. **Microtask Sources:**
```javascript
// Promise.then/catch/finally
Promise.resolve().then(() => {
    console.log('Promise microtask');
});

// queueMicrotask API
queueMicrotask(() => {
    console.log('queueMicrotask');
});

// MutationObserver
const observer = new MutationObserver(() => {
    console.log('MutationObserver microtask');
});

// Process.nextTick (Node.js only)
// process.nextTick(() => {
//     console.log('process.nextTick microtask');
// });
```

4. **Microtask Queue Behavior:**
```javascript
console.log('Start');

// Multiple microtasks
Promise.resolve().then(() => {
    console.log('Microtask 1');
    
    // Adding more microtasks
    Promise.resolve().then(() => {
        console.log('Microtask 3');
    });
    
    queueMicrotask(() => {
        console.log('Microtask 4');
    });
});

Promise.resolve().then(() => {
    console.log('Microtask 2');
});

setTimeout(() => {
    console.log('Macrotask (setTimeout)');
}, 0);

console.log('End');

// Output:
// Start
// End
// Microtask 1
// Microtask 2
// Microtask 3
// Microtask 4
// Macrotask (setTimeout)
```

**Macrotasks:**

5. **Macrotask Sources:**
```javascript
// setTimeout/setInterval
setTimeout(() => {
    console.log('setTimeout macrotask');
}, 0);

setInterval(() => {
    console.log('setInterval macrotask');
}, 1000);

// setImmediate (Node.js only)
// setImmediate(() => {
//     console.log('setImmediate macrotask');
// });

// I/O operations (Node.js)
// fs.readFile('file.txt', () => {
//     console.log('I/O macrotask');
// });

// User interactions
button.addEventListener('click', () => {
    console.log('Click macrotask');
});
```

6. **Macrotask Queue Behavior:**
```javascript
console.log('Start');

// Multiple macrotasks
setTimeout(() => console.log('Macrotask 1'), 0);
setTimeout(() => console.log('Macrotask 2'), 0);
setTimeout(() => console.log('Macrotask 3'), 0);

// Microtasks have priority
Promise.resolve().then(() => {
    console.log('Microtask 1');
    
    // Adding more microtasks
    Promise.resolve().then(() => {
        console.log('Microtask 2');
    });
});

console.log('End');

// Output:
// Start
// End
// Microtask 1
// Microtask 2
// Macrotask 1
// Macrotask 2
// Macrotask 3
```

**Priority and Execution Order:**

7. **Execution Priority:**
```javascript
console.log('1. Synchronous');

// Macrotasks
setTimeout(() => console.log('2. Macrotask 1'), 0);
setTimeout(() => console.log('3. Macrotask 2'), 0);

// Microtasks
Promise.resolve().then(() => console.log('4. Microtask 1'));
queueMicrotask(() => console.log('5. Microtask 2'));

// More synchronous code
console.log('6. Synchronous');

// Output:
// 1. Synchronous
// 6. Synchronous
// 4. Microtask 1
// 5. Microtask 2
// 2. Macrotask 1
// 3. Macrotask 2
```

8. **Nested Task Execution:**
```javascript
console.log('Start');

setTimeout(() => {
    console.log('Macrotask 1');
    
    // Microtasks in macrotask
    Promise.resolve().then(() => {
        console.log('Microtask in macrotask 1');
    });
    
    queueMicrotask(() => {
        console.log('Microtask in macrotask 2');
    });
    
    // Another macrotask
    setTimeout(() => {
        console.log('Macrotask 2');
    }, 0);
}, 0);

Promise.resolve().then(() => {
    console.log('Microtask 1');
    
    // Macrotask in microtask
    setTimeout(() => {
        console.log('Macrotask in microtask');
    }, 0);
});

console.log('End');

// Output:
// Start
// End
// Microtask 1
// Macrotask 1
// Microtask in macrotask 1
// Microtask in macrotask 2
// Macrotask 2
// Macrotask in microtask
```

**Practical Examples:**

9. **Async/Await and Microtasks:**
```javascript
async function asyncFunction() {
    console.log('Async function start');
    
    await Promise.resolve();
    console.log('After await');
    
    return 'result';
}

console.log('Start');

asyncFunction().then(result => {
    console.log('Promise resolved:', result);
});

setTimeout(() => {
    console.log('setTimeout');
}, 0);

console.log('End');

// Output:
// Start
// Async function start
// End
// After await
// Promise resolved: result
// setTimeout
```

10. **Event Loop Blocking:**
```javascript
console.log('Start');

// This blocks the event loop
setTimeout(() => {
    console.log('Macrotask 1');
    
    // Long running operation
    const start = Date.now();
    while (Date.now() - start < 1000) {
        // Block for 1 second
    }
    
    console.log('Macrotask 1 done');
}, 0);

setTimeout(() => {
    console.log('Macrotask 2');
}, 0);

Promise.resolve().then(() => {
    console.log('Microtask 1');
});

console.log('End');

// Output:
// Start
// End
// Microtask 1
// Macrotask 1
// Macrotask 1 done
// Macrotask 2
```

**Best Practices:**

11. **Avoiding Event Loop Blocking:**
```javascript
// Bad: Blocking the event loop
function badFunction() {
    const start = Date.now();
    while (Date.now() - start < 1000) {
        // Block for 1 second
    }
}

// Good: Using setTimeout to yield control
function goodFunction() {
    return new Promise(resolve => {
        setTimeout(() => {
            // Do work here
            resolve('done');
        }, 0);
    });
}

// Better: Using requestIdleCallback
function betterFunction() {
    return new Promise(resolve => {
        requestIdleCallback(() => {
            // Do work here
            resolve('done');
        });
    });
}
```

12. **Microtask vs Macrotask Use Cases:**
```javascript
// Use microtasks for:
// - Promise resolution
// - DOM updates that need to happen before next render
// - Cleanup operations

Promise.resolve().then(() => {
    // This runs before the next render
    document.body.classList.add('loaded');
});

// Use macrotasks for:
// - User interactions
// - Network requests
// - File I/O
// - Operations that can be delayed

setTimeout(() => {
    // This runs after the current execution stack
    fetch('/api/data').then(response => response.json());
}, 0);
```

**Summary:**
- **Microtasks**: Higher priority, processed before macrotasks
- **Macrotasks**: Lower priority, processed after microtasks
- **Execution order**: Synchronous → Microtasks → Macrotasks
- **Use microtasks**: For immediate, high-priority operations
- **Use macrotasks**: For operations that can be delayed
- **Avoid blocking**: Use setTimeout or requestIdleCallback for long operations
- **Understand the event loop**: For predictable asynchronous behavior

### 55. What are JavaScript Generators and how do you use them?
**Answer:**
Functions that can be paused and resumed using `yield` keyword, useful for creating iterators.

**Detailed Explanation:**
Generators are special functions that can be paused and resumed during execution. They provide a powerful way to create iterators and handle asynchronous operations in a more readable manner.

**Basic Generator Syntax:**

1. **Simple Generator:**
```javascript
function* simpleGenerator() {
    yield 1;
    yield 2;
    yield 3;
}

const gen = simpleGenerator();
console.log(gen.next()); // { value: 1, done: false }
console.log(gen.next()); // { value: 2, done: false }
console.log(gen.next()); // { value: 3, done: false }
console.log(gen.next()); // { value: undefined, done: true }
```

2. **Generator with Parameters:**
```javascript
function* generatorWithParams() {
    const first = yield 'First yield';
    const second = yield `Second yield: ${first}`;
    return `Final: ${second}`;
}

const gen = generatorWithParams();
console.log(gen.next()); // { value: 'First yield', done: false }
console.log(gen.next('Hello')); // { value: 'Second yield: Hello', done: false }
console.log(gen.next('World')); // { value: 'Final: World', done: true }
```

**Generator Methods:**

3. **Generator Object Methods:**
```javascript
function* generator() {
    yield 1;
    yield 2;
    yield 3;
}

const gen = generator();

// next() method
console.log(gen.next()); // { value: 1, done: false }
console.log(gen.next()); // { value: 2, done: false }

// return() method
console.log(gen.return('Early return')); // { value: 'Early return', done: true }
console.log(gen.next()); // { value: undefined, done: true }

// throw() method
const gen2 = generator();
console.log(gen2.next()); // { value: 1, done: false }
try {
    gen2.throw(new Error('Generator error'));
} catch (error) {
    console.log('Caught error:', error.message);
}
```

**Iterator Implementation:**

4. **Custom Iterator with Generator:**
```javascript
class NumberRange {
    constructor(start, end) {
        this.start = start;
        this.end = end;
    }
    
    *[Symbol.iterator]() {
        for (let i = this.start; i <= this.end; i++) {
            yield i;
        }
    }
}

const range = new NumberRange(1, 5);
for (const num of range) {
    console.log(num); // 1, 2, 3, 4, 5
}

// Using spread operator
console.log([...range]); // [1, 2, 3, 4, 5]
```

5. **Fibonacci Generator:**
```javascript
function* fibonacci() {
    let a = 0, b = 1;
    while (true) {
        yield a;
        [a, b] = [b, a + b];
    }
}

const fib = fibonacci();
console.log(fib.next().value); // 0
console.log(fib.next().value); // 1
console.log(fib.next().value); // 1
console.log(fib.next().value); // 2
console.log(fib.next().value); // 3
```

**Advanced Generator Patterns:**

6. **Generator Composition:**
```javascript
function* take(generator, count) {
    let i = 0;
    for (const value of generator) {
        if (i >= count) break;
        yield value;
        i++;
    }
}

function* filter(generator, predicate) {
    for (const value of generator) {
        if (predicate(value)) {
            yield value;
        }
    }
}

function* map(generator, transform) {
    for (const value of generator) {
        yield transform(value);
    }
}

// Usage
function* numbers() {
    let i = 0;
    while (true) {
        yield i++;
    }
}

const evenNumbers = take(
    filter(numbers(), n => n % 2 === 0),
    5
);

console.log([...evenNumbers]); // [0, 2, 4, 6, 8]
```

7. **Generator with Error Handling:**
```javascript
function* generatorWithError() {
    try {
        yield 1;
        yield 2;
        yield 3;
    } catch (error) {
        console.log('Generator caught error:', error.message);
        yield 'Error handled';
    } finally {
        console.log('Generator cleanup');
    }
}

const gen = generatorWithError();
console.log(gen.next()); // { value: 1, done: false }
console.log(gen.next()); // { value: 2, done: false }
console.log(gen.throw(new Error('Test error')));
// Generator caught error: Test error
// Generator cleanup
// { value: 'Error handled', done: false }
```

**Async Generators:**

8. **Async Generator:**
```javascript
async function* asyncGenerator() {
    yield 'First';
    await new Promise(resolve => setTimeout(resolve, 1000));
    yield 'Second';
    await new Promise(resolve => setTimeout(resolve, 1000));
    yield 'Third';
}

async function consumeAsyncGenerator() {
    for await (const value of asyncGenerator()) {
        console.log(value);
    }
}

consumeAsyncGenerator();
// First (immediately)
// Second (after 1 second)
// Third (after 2 seconds)
```

9. **Data Streaming with Async Generators:**
```javascript
async function* fetchDataStream(urls) {
    for (const url of urls) {
        try {
            const response = await fetch(url);
            const data = await response.json();
            yield data;
        } catch (error) {
            yield { error: error.message, url };
        }
    }
}

async function processDataStream() {
    const urls = [
        'https://api.example.com/users',
        'https://api.example.com/posts',
        'https://api.example.com/comments'
    ];
    
    for await (const data of fetchDataStream(urls)) {
        if (data.error) {
            console.error('Error fetching data:', data.error);
        } else {
            console.log('Data received:', data);
        }
    }
}

processDataStream();
```

**Practical Use Cases:**

10. **State Machine with Generator:**
```javascript
function* stateMachine() {
    let state = 'idle';
    
    while (true) {
        const action = yield state;
        
        switch (state) {
            case 'idle':
                if (action === 'start') state = 'running';
                break;
            case 'running':
                if (action === 'pause') state = 'paused';
                else if (action === 'stop') state = 'stopped';
                break;
            case 'paused':
                if (action === 'resume') state = 'running';
                else if (action === 'stop') state = 'stopped';
                break;
            case 'stopped':
                if (action === 'reset') state = 'idle';
                break;
        }
    }
}

const machine = stateMachine();
machine.next(); // Initialize
console.log(machine.next('start').value); // 'running'
console.log(machine.next('pause').value); // 'paused'
console.log(machine.next('resume').value); // 'running'
console.log(machine.next('stop').value); // 'stopped'
```

11. **Generator for Pagination:**
```javascript
async function* paginatedData(baseUrl, pageSize = 10) {
    let page = 1;
    let hasMore = true;
    
    while (hasMore) {
        const url = `${baseUrl}?page=${page}&size=${pageSize}`;
        const response = await fetch(url);
        const data = await response.json();
        
        yield data.items;
        
        hasMore = data.hasMore;
        page++;
    }
}

async function processAllPages() {
    for await (const page of paginatedData('/api/data')) {
        console.log('Processing page:', page);
        // Process each page
    }
}

processAllPages();
```

**Generator Delegation:**

12. **Generator Delegation with yield*:**
```javascript
function* generator1() {
    yield 1;
    yield 2;
}

function* generator2() {
    yield 3;
    yield 4;
}

function* combinedGenerator() {
    yield* generator1();
    yield* generator2();
    yield 5;
}

console.log([...combinedGenerator()]); // [1, 2, 3, 4, 5]
```

13. **Recursive Generator:**
```javascript
function* treeTraversal(node) {
    if (node) {
        yield node.value;
        yield* treeTraversal(node.left);
        yield* treeTraversal(node.right);
    }
}

const tree = {
    value: 1,
    left: {
        value: 2,
        left: { value: 4, left: null, right: null },
        right: { value: 5, left: null, right: null }
    },
    right: {
        value: 3,
        left: { value: 6, left: null, right: null },
        right: { value: 7, left: null, right: null }
    }
};

console.log([...treeTraversal(tree)]); // [1, 2, 4, 5, 3, 6, 7]
```

**Best Practices:**
- Use generators for creating custom iterators
- Use async generators for handling asynchronous data streams
- Use generators for state machines and coroutines
- Consider performance implications of generator functions
- Use generator delegation (yield*) for composition
- Handle errors properly in generator functions
- Use generators for lazy evaluation of sequences
- Consider using generators for pagination and data processing
- Test generator behavior thoroughly
- Document generator function behavior and expected inputs

### 56. What is the difference between WeakMap and WeakSet?
**Answer:**
WeakMap and WeakSet hold weak references to objects, allowing garbage collection when objects are no longer referenced.

**Detailed Explanation:**
WeakMap and WeakSet are specialized collections that hold weak references to objects. Unlike Map and Set, they don't prevent garbage collection of their keys/values, making them useful for metadata storage and avoiding memory leaks.

**WeakMap:**

1. **Basic WeakMap Usage:**
```javascript
const weakMap = new WeakMap();

// Create objects
const obj1 = { name: 'John' };
const obj2 = { name: 'Jane' };

// Store metadata
weakMap.set(obj1, 'Metadata for John');
weakMap.set(obj2, 'Metadata for Jane');

// Retrieve metadata
console.log(weakMap.get(obj1)); // 'Metadata for John'
console.log(weakMap.get(obj2)); // 'Metadata for Jane'

// Check if key exists
console.log(weakMap.has(obj1)); // true

// Delete entry
weakMap.delete(obj1);
console.log(weakMap.has(obj1)); // false
```

2. **WeakMap vs Map:**
```javascript
// Map - holds strong references
const map = new Map();
const obj1 = { name: 'John' };
map.set(obj1, 'data');

// WeakMap - holds weak references
const weakMap = new WeakMap();
const obj2 = { name: 'Jane' };
weakMap.set(obj2, 'data');

// Clear references
obj1 = null; // obj1 still exists in map
obj2 = null; // obj2 can be garbage collected

// Map still has the object
console.log(map.size); // 1

// WeakMap doesn't prevent garbage collection
// obj2 will be garbage collected when no other references exist
```

**WeakSet:**

3. **Basic WeakSet Usage:**
```javascript
const weakSet = new WeakSet();

// Create objects
const obj1 = { name: 'John' };
const obj2 = { name: 'Jane' };
const obj3 = { name: 'Bob' };

// Add objects to set
weakSet.add(obj1);
weakSet.add(obj2);

// Check if object is in set
console.log(weakSet.has(obj1)); // true
console.log(weakSet.has(obj3)); // false

// Remove object from set
weakSet.delete(obj1);
console.log(weakSet.has(obj1)); // false
```

4. **WeakSet vs Set:**
```javascript
// Set - holds strong references
const set = new Set();
const obj1 = { name: 'John' };
set.add(obj1);

// WeakSet - holds weak references
const weakSet = new WeakSet();
const obj2 = { name: 'Jane' };
weakSet.add(obj2);

// Clear references
obj1 = null; // obj1 still exists in set
obj2 = null; // obj2 can be garbage collected

// Set still has the object
console.log(set.size); // 1

// WeakSet doesn't prevent garbage collection
// obj2 will be garbage collected when no other references exist
```

**Key Differences:**

5. **WeakMap vs Map:**
```javascript
// Map
const map = new Map();
const obj = { name: 'John' };
map.set(obj, 'data');

// WeakMap
const weakMap = new WeakMap();
const obj2 = { name: 'Jane' };
weakMap.set(obj2, 'data');

// Key differences:
console.log('Map size:', map.size); // 1
// console.log('WeakMap size:', weakMap.size); // Error: size is not a function

// Map keys are enumerable
for (const [key, value] of map) {
    console.log(key, value);
}

// WeakMap keys are not enumerable
// for (const [key, value] of weakMap) { // Error: not iterable
//     console.log(key, value);
// }

// Map can use any type as key
map.set('string', 'value');
map.set(123, 'value');
map.set(true, 'value');

// WeakMap can only use objects as keys
// weakMap.set('string', 'value'); // Error: Invalid value used as weak map key
// weakMap.set(123, 'value'); // Error: Invalid value used as weak map key
```

6. **WeakSet vs Set:**
```javascript
// Set
const set = new Set();
const obj = { name: 'John' };
set.add(obj);

// WeakSet
const weakSet = new WeakSet();
const obj2 = { name: 'Jane' };
weakSet.add(obj2);

// Key differences:
console.log('Set size:', set.size); // 1
// console.log('WeakSet size:', weakSet.size); // Error: size is not a function

// Set values are enumerable
for (const value of set) {
    console.log(value);
}

// WeakSet values are not enumerable
// for (const value of weakSet) { // Error: not iterable
//     console.log(value);
// }

// Set can store any type
set.add('string');
set.add(123);
set.add(true);

// WeakSet can only store objects
// weakSet.add('string'); // Error: Invalid value used as weak set key
// weakSet.add(123); // Error: Invalid value used as weak set key
```

**Practical Use Cases:**

7. **Metadata Storage with WeakMap:**
```javascript
// Store metadata for DOM elements
const elementMetadata = new WeakMap();

function addMetadata(element, metadata) {
    elementMetadata.set(element, metadata);
}

function getMetadata(element) {
    return elementMetadata.get(element);
}

// Usage
const button = document.createElement('button');
addMetadata(button, { clickCount: 0, lastClicked: null });

button.addEventListener('click', () => {
    const metadata = getMetadata(button);
    metadata.clickCount++;
    metadata.lastClicked = new Date();
    console.log('Button clicked', metadata.clickCount, 'times');
});

// When button is removed from DOM, metadata is automatically cleaned up
```

8. **Object Tracking with WeakSet:**
```javascript
// Track processed objects
const processedObjects = new WeakSet();

function processObject(obj) {
    if (processedObjects.has(obj)) {
        console.log('Object already processed');
        return;
    }
    
    // Process object
    console.log('Processing object:', obj);
    processedObjects.add(obj);
}

// Usage
const obj1 = { name: 'John' };
const obj2 = { name: 'Jane' };

processObject(obj1); // Processing object: { name: 'John' }
processObject(obj1); // Object already processed
processObject(obj2); // Processing object: { name: 'Jane' }
```

9. **Cache with WeakMap:**
```javascript
// Cache computed values for objects
const cache = new WeakMap();

function expensiveComputation(obj) {
    if (cache.has(obj)) {
        console.log('Cache hit');
        return cache.get(obj);
    }
    
    console.log('Computing...');
    const result = obj.value * obj.value; // Expensive operation
    cache.set(obj, result);
    return result;
}

// Usage
const obj1 = { value: 5 };
const obj2 = { value: 10 };

console.log(expensiveComputation(obj1)); // Computing... 25
console.log(expensiveComputation(obj1)); // Cache hit 25
console.log(expensiveComputation(obj2)); // Computing... 100

// When objects are no longer referenced, cache entries are automatically cleaned up
```

10. **Event Listener Management:**
```javascript
// Track objects with event listeners
const objectsWithListeners = new WeakSet();
const listenerMetadata = new WeakMap();

function addEventListener(obj, event, handler) {
    if (!objectsWithListeners.has(obj)) {
        objectsWithListeners.add(obj);
        listenerMetadata.set(obj, []);
    }
    
    const listeners = listenerMetadata.get(obj);
    listeners.push({ event, handler });
    
    obj.addEventListener(event, handler);
}

function removeAllListeners(obj) {
    if (objectsWithListeners.has(obj)) {
        const listeners = listenerMetadata.get(obj);
        listeners.forEach(({ event, handler }) => {
            obj.removeEventListener(event, handler);
        });
        
        objectsWithListeners.delete(obj);
        listenerMetadata.delete(obj);
    }
}

// Usage
const button = document.createElement('button');
addEventListener(button, 'click', () => console.log('Clicked'));
addEventListener(button, 'mouseover', () => console.log('Mouse over'));

// When button is removed from DOM, all metadata is automatically cleaned up
```

**Memory Management:**

11. **Memory Leak Prevention:**
```javascript
// Bad: Using Map can cause memory leaks
const badCache = new Map();

function badFunction(obj) {
    if (badCache.has(obj)) {
        return badCache.get(obj);
    }
    
    const result = obj.value * 2;
    badCache.set(obj, result);
    return result;
}

// Good: Using WeakMap prevents memory leaks
const goodCache = new WeakMap();

function goodFunction(obj) {
    if (goodCache.has(obj)) {
        return goodCache.get(obj);
    }
    
    const result = obj.value * 2;
    goodCache.set(obj, result);
    return result;
}

// Usage
const obj = { value: 5 };
console.log(badFunction(obj)); // 10
console.log(goodFunction(obj)); // 10

// When obj is no longer referenced:
// - badCache still holds reference to obj (memory leak)
// - goodCache automatically releases reference to obj
```

**Best Practices:**
- Use WeakMap for object metadata storage
- Use WeakSet for object tracking and deduplication
- Use WeakMap/WeakSet to prevent memory leaks
- Don't use WeakMap/WeakSet for primitive values
- Consider WeakMap/WeakSet for caching object-related data
- Use WeakMap/WeakSet for event listener management
- Be aware that WeakMap/WeakSet are not enumerable
- Use WeakMap/WeakSet for temporary object associations
- Consider WeakMap/WeakSet for DOM element metadata
- Test WeakMap/WeakSet behavior with garbage collection

### 57. What are JavaScript decorators and how do you use them?
**Answer:**
Functions that modify or enhance other functions or classes using `@decorator` syntax.

**Detailed Explanation:**
Decorators are a design pattern that allows you to modify or enhance the behavior of functions, classes, or properties without changing their original code. They provide a clean way to add cross-cutting concerns like logging, validation, caching, and more.

**Basic Decorator Syntax:**

1. **Function Decorators:**
```javascript
// Simple decorator function
function logDecorator(target, propertyKey, descriptor) {
    const originalMethod = descriptor.value;
    
    descriptor.value = function(...args) {
        console.log(`Calling ${propertyKey} with args:`, args);
        const result = originalMethod.apply(this, args);
        console.log(`${propertyKey} returned:`, result);
        return result;
    };
    
    return descriptor;
}

// Usage with Object.defineProperty
class Calculator {
    add(a, b) {
        return a + b;
    }
}

// Apply decorator
const descriptor = Object.getOwnPropertyDescriptor(Calculator.prototype, 'add');
const decoratedDescriptor = logDecorator(Calculator.prototype, 'add', descriptor);
Object.defineProperty(Calculator.prototype, 'add', decoratedDescriptor);

const calc = new Calculator();
calc.add(2, 3); // Logs: Calling add with args: [2, 3], add returned: 5
```

2. **Class Decorators:**
```javascript
function classDecorator(target) {
    return class extends target {
        constructor(...args) {
            super(...args);
            console.log('Instance created');
        }
    };
}

// Usage
@classDecorator
class MyClass {
    constructor(name) {
        this.name = name;
    }
}

const instance = new MyClass('John'); // Logs: Instance created
```

**Advanced Decorator Patterns:**

3. **Method Decorators:**
```javascript
function timing(target, propertyKey, descriptor) {
    const originalMethod = descriptor.value;
    
    descriptor.value = function(...args) {
        const start = performance.now();
        const result = originalMethod.apply(this, args);
        const end = performance.now();
        console.log(`${propertyKey} took ${end - start} milliseconds`);
        return result;
    };
    
    return descriptor;
}

function retry(maxAttempts = 3) {
    return function(target, propertyKey, descriptor) {
        const originalMethod = descriptor.value;
        
        descriptor.value = async function(...args) {
            let lastError;
            
            for (let attempt = 1; attempt <= maxAttempts; attempt++) {
                try {
                    return await originalMethod.apply(this, args);
                } catch (error) {
                    lastError = error;
                    console.log(`Attempt ${attempt} failed:`, error.message);
                    
                    if (attempt < maxAttempts) {
                        await new Promise(resolve => setTimeout(resolve, 1000 * attempt));
                    }
                }
            }
            
            throw lastError;
        };
        
        return descriptor;
    };
}

// Usage
class ApiService {
    @timing
    @retry(3)
    async fetchData(url) {
        const response = await fetch(url);
        if (!response.ok) {
            throw new Error(`HTTP ${response.status}`);
        }
        return response.json();
    }
}
```

4. **Property Decorators:**
```javascript
function readonly(target, propertyKey, descriptor) {
    descriptor.writable = false;
    return descriptor;
}

function validate(type) {
    return function(target, propertyKey, descriptor) {
        const originalSet = descriptor.set;
        
        descriptor.set = function(value) {
            if (typeof value !== type) {
                throw new Error(`${propertyKey} must be of type ${type}`);
            }
            originalSet.call(this, value);
        };
        
        return descriptor;
    };
}

// Usage
class User {
    constructor(name, age) {
        this._name = name;
        this._age = age;
    }
    
    @readonly
    @validate('string')
    get name() {
        return this._name;
    }
    
    set name(value) {
        this._name = value;
    }
    
    @validate('number')
    get age() {
        return this._age;
    }
    
    set age(value) {
        this._age = value;
    }
}
```

**Decorator Libraries:**

5. **Using core-decorators Library:**
```javascript
// Install: npm install core-decorators
import { readonly, deprecate, debounce, throttle } from 'core-decorators';

class MyClass {
    @readonly
    get value() {
        return 'readonly value';
    }
    
    @deprecate('Use newMethod instead')
    oldMethod() {
        console.log('This is deprecated');
    }
    
    @debounce(300)
    handleInput(event) {
        console.log('Input handled:', event.target.value);
    }
    
    @throttle(1000)
    handleScroll() {
        console.log('Scroll handled');
    }
}
```

6. **Custom Decorator Factory:**
```javascript
function cache(maxSize = 100) {
    return function(target, propertyKey, descriptor) {
        const originalMethod = descriptor.value;
        const cache = new Map();
        
        descriptor.value = function(...args) {
            const key = JSON.stringify(args);
            
            if (cache.has(key)) {
                console.log('Cache hit');
                return cache.get(key);
            }
            
            const result = originalMethod.apply(this, args);
            
            if (cache.size >= maxSize) {
                const firstKey = cache.keys().next().value;
                cache.delete(firstKey);
            }
            
            cache.set(key, result);
            return result;
        };
        
        return descriptor;
    };
}

function measure(target, propertyKey, descriptor) {
    const originalMethod = descriptor.value;
    
    descriptor.value = function(...args) {
        const start = performance.now();
        const result = originalMethod.apply(this, args);
        const end = performance.now();
        
        console.log(`${propertyKey} execution time: ${end - start}ms`);
        return result;
    };
    
    return descriptor;
}

// Usage
class MathService {
    @cache(50)
    @measure
    fibonacci(n) {
        if (n <= 1) return n;
        return this.fibonacci(n - 1) + this.fibonacci(n - 2);
    }
}
```

**Practical Use Cases:**

7. **API Endpoint Decorators:**
```javascript
function apiEndpoint(method, path) {
    return function(target, propertyKey, descriptor) {
        const originalMethod = descriptor.value;
        
        descriptor.value = async function(req, res) {
            try {
                console.log(`${method} ${path} - ${propertyKey}`);
                const result = await originalMethod.call(this, req, res);
                res.json(result);
            } catch (error) {
                console.error(`Error in ${propertyKey}:`, error);
                res.status(500).json({ error: error.message });
            }
        };
        
        // Store metadata
        descriptor.value._endpoint = { method, path };
        
        return descriptor;
    };
}

function authenticate(target, propertyKey, descriptor) {
    const originalMethod = descriptor.value;
    
    descriptor.value = function(req, res, next) {
        if (!req.headers.authorization) {
            return res.status(401).json({ error: 'Authentication required' });
        }
        
        return originalMethod.call(this, req, res, next);
    };
    
    return descriptor;
}

// Usage
class UserController {
    @apiEndpoint('GET', '/users')
    async getUsers(req, res) {
        return { users: [] };
    }
    
    @apiEndpoint('POST', '/users')
    @authenticate
    async createUser(req, res) {
        return { message: 'User created' };
    }
}
```

8. **Validation Decorators:**
```javascript
function validateInput(schema) {
    return function(target, propertyKey, descriptor) {
        const originalMethod = descriptor.value;
        
        descriptor.value = function(...args) {
            const [req, res, next] = args;
            
            // Validate request body
            for (const [field, rules] of Object.entries(schema)) {
                const value = req.body[field];
                
                if (rules.required && !value) {
                    return res.status(400).json({ error: `${field} is required` });
                }
                
                if (value && rules.type && typeof value !== rules.type) {
                    return res.status(400).json({ error: `${field} must be ${rules.type}` });
                }
                
                if (value && rules.minLength && value.length < rules.minLength) {
                    return res.status(400).json({ error: `${field} must be at least ${rules.minLength} characters` });
                }
            }
            
            return originalMethod.apply(this, args);
        };
        
        return descriptor;
    };
}

// Usage
class UserController {
    @validateInput({
        name: { required: true, type: 'string', minLength: 2 },
        email: { required: true, type: 'string' },
        age: { type: 'number' }
    })
    async createUser(req, res) {
        // Validation passed, create user
        return { message: 'User created successfully' };
    }
}
```

**Best Practices:**
- Use decorators for cross-cutting concerns
- Keep decorators simple and focused
- Document decorator behavior and usage
- Consider performance implications
- Use decorators consistently across your codebase
- Test decorator behavior thoroughly
- Consider using established decorator libraries
- Use decorators for metadata and configuration
- Avoid overusing decorators for simple functionality
- Consider decorator composition and ordering

### 58. What is the difference between static and instance methods?
**Answer:**
Static methods belong to the class, instance methods belong to instances of the class.

**Detailed Explanation:**
Static and instance methods serve different purposes in object-oriented programming. Understanding their differences is crucial for designing effective class hierarchies and APIs.

**Instance Methods:**

1. **Basic Instance Methods:**
```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    
    // Instance method - operates on instance data
    greet() {
        return `Hello, I'm ${this.name} and I'm ${this.age} years old.`;
    }
    
    // Instance method - modifies instance state
    haveBirthday() {
        this.age++;
        return `Happy birthday! You are now ${this.age} years old.`;
    }
    
    // Instance method - returns instance data
    getInfo() {
        return {
            name: this.name,
            age: this.age
        };
    }
}

// Usage
const person = new Person('John', 30);
console.log(person.greet()); // Hello, I'm John and I'm 30 years old.
console.log(person.haveBirthday()); // Happy birthday! You are now 31 years old.
console.log(person.getInfo()); // { name: 'John', age: 31 }
```

2. **Instance Methods with this Context:**
```javascript
class Calculator {
    constructor() {
        this.result = 0;
    }
    
    add(value) {
        this.result += value;
        return this; // Method chaining
    }
    
    subtract(value) {
        this.result -= value;
        return this;
    }
    
    multiply(value) {
        this.result *= value;
        return this;
    }
    
    getResult() {
        return this.result;
    }
    
    reset() {
        this.result = 0;
        return this;
    }
}

// Usage
const calc = new Calculator();
const result = calc.add(5).multiply(3).subtract(2).getResult();
console.log(result); // 13
```

**Static Methods:**

3. **Basic Static Methods:**
```javascript
class MathUtils {
    // Static method - belongs to class, not instance
    static add(a, b) {
        return a + b;
    }
    
    static multiply(a, b) {
        return a * b;
    }
    
    static isEven(number) {
        return number % 2 === 0;
    }
    
    static factorial(n) {
        if (n <= 1) return 1;
        return n * MathUtils.factorial(n - 1);
    }
}

// Usage - called on class, not instance
console.log(MathUtils.add(5, 3)); // 8
console.log(MathUtils.multiply(4, 6)); // 24
console.log(MathUtils.isEven(10)); // true
console.log(MathUtils.factorial(5)); // 120

// Cannot call on instance
const math = new MathUtils();
// console.log(math.add(5, 3)); // Error: math.add is not a function
```

4. **Static Methods for Factory Patterns:**
```javascript
class User {
    constructor(name, email, role) {
        this.name = name;
        this.email = email;
        this.role = role;
    }
    
    // Static factory method
    static createAdmin(name, email) {
        return new User(name, email, 'admin');
    }
    
    static createUser(name, email) {
        return new User(name, email, 'user');
    }
    
    static createGuest() {
        return new User('Guest', 'guest@example.com', 'guest');
    }
    
    // Static method for validation
    static validateEmail(email) {
        const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        return emailRegex.test(email);
    }
    
    // Static method for data processing
    static fromJSON(jsonString) {
        const data = JSON.parse(jsonString);
        return new User(data.name, data.email, data.role);
    }
}

// Usage
const admin = User.createAdmin('John', 'john@example.com');
const user = User.createUser('Jane', 'jane@example.com');
const guest = User.createGuest();

console.log(admin.role); // admin
console.log(user.role); // user
console.log(guest.role); // guest

// Validation
console.log(User.validateEmail('test@example.com')); // true
console.log(User.validateEmail('invalid-email')); // false

// Data processing
const jsonString = '{"name":"Bob","email":"bob@example.com","role":"user"}';
const userFromJSON = User.fromJSON(jsonString);
console.log(userFromJSON.name); // Bob
```

**Key Differences:**

5. **Access and Context:**
```javascript
class Example {
    constructor(value) {
        this.value = value;
    }
    
    // Instance method - has access to 'this'
    instanceMethod() {
        console.log('Instance method called');
        console.log('this.value:', this.value);
        console.log('this instanceof Example:', this instanceof Example);
    }
    
    // Static method - no access to 'this'
    static staticMethod() {
        console.log('Static method called');
        // console.log('this.value:', this.value); // Error: this.value is undefined
        console.log('this === Example:', this === Example);
    }
}

// Usage
const instance = new Example('test');

// Instance method - called on instance
instance.instanceMethod();
// Instance method called
// this.value: test
// this instanceof Example: true

// Static method - called on class
Example.staticMethod();
// Static method called
// this === Example: true
```

6. **Memory and Performance:**
```javascript
class PerformanceExample {
    constructor(data) {
        this.data = data;
    }
    
    // Instance method - created for each instance
    processData() {
        return this.data.map(item => item * 2);
    }
    
    // Static method - shared across all instances
    static processData(data) {
        return data.map(item => item * 2);
    }
}

// Instance method - each instance has its own copy
const instance1 = new PerformanceExample([1, 2, 3]);
const instance2 = new PerformanceExample([4, 5, 6]);

console.log(instance1.processData()); // [2, 4, 6]
console.log(instance2.processData()); // [8, 10, 12]

// Static method - shared, more memory efficient
console.log(PerformanceExample.processData([1, 2, 3])); // [2, 4, 6]
console.log(PerformanceExample.processData([4, 5, 6])); // [8, 10, 12]
```

**Advanced Patterns:**

7. **Static Methods for Utilities:**
```javascript
class StringUtils {
    static capitalize(str) {
        return str.charAt(0).toUpperCase() + str.slice(1).toLowerCase();
    }
    
    static reverse(str) {
        return str.split('').reverse().join('');
    }
    
    static isPalindrome(str) {
        const cleaned = str.toLowerCase().replace(/[^a-z0-9]/g, '');
        return cleaned === cleaned.split('').reverse().join('');
    }
    
    static truncate(str, length, suffix = '...') {
        if (str.length <= length) return str;
        return str.slice(0, length - suffix.length) + suffix;
    }
}

// Usage
console.log(StringUtils.capitalize('hello')); // Hello
console.log(StringUtils.reverse('world')); // dlrow
console.log(StringUtils.isPalindrome('racecar')); // true
console.log(StringUtils.truncate('This is a long string', 10)); // This is a...
```

8. **Static Methods for Configuration:**
```javascript
class DatabaseConnection {
    static config = {
        host: 'localhost',
        port: 5432,
        database: 'mydb',
        username: 'user',
        password: 'pass'
    };
    
    static setConfig(newConfig) {
        this.config = { ...this.config, ...newConfig };
    }
    
    static getConfig() {
        return { ...this.config };
    }
    
    static createConnection() {
        return new DatabaseConnection(this.config);
    }
    
    constructor(config) {
        this.config = config;
        this.connected = false;
    }
    
    connect() {
        this.connected = true;
        console.log('Connected to database');
    }
    
    disconnect() {
        this.connected = false;
        console.log('Disconnected from database');
    }
}

// Usage
DatabaseConnection.setConfig({ host: 'production-server.com' });
const connection = DatabaseConnection.createConnection();
connection.connect();
```

**Best Practices:**
- Use instance methods for operations that need access to instance data
- Use static methods for utility functions and factory methods
- Use static methods for operations that don't need instance state
- Use static methods for configuration and setup
- Consider using static methods for performance-critical operations
- Use static methods for data validation and transformation
- Use static methods for creating instances with different configurations
- Avoid using static methods when you need access to instance state
- Use static methods for constants and configuration values
- Consider using static methods for mathematical and utility operations

### 59. What are JavaScript mixins and how do you implement them?
**Answer:**
Pattern for adding functionality to classes by combining multiple objects.

**Detailed Explanation:**
Mixins are a design pattern that allows you to add functionality to classes by combining multiple objects. They provide a way to share behavior between classes without using inheritance, making code more modular and reusable.

**Basic Mixin Pattern:**

1. **Simple Mixin:**
```javascript
// Define mixins
const LoggingMixin = {
    log(message) {
        console.log(`[${this.constructor.name}] ${message}`);
    },
    
    error(message) {
        console.error(`[${this.constructor.name}] ERROR: ${message}`);
    }
};

const ValidationMixin = {
    validateEmail(email) {
        const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        return emailRegex.test(email);
    },
    
    validateAge(age) {
        return typeof age === 'number' && age > 0 && age < 150;
    }
};

// Apply mixins to class
class User {
    constructor(name, email, age) {
        this.name = name;
        this.email = email;
        this.age = age;
    }
}

// Mix in functionality
Object.assign(User.prototype, LoggingMixin, ValidationMixin);

// Usage
const user = new User('John', 'john@example.com', 30);
user.log('User created'); // [User] User created
console.log(user.validateEmail('john@example.com')); // true
console.log(user.validateAge(30)); // true
```

2. **Mixin with Object.assign:**
```javascript
// Define mixins
const TimestampMixin = {
    getTimestamp() {
        return new Date().toISOString();
    },
    
    getAge() {
        return Date.now() - this.createdAt;
    }
};

const SerializationMixin = {
    toJSON() {
        return JSON.stringify(this);
    },
    
    fromJSON(jsonString) {
        const data = JSON.parse(jsonString);
        Object.assign(this, data);
        return this;
    }
};

// Base class
class Document {
    constructor(title, content) {
        this.title = title;
        this.content = content;
        this.createdAt = Date.now();
    }
}

// Apply mixins
Object.assign(Document.prototype, TimestampMixin, SerializationMixin);

// Usage
const doc = new Document('My Document', 'This is the content');
console.log(doc.getTimestamp()); // 2023-12-01T10:00:00.000Z
console.log(doc.toJSON()); // {"title":"My Document","content":"This is the content","createdAt":1701432000000}
```

**Advanced Mixin Patterns:**

3. **Mixin Factory:**
```javascript
function createMixin(name, methods) {
    return {
        [name]: methods,
        ...methods
    };
}

// Create mixins
const LoggingMixin = createMixin('LoggingMixin', {
    log(message) {
        console.log(`[${this.constructor.name}] ${message}`);
    },
    
    warn(message) {
        console.warn(`[${this.constructor.name}] WARNING: ${message}`);
    }
});

const CachingMixin = createMixin('CachingMixin', {
    cache: new Map(),
    
    get(key) {
        return this.cache.get(key);
    },
    
    set(key, value) {
        this.cache.set(key, value);
    },
    
    clear() {
        this.cache.clear();
    }
});

// Apply mixins
class ApiService {
    constructor(baseURL) {
        this.baseURL = baseURL;
    }
    
    async fetchData(endpoint) {
        const url = `${this.baseURL}/${endpoint}`;
        
        // Check cache first
        if (this.get(endpoint)) {
            this.log('Cache hit for ' + endpoint);
            return this.get(endpoint);
        }
        
        this.log('Fetching data from ' + url);
        const response = await fetch(url);
        const data = await response.json();
        
        // Cache the result
        this.set(endpoint, data);
        return data;
    }
}

// Mix in functionality
Object.assign(ApiService.prototype, LoggingMixin, CachingMixin);

// Usage
const api = new ApiService('https://api.example.com');
api.fetchData('users'); // [ApiService] Fetching data from https://api.example.com/users
api.fetchData('users'); // [ApiService] Cache hit for users
```

4. **Mixin with Inheritance:**
```javascript
// Base mixin class
class Mixin {
    static mixin(target) {
        Object.assign(target.prototype, this.prototype);
        return target;
    }
}

// Define mixins as classes
class LoggingMixin extends Mixin {
    log(message) {
        console.log(`[${this.constructor.name}] ${message}`);
    }
    
    error(message) {
        console.error(`[${this.constructor.name}] ERROR: ${message}`);
    }
}

class ValidationMixin extends Mixin {
    validateEmail(email) {
        const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        return emailRegex.test(email);
    }
    
    validateAge(age) {
        return typeof age === 'number' && age > 0 && age < 150;
    }
}

// Base class
class User {
    constructor(name, email, age) {
        this.name = name;
        this.email = email;
        this.age = age;
    }
}

// Apply mixins
LoggingMixin.mixin(User);
ValidationMixin.mixin(User);

// Usage
const user = new User('John', 'john@example.com', 30);
user.log('User created'); // [User] User created
console.log(user.validateEmail('john@example.com')); // true
```

**Mixin Composition:**

5. **Composing Multiple Mixins:**
```javascript
// Define mixins
const EventEmitterMixin = {
    events: {},
    
    on(event, callback) {
        if (!this.events[event]) {
            this.events[event] = [];
        }
        this.events[event].push(callback);
    },
    
    emit(event, data) {
        if (this.events[event]) {
            this.events[event].forEach(callback => callback(data));
        }
    },
    
    off(event, callback) {
        if (this.events[event]) {
            this.events[event] = this.events[event].filter(cb => cb !== callback);
        }
    }
};

const StateMixin = {
    state: {},
    
    setState(newState) {
        const oldState = { ...this.state };
        this.state = { ...this.state, ...newState };
        this.emit('stateChange', { oldState, newState: this.state });
    },
    
    getState() {
        return { ...this.state };
    }
};

const PersistenceMixin = {
    save() {
        const data = JSON.stringify(this.state);
        localStorage.setItem(this.constructor.name, data);
        this.emit('saved', this.state);
    },
    
    load() {
        const data = localStorage.getItem(this.constructor.name);
        if (data) {
            this.state = JSON.parse(data);
            this.emit('loaded', this.state);
        }
    }
};

// Compose mixins
function mixin(target, ...mixins) {
    mixins.forEach(mixin => {
        Object.assign(target.prototype, mixin);
    });
    return target;
}

// Apply mixins to class
class App {
    constructor() {
        this.load();
    }
}

mixin(App, EventEmitterMixin, StateMixin, PersistenceMixin);

// Usage
const app = new App();

app.on('stateChange', ({ oldState, newState }) => {
    console.log('State changed:', { oldState, newState });
});

app.on('saved', (state) => {
    console.log('State saved:', state);
});

app.setState({ user: 'John', theme: 'dark' });
app.save();
```

**Mixin Best Practices:**

6. **Mixin with Conflict Resolution:**
```javascript
// Mixin with conflict resolution
function mixinWithResolution(target, ...mixins) {
    mixins.forEach(mixin => {
        Object.keys(mixin).forEach(key => {
            if (target.prototype[key] && typeof target.prototype[key] === 'function') {
                // Resolve conflict by combining methods
                const existingMethod = target.prototype[key];
                const newMethod = mixin[key];
                
                target.prototype[key] = function(...args) {
                    const result1 = existingMethod.apply(this, args);
                    const result2 = newMethod.apply(this, args);
                    return result2 !== undefined ? result2 : result1;
                };
            } else {
                target.prototype[key] = mixin[key];
            }
        });
    });
    return target;
}

// Define mixins with potential conflicts
const LoggingMixin = {
    log(message) {
        console.log(`[LOG] ${message}`);
    }
};

const ErrorLoggingMixin = {
    log(message) {
        console.error(`[ERROR] ${message}`);
    }
};

// Apply mixins with conflict resolution
class Service {
    constructor(name) {
        this.name = name;
    }
    
    log(message) {
        console.log(`[${this.name}] ${message}`);
    }
}

mixinWithResolution(Service, LoggingMixin, ErrorLoggingMixin);

// Usage
const service = new Service('MyService');
service.log('Test message'); // [ERROR] Test message (last mixin wins)
```

7. **Mixin with Dependencies:**
```javascript
// Mixin with dependency checking
function mixinWithDependencies(target, mixin, dependencies = []) {
    // Check if dependencies are met
    const missingDependencies = dependencies.filter(dep => 
        !target.prototype[dep]
    );
    
    if (missingDependencies.length > 0) {
        throw new Error(`Missing dependencies: ${missingDependencies.join(', ')}`);
    }
    
    Object.assign(target.prototype, mixin);
    return target;
}

// Define mixins with dependencies
const LoggingMixin = {
    log(message) {
        console.log(`[${this.constructor.name}] ${message}`);
    }
};

const CachingMixin = {
    cache: new Map(),
    
    get(key) {
        return this.cache.get(key);
    },
    
    set(key, value) {
        this.cache.set(key, value);
    }
};

const CachedLoggingMixin = {
    log(message) {
        const cacheKey = `log_${message}`;
        if (!this.get(cacheKey)) {
            console.log(`[${this.constructor.name}] ${message}`);
            this.set(cacheKey, true);
        }
    }
};

// Apply mixins with dependencies
class ApiService {
    constructor(baseURL) {
        this.baseURL = baseURL;
    }
}

// Apply dependencies first
mixinWithDependencies(ApiService, LoggingMixin);
mixinWithDependencies(ApiService, CachingMixin);
mixinWithDependencies(ApiService, CachedLoggingMixin, ['log', 'get', 'set']);

// Usage
const api = new ApiService('https://api.example.com');
api.log('First message'); // [ApiService] First message
api.log('First message'); // (cached, not logged again)
api.log('Second message'); // [ApiService] Second message
```

**Best Practices:**
- Use mixins for cross-cutting concerns
- Keep mixins focused and single-purpose
- Document mixin dependencies and conflicts
- Use composition over inheritance when possible
- Consider using modern alternatives like decorators
- Test mixin behavior thoroughly
- Use mixins for utility functions and common behavior
- Avoid deep mixin hierarchies
- Consider using libraries like Lodash for utility mixins
- Use mixins for adding capabilities to existing classes

### 60. What is the difference between composition and inheritance?
**Answer:**
Inheritance creates "is-a" relationships, composition creates "has-a" relationships.

**Detailed Explanation:**
Inheritance and composition are two fundamental object-oriented design patterns. Understanding their differences is crucial for creating maintainable, flexible, and scalable code.

**Inheritance (Is-A Relationship):**

1. **Basic Inheritance:**
```javascript
// Base class
class Animal {
    constructor(name, species) {
        this.name = name;
        this.species = species;
    }
    
    speak() {
        return `${this.name} makes a sound`;
    }
    
    move() {
        return `${this.name} moves`;
    }
}

// Derived class
class Dog extends Animal {
    constructor(name, breed) {
        super(name, 'Canis lupus');
        this.breed = breed;
    }
    
    speak() {
        return `${this.name} barks`;
    }
    
    fetch() {
        return `${this.name} fetches the ball`;
    }
}

// Usage
const dog = new Dog('Buddy', 'Golden Retriever');
console.log(dog.speak()); // Buddy barks
console.log(dog.move()); // Buddy moves
console.log(dog.fetch()); // Buddy fetches the ball
```

2. **Inheritance Hierarchy:**
```javascript
// Base class
class Vehicle {
    constructor(make, model, year) {
        this.make = make;
        this.model = model;
        this.year = year;
    }
    
    start() {
        return `${this.make} ${this.model} is starting`;
    }
    
    stop() {
        return `${this.make} ${this.model} has stopped`;
    }
}

// Derived class
class Car extends Vehicle {
    constructor(make, model, year, doors) {
        super(make, model, year);
        this.doors = doors;
    }
    
    honk() {
        return `${this.make} ${this.model} honks`;
    }
}

// Another derived class
class Truck extends Vehicle {
    constructor(make, model, year, payload) {
        super(make, model, year);
        this.payload = payload;
    }
    
    load() {
        return `${this.make} ${this.model} is loading cargo`;
    }
}

// Usage
const car = new Car('Toyota', 'Camry', 2023, 4);
const truck = new Truck('Ford', 'F-150', 2023, 1000);

console.log(car.start()); // Toyota Camry is starting
console.log(car.honk()); // Toyota Camry honks
console.log(truck.load()); // Ford F-150 is loading cargo
```

**Composition (Has-A Relationship):**

3. **Basic Composition:**
```javascript
// Component classes
class Engine {
    constructor(type) {
        this.type = type;
        this.isRunning = false;
    }
    
    start() {
        this.isRunning = true;
        return `Engine started`;
    }
    
    stop() {
        this.isRunning = false;
        return `Engine stopped`;
    }
}

class Wheels {
    constructor(count) {
        this.count = count;
    }
    
    rotate() {
        return `Wheels rotating`;
    }
}

class Steering {
    constructor(type) {
        this.type = type;
    }
    
    turn(direction) {
        return `Turning ${direction}`;
    }
}

// Main class using composition
class Car {
    constructor(make, model, year) {
        this.make = make;
        this.model = model;
        this.year = year;
        
        // Composition - Car HAS-A Engine, Wheels, Steering
        this.engine = new Engine('V6');
        this.wheels = new Wheels(4);
        this.steering = new Steering('Power');
    }
    
    start() {
        return `${this.make} ${this.model}: ${this.engine.start()}`;
    }
    
    drive() {
        return `${this.make} ${this.model}: ${this.wheels.rotate()}`;
    }
    
    turn(direction) {
        return `${this.make} ${this.model}: ${this.steering.turn(direction)}`;
    }
}

// Usage
const car = new Car('Honda', 'Civic', 2023);
console.log(car.start()); // Honda Civic: Engine started
console.log(car.drive()); // Honda Civic: Wheels rotating
console.log(car.turn('left')); // Honda Civic: Turning left
```

4. **Composition with Interfaces:**
```javascript
// Interface-like classes
class Flyable {
    fly() {
        return 'Flying';
    }
}

class Swimmable {
    swim() {
        return 'Swimming';
    }
}

class Walkable {
    walk() {
        return 'Walking';
    }
}

// Main class using composition
class Duck {
    constructor(name) {
        this.name = name;
        
        // Composition - Duck HAS-A Flyable, Swimmable, Walkable
        this.flyable = new Flyable();
        this.swimmable = new Swimmable();
        this.walkable = new Walkable();
    }
    
    fly() {
        return `${this.name}: ${this.flyable.fly()}`;
    }
    
    swim() {
        return `${this.name}: ${this.swimmable.swim()}`;
    }
    
    walk() {
        return `${this.name}: ${this.walkable.walk()}`;
    }
}

// Usage
const duck = new Duck('Donald');
console.log(duck.fly()); // Donald: Flying
console.log(duck.swim()); // Donald: Swimming
console.log(duck.walk()); // Donald: Walking
```

**Comparison Examples:**

5. **Inheritance vs Composition:**
```javascript
// INHERITANCE APPROACH
class Animal {
    constructor(name) {
        this.name = name;
    }
    
    eat() {
        return `${this.name} is eating`;
    }
}

class Dog extends Animal {
    constructor(name, breed) {
        super(name);
        this.breed = breed;
    }
    
    bark() {
        return `${this.name} barks`;
    }
}

// COMPOSITION APPROACH
class Eater {
    eat() {
        return 'is eating';
    }
}

class Barker {
    bark() {
        return 'barks';
    }
}

class DogComposed {
    constructor(name, breed) {
        this.name = name;
        this.breed = breed;
        
        // Composition
        this.eater = new Eater();
        this.barker = new Barker();
    }
    
    eat() {
        return `${this.name} ${this.eater.eat()}`;
    }
    
    bark() {
        return `${this.name} ${this.barker.bark()}`;
    }
}

// Usage
const dogInherited = new Dog('Buddy', 'Golden Retriever');
const dogComposed = new DogComposed('Buddy', 'Golden Retriever');

console.log(dogInherited.eat()); // Buddy is eating
console.log(dogInherited.bark()); // Buddy barks

console.log(dogComposed.eat()); // Buddy is eating
console.log(dogComposed.bark()); // Buddy barks
```

**Advantages and Disadvantages:**

6. **Inheritance Advantages:**
```javascript
// Code reuse
class Shape {
    constructor(color) {
        this.color = color;
    }
    
    getColor() {
        return this.color;
    }
    
    // Abstract method (to be overridden)
    getArea() {
        throw new Error('getArea must be implemented');
    }
}

class Circle extends Shape {
    constructor(color, radius) {
        super(color);
        this.radius = radius;
    }
    
    getArea() {
        return Math.PI * this.radius * this.radius;
    }
}

class Rectangle extends Shape {
    constructor(color, width, height) {
        super(color);
        this.width = width;
        this.height = height;
    }
    
    getArea() {
        return this.width * this.height;
    }
}

// Polymorphism
const shapes = [
    new Circle('red', 5),
    new Rectangle('blue', 4, 6)
];

shapes.forEach(shape => {
    console.log(`${shape.getColor()} shape has area: ${shape.getArea()}`);
});
```

7. **Composition Advantages:**
```javascript
// Flexibility and modularity
class Logger {
    log(message) {
        console.log(`[LOG] ${message}`);
    }
}

class FileLogger extends Logger {
    log(message) {
        console.log(`[FILE] ${message}`);
    }
}

class DatabaseLogger extends Logger {
    log(message) {
        console.log(`[DB] ${message}`);
    }
}

class UserService {
    constructor(logger) {
        this.logger = logger;
    }
    
    createUser(userData) {
        this.logger.log(`Creating user: ${userData.name}`);
        // User creation logic
        return { id: 1, ...userData };
    }
}

// Usage with different loggers
const fileLogger = new FileLogger();
const dbLogger = new DatabaseLogger();

const userService1 = new UserService(fileLogger);
const userService2 = new UserService(dbLogger);

userService1.createUser({ name: 'John' }); // [FILE] Creating user: John
userService2.createUser({ name: 'Jane' }); // [DB] Creating user: Jane
```

**Best Practices:**

8. **When to Use Inheritance:**
```javascript
// Use inheritance when:
// 1. You have a clear "is-a" relationship
// 2. You need to share common behavior
// 3. You want to use polymorphism

class Employee {
    constructor(name, id) {
        this.name = name;
        this.id = id;
    }
    
    work() {
        return `${this.name} is working`;
    }
}

class Manager extends Employee {
    constructor(name, id, teamSize) {
        super(name, id);
        this.teamSize = teamSize;
    }
    
    manage() {
        return `${this.name} is managing ${this.teamSize} people`;
    }
}

class Developer extends Employee {
    constructor(name, id, language) {
        super(name, id);
        this.language = language;
    }
    
    code() {
        return `${this.name} is coding in ${this.language}`;
    }
}
```

9. **When to Use Composition:**
```javascript
// Use composition when:
// 1. You have a "has-a" relationship
// 2. You need flexibility
// 3. You want to avoid deep inheritance hierarchies

class EmailService {
    sendEmail(to, subject, body) {
        return `Email sent to ${to}: ${subject}`;
    }
}

class SMSService {
    sendSMS(to, message) {
        return `SMS sent to ${to}: ${message}`;
    }
}

class NotificationService {
    constructor(emailService, smsService) {
        this.emailService = emailService;
        this.smsService = smsService;
    }
    
    notifyUser(user, message) {
        const emailResult = this.emailService.sendEmail(user.email, 'Notification', message);
        const smsResult = this.smsService.sendSMS(user.phone, message);
        
        return { emailResult, smsResult };
    }
}

// Usage
const emailService = new EmailService();
const smsService = new SMSService();
const notificationService = new NotificationService(emailService, smsService);

const user = { email: 'user@example.com', phone: '123-456-7890' };
const result = notificationService.notifyUser(user, 'Hello!');
console.log(result);
```

**Best Practices:**
- Prefer composition over inheritance when possible
- Use inheritance for clear "is-a" relationships
- Use composition for "has-a" relationships
- Avoid deep inheritance hierarchies
- Use composition for better testability
- Use inheritance for code reuse and polymorphism
- Consider using interfaces and abstract classes
- Use composition for dependency injection
- Use inheritance for shared behavior
- Use composition for flexible behavior

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

**Detailed Explanation:**
Advanced JavaScript testing and debugging involves comprehensive strategies for ensuring code quality, performance, and reliability. This includes unit testing, integration testing, end-to-end testing, performance testing, and advanced debugging techniques.

**Testing Frameworks and Tools:**

1. **Jest Testing Framework:**
```javascript
// math.js
function add(a, b) {
    if (typeof a !== 'number' || typeof b !== 'number') {
        throw new Error('Arguments must be numbers');
    }
    return a + b;
}

function multiply(a, b) {
    return a * b;
}

// math.test.js
describe('Math Functions', () => {
    describe('add', () => {
        test('should add two numbers correctly', () => {
            expect(add(2, 3)).toBe(5);
            expect(add(-1, 1)).toBe(0);
            expect(add(0, 0)).toBe(0);
        });
        
        test('should throw error for non-number arguments', () => {
            expect(() => add('2', 3)).toThrow('Arguments must be numbers');
            expect(() => add(2, '3')).toThrow('Arguments must be numbers');
        });
        
        test('should handle edge cases', () => {
            expect(add(Number.MAX_SAFE_INTEGER, 1)).toBe(9007199254740992);
        });
    });
    
    describe('multiply', () => {
        test('should multiply two numbers correctly', () => {
            expect(multiply(2, 3)).toBe(6);
            expect(multiply(-2, 3)).toBe(-6);
            expect(multiply(0, 5)).toBe(0);
        });
    });
});
```

2. **Advanced Jest Features:**
```javascript
// async.test.js
describe('Async Operations', () => {
    test('should handle async operations', async () => {
        const result = await fetchData();
        expect(result).toBeDefined();
        expect(result.status).toBe('success');
    });
    
    test('should handle promises', () => {
        return fetchData().then(data => {
            expect(data).toBeDefined();
        });
    });
    
    test('should handle async errors', async () => {
        await expect(fetchDataWithError()).rejects.toThrow('Network error');
    });
});

// Mocking
describe('Mocking', () => {
    beforeEach(() => {
        jest.clearAllMocks();
    });
    
    test('should mock functions', () => {
        const mockFn = jest.fn();
        mockFn('test');
        
        expect(mockFn).toHaveBeenCalledWith('test');
        expect(mockFn).toHaveBeenCalledTimes(1);
    });
    
    test('should mock modules', () => {
        jest.mock('./api', () => ({
            fetchData: jest.fn().mockResolvedValue({ data: 'test' })
        }));
        
        const { fetchData } = require('./api');
        return fetchData().then(result => {
            expect(result.data).toBe('test');
        });
    });
});
```

**Advanced Testing Patterns:**

3. **Integration Testing:**
```javascript
// integration.test.js
describe('API Integration', () => {
    let server;
    
    beforeAll(async () => {
        server = await startTestServer();
    });
    
    afterAll(async () => {
        await server.close();
    });
    
    test('should create and retrieve user', async () => {
        const userData = { name: 'John', email: 'john@example.com' };
        
        // Create user
        const createResponse = await request(server)
            .post('/api/users')
            .send(userData)
            .expect(201);
        
        const userId = createResponse.body.id;
        
        // Retrieve user
        const getResponse = await request(server)
            .get(`/api/users/${userId}`)
            .expect(200);
        
        expect(getResponse.body).toMatchObject(userData);
    });
});
```

4. **End-to-End Testing with Playwright:**
```javascript
// e2e.test.js
const { test, expect } = require('@playwright/test');

test.describe('User Management', () => {
    test('should create and edit user', async ({ page }) => {
        await page.goto('/users');
        
        // Create user
        await page.click('[data-testid="create-user-btn"]');
        await page.fill('[data-testid="name-input"]', 'John Doe');
        await page.fill('[data-testid="email-input"]', 'john@example.com');
        await page.click('[data-testid="save-btn"]');
        
        // Verify user created
        await expect(page.locator('[data-testid="user-list"]')).toContainText('John Doe');
        
        // Edit user
        await page.click('[data-testid="edit-user-btn"]');
        await page.fill('[data-testid="name-input"]', 'Jane Doe');
        await page.click('[data-testid="save-btn"]');
        
        // Verify user updated
        await expect(page.locator('[data-testid="user-list"]')).toContainText('Jane Doe');
    });
});
```

**Performance Testing:**

5. **Performance Testing with Jest:**
```javascript
// performance.test.js
describe('Performance Tests', () => {
    test('should execute within time limit', () => {
        const startTime = performance.now();
        
        // Expensive operation
        const result = fibonacci(40);
        
        const endTime = performance.now();
        const executionTime = endTime - startTime;
        
        expect(executionTime).toBeLessThan(1000); // 1 second
        expect(result).toBe(102334155);
    });
    
    test('should handle large datasets efficiently', () => {
        const largeArray = Array.from({ length: 100000 }, (_, i) => i);
        
        const startTime = performance.now();
        const result = largeArray.filter(n => n % 2 === 0);
        const endTime = performance.now();
        
        expect(endTime - startTime).toBeLessThan(100); // 100ms
        expect(result.length).toBe(50000);
    });
});
```

6. **Memory Testing:**
```javascript
// memory.test.js
describe('Memory Tests', () => {
    test('should not leak memory', () => {
        const initialMemory = process.memoryUsage().heapUsed;
        
        // Create objects
        const objects = [];
        for (let i = 0; i < 10000; i++) {
            objects.push({ id: i, data: 'test' });
        }
        
        // Clear references
        objects.length = 0;
        
        // Force garbage collection
        if (global.gc) {
            global.gc();
        }
        
        const finalMemory = process.memoryUsage().heapUsed;
        const memoryIncrease = finalMemory - initialMemory;
        
        expect(memoryIncrease).toBeLessThan(1024 * 1024); // 1MB
    });
});
```

**Advanced Debugging Techniques:**

7. **Source Maps and Debugging:**
```javascript
// webpack.config.js
module.exports = {
    mode: 'development',
    devtool: 'source-map',
    entry: './src/index.js',
    output: {
        filename: 'bundle.js',
        path: path.resolve(__dirname, 'dist')
    },
    module: {
        rules: [
            {
                test: /\.js$/,
                use: {
                    loader: 'babel-loader',
                    options: {
                        presets: ['@babel/preset-env']
                    }
                }
            }
        ]
    }
};

// Debugging with breakpoints
function complexFunction(data) {
    debugger; // Breakpoint
    
    const processed = data.map(item => {
        debugger; // Conditional breakpoint
        return item * 2;
    });
    
    return processed.filter(item => item > 10);
}
```

8. **Custom Debugging Tools:**
```javascript
// debug.js
class Debugger {
    constructor() {
        this.logs = [];
        this.performance = new Map();
    }
    
    log(message, data = null) {
        const timestamp = new Date().toISOString();
        const logEntry = { timestamp, message, data };
        this.logs.push(logEntry);
        
        console.log(`[${timestamp}] ${message}`, data);
    }
    
    startTimer(name) {
        this.performance.set(name, performance.now());
    }
    
    endTimer(name) {
        const startTime = this.performance.get(name);
        if (startTime) {
            const duration = performance.now() - startTime;
            this.log(`Timer ${name} completed in ${duration}ms`);
            this.performance.delete(name);
        }
    }
    
    getLogs() {
        return this.logs;
    }
    
    clearLogs() {
        this.logs = [];
    }
}

// Usage
const debugger = new Debugger();

debugger.startTimer('data-processing');
debugger.log('Starting data processing');

// Process data
const result = processData(largeDataset);

debugger.log('Data processing completed', { resultCount: result.length });
debugger.endTimer('data-processing');
```

**Testing Best Practices:**

9. **Test Organization:**
```javascript
// tests/unit/math.test.js
describe('Math Utils', () => {
    describe('add', () => {
        test('should add positive numbers', () => {
            expect(add(2, 3)).toBe(5);
        });
        
        test('should add negative numbers', () => {
            expect(add(-2, -3)).toBe(-5);
        });
        
        test('should handle zero', () => {
            expect(add(0, 5)).toBe(5);
        });
    });
});

// tests/integration/api.test.js
describe('API Integration', () => {
    test('should handle user CRUD operations', async () => {
        // Integration test logic
    });
});

// tests/e2e/user-flow.test.js
describe('User Flow', () => {
    test('should complete user registration flow', async ({ page }) => {
        // E2E test logic
    });
});
```

10. **Test Coverage and Quality:**
```javascript
// jest.config.js
module.exports = {
    testEnvironment: 'node',
    collectCoverage: true,
    coverageDirectory: 'coverage',
    coverageReporters: ['text', 'lcov', 'html'],
    coverageThreshold: {
        global: {
            branches: 80,
            functions: 80,
            lines: 80,
            statements: 80
        }
    },
    testMatch: [
        '**/__tests__/**/*.js',
        '**/?(*.)+(spec|test).js'
    ]
};

// Custom matchers
expect.extend({
    toBeWithinRange(received, floor, ceiling) {
        const pass = received >= floor && received <= ceiling;
        if (pass) {
            return {
                message: () => `expected ${received} not to be within range ${floor} - ${ceiling}`,
                pass: true
            };
        } else {
            return {
                message: () => `expected ${received} to be within range ${floor} - ${ceiling}`,
                pass: false
            };
        }
    }
});

// Usage
test('should be within range', () => {
    expect(5).toBeWithinRange(1, 10);
});
```

**Best Practices:**
- Write tests before implementation (TDD)
- Use descriptive test names
- Keep tests simple and focused
- Mock external dependencies
- Test edge cases and error conditions
- Use proper test organization
- Monitor test coverage
- Use continuous integration
- Test performance and memory usage
- Document testing strategies
- Use appropriate testing tools for each level
- Implement proper error handling in tests
- Use test data factories for consistency
- Automate test execution
- Monitor test execution time
- Use proper assertions and matchers
- Test both happy path and error scenarios

### 72. What are JavaScript metaprogramming techniques?
**Answer:**
Techniques for writing programs that manipulate other programs, including reflection, introspection, and code generation.

**Detailed Explanation:**
Metaprogramming is the practice of writing programs that manipulate other programs. In JavaScript, this includes reflection, introspection, code generation, and dynamic program modification. These techniques enable powerful abstractions and dynamic behavior.

**Reflection and Introspection:**

1. **Object Introspection:**
```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    
    greet() {
        return `Hello, I'm ${this.name}`;
    }
    
    get info() {
        return `${this.name} is ${this.age} years old`;
    }
}

const person = new Person('John', 30);

// Introspect object properties
console.log(Object.getOwnPropertyNames(person)); // ['name', 'age']
console.log(Object.getOwnPropertyNames(Person.prototype)); // ['constructor', 'greet', 'info']

// Introspect object descriptors
const descriptor = Object.getOwnPropertyDescriptor(Person.prototype, 'info');
console.log(descriptor); // { get: [Function: get info], set: undefined, enumerable: false, configurable: true }

// Check if property exists
console.log('name' in person); // true
console.log('greet' in person); // true
console.log('toString' in person); // true (inherited)

// Get property names (including inherited)
console.log(Object.getPrototypeOf(person)); // Person {}
console.log(Object.getPrototypeOf(Object.getPrototypeOf(person))); // Object {}
```

2. **Function Introspection:**
```javascript
function exampleFunction(a, b, c = 'default') {
    return a + b + c;
}

// Get function name
console.log(exampleFunction.name); // 'exampleFunction'

// Get function length (number of parameters)
console.log(exampleFunction.length); // 2 (ignores default parameters)

// Get function source
console.log(exampleFunction.toString());
// function exampleFunction(a, b, c = 'default') {
//     return a + b + c;
// }

// Introspect function properties
console.log(Object.getOwnPropertyNames(exampleFunction));
// ['length', 'name', 'prototype']

// Check if function is constructor
console.log(typeof exampleFunction.prototype); // 'object'
console.log(exampleFunction.prototype.constructor === exampleFunction); // true
```

**Dynamic Code Generation:**

3. **Function Generation:**
```javascript
function createFunction(name, params, body) {
    const paramString = params.join(', ');
    const functionString = `function ${name}(${paramString}) { ${body} }`;
    
    return new Function('return ' + functionString)();
}

// Generate function dynamically
const addFunction = createFunction('add', ['a', 'b'], 'return a + b;');
console.log(addFunction(2, 3)); // 5

// Generate class dynamically
function createClass(name, methods) {
    const methodStrings = Object.entries(methods)
        .map(([methodName, methodBody]) => `    ${methodName}() { ${methodBody} }`)
        .join('\n');
    
    const classString = `class ${name} {\n${methodStrings}\n}`;
    
    return new Function('return ' + classString)();
}

const Calculator = createClass('Calculator', {
    add: 'return this.a + this.b;',
    subtract: 'return this.a - this.b;',
    multiply: 'return this.a * this.b;'
});

const calc = new Calculator();
calc.a = 5;
calc.b = 3;
console.log(calc.add()); // 8
console.log(calc.multiply()); // 15
```

4. **Code Generation with Templates:**
```javascript
class CodeGenerator {
    constructor() {
        this.templates = new Map();
    }
    
    addTemplate(name, template) {
        this.templates.set(name, template);
    }
    
    generate(templateName, variables) {
        const template = this.templates.get(templateName);
        if (!template) {
            throw new Error(`Template ${templateName} not found`);
        }
        
        return template.replace(/\{\{([^}]+)\}\}/g, (match, key) => {
            return variables[key.trim()] || match;
        });
    }
}

// Usage
const generator = new CodeGenerator();

generator.addTemplate('class', `
class {{className}} {
    constructor({{constructorParams}}) {
        {{constructorBody}}
    }
    
    {{methods}}
}
`);

generator.addTemplate('method', `
    {{methodName}}({{methodParams}}) {
        {{methodBody}}
    }
`);

// Generate class
const className = 'User';
const constructorParams = 'name, email';
const constructorBody = 'this.name = name;\n        this.email = email;';
const methods = generator.generate('method', {
    methodName: 'greet',
    methodParams: '',
    methodBody: 'return `Hello, I\'m ${this.name}`;'
});

const generatedClass = generator.generate('class', {
    className,
    constructorParams,
    constructorBody,
    methods
});

console.log(generatedClass);
// class User {
//     constructor(name, email) {
//         this.name = name;
//         this.email = email;
//     }
//     
//     greet() {
//         return `Hello, I'm ${this.name}`;
//     }
// }
```

**Dynamic Program Modification:**

5. **Function Wrapping:**
```javascript
function wrapFunction(originalFunction, before, after) {
    return function(...args) {
        const beforeResult = before ? before.apply(this, args) : undefined;
        const result = originalFunction.apply(this, args);
        const afterResult = after ? after.call(this, result, args) : undefined;
        
        return afterResult !== undefined ? afterResult : result;
    };
}

// Usage
function add(a, b) {
    return a + b;
}

const wrappedAdd = wrapFunction(
    add,
    (a, b) => console.log(`Adding ${a} and ${b}`),
    (result, args) => {
        console.log(`Result: ${result}`);
        return result * 2; // Modify result
    }
);

console.log(wrappedAdd(2, 3)); // Adding 2 and 3, Result: 5, 10
```

6. **Method Interception:**
```javascript
class Interceptor {
    constructor(target) {
        this.target = target;
        this.interceptors = new Map();
    }
    
    intercept(methodName, interceptor) {
        if (!this.interceptors.has(methodName)) {
            this.interceptors.set(methodName, []);
        }
        this.interceptors.get(methodName).push(interceptor);
    }
    
    createProxy() {
        return new Proxy(this.target, {
            get(target, property, receiver) {
                const originalMethod = target[property];
                
                if (typeof originalMethod === 'function' && this.interceptors.has(property)) {
                    return (...args) => {
                        const interceptors = this.interceptors.get(property);
                        
                        // Execute before interceptors
                        for (const interceptor of interceptors) {
                            if (interceptor.before) {
                                interceptor.before.apply(target, args);
                            }
                        }
                        
                        // Execute original method
                        const result = originalMethod.apply(target, args);
                        
                        // Execute after interceptors
                        for (const interceptor of interceptors) {
                            if (interceptor.after) {
                                interceptor.after.call(target, result, args);
                            }
                        }
                        
                        return result;
                    };
                }
                
                return originalMethod;
            }
        });
    }
}

// Usage
class Calculator {
    add(a, b) {
        return a + b;
    }
    
    multiply(a, b) {
        return a * b;
    }
}

const calculator = new Calculator();
const interceptor = new Interceptor(calculator);

interceptor.intercept('add', {
    before: (a, b) => console.log(`Before adding ${a} and ${b}`),
    after: (result) => console.log(`After adding, result: ${result}`)
});

const proxy = interceptor.createProxy();
console.log(proxy.add(2, 3)); // Before adding 2 and 3, After adding, result: 5, 5
```

**Advanced Metaprogramming Patterns:**

7. **Dynamic Property Access:**
```javascript
class DynamicObject {
    constructor() {
        this.data = {};
    }
    
    get(property) {
        return this.data[property];
    }
    
    set(property, value) {
        this.data[property] = value;
    }
    
    has(property) {
        return property in this.data;
    }
    
    delete(property) {
        delete this.data[property];
    }
    
    keys() {
        return Object.keys(this.data);
    }
    
    values() {
        return Object.values(this.data);
    }
    
    entries() {
        return Object.entries(this.data);
    }
}

// Usage
const obj = new DynamicObject();
obj.set('name', 'John');
obj.set('age', 30);

console.log(obj.get('name')); // John
console.log(obj.has('age')); // true
console.log(obj.keys()); // ['name', 'age']
```

8. **Code Analysis and Transformation:**
```javascript
class CodeAnalyzer {
    static analyzeFunction(fn) {
        const source = fn.toString();
        const ast = this.parseAST(source);
        
        return {
            name: fn.name,
            length: fn.length,
            source: source,
            ast: ast,
            complexity: this.calculateComplexity(ast),
            dependencies: this.extractDependencies(ast)
        };
    }
    
    static parseAST(source) {
        // Simplified AST parsing
        const functions = source.match(/function\s+\w+\s*\([^)]*\)/g) || [];
        const variables = source.match(/\b\w+\s*=/g) || [];
        const calls = source.match(/\w+\s*\(/g) || [];
        
        return {
            functions: functions.length,
            variables: variables.length,
            calls: calls.length
        };
    }
    
    static calculateComplexity(ast) {
        // Simplified complexity calculation
        return ast.functions + ast.variables + ast.calls;
    }
    
    static extractDependencies(ast) {
        // Extract function calls and variable references
        return {
            functionCalls: ast.calls,
            variableReferences: ast.variables
        };
    }
}

// Usage
function exampleFunction(a, b) {
    const result = a + b;
    console.log(result);
    return result;
}

const analysis = CodeAnalyzer.analyzeFunction(exampleFunction);
console.log(analysis);
// {
//     name: 'exampleFunction',
//     length: 2,
//     source: 'function exampleFunction(a, b) { ... }',
//     ast: { functions: 1, variables: 1, calls: 1 },
//     complexity: 3,
//     dependencies: { functionCalls: 1, variableReferences: 1 }
// }
```

**Best Practices:**
- Use metaprogramming judiciously
- Document dynamic behavior clearly
- Consider performance implications
- Use TypeScript for better type safety
- Test metaprogramming code thoroughly
- Use metaprogramming for frameworks and libraries
- Avoid overuse in application code
- Consider maintainability and readability
- Use proper error handling
- Document metaprogramming patterns
- Consider security implications
- Use metaprogramming for code generation tools
- Test edge cases and error conditions
- Use proper debugging techniques
- Consider alternative approaches when possible

### 73. How do you implement advanced JavaScript concurrency patterns?
**Answer:**
Web Workers, SharedArrayBuffer, Atomics, and advanced async patterns for concurrent programming.

**Detailed Explanation:**
Advanced JavaScript concurrency involves managing multiple execution contexts, shared memory, and complex asynchronous workflows. This includes Web Workers, SharedArrayBuffer, Atomics, and sophisticated async patterns for concurrent programming.

**Web Workers:**

1. **Basic Web Worker:**
```javascript
// main.js
const worker = new Worker('worker.js');

// Send message to worker
worker.postMessage({ type: 'CALCULATE', data: [1, 2, 3, 4, 5] });

// Listen for messages from worker
worker.onmessage = function(event) {
    console.log('Result from worker:', event.data);
};

// Handle errors
worker.onerror = function(error) {
    console.error('Worker error:', error);
};

// Terminate worker when done
setTimeout(() => {
    worker.terminate();
}, 5000);

// worker.js
self.onmessage = function(event) {
    const { type, data } = event.data;
    
    switch (type) {
        case 'CALCULATE':
            const result = data.reduce((sum, num) => sum + num, 0);
            self.postMessage({ type: 'RESULT', data: result });
            break;
        
        case 'FIBONACCI':
            const fib = fibonacci(data);
            self.postMessage({ type: 'RESULT', data: fib });
            break;
    }
};

function fibonacci(n) {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}
```

2. **Advanced Web Worker Pool:**
```javascript
class WorkerPool {
    constructor(workerScript, poolSize = navigator.hardwareConcurrency || 4) {
        this.workerScript = workerScript;
        this.poolSize = poolSize;
        this.workers = [];
        this.queue = [];
        this.busyWorkers = new Set();
        
        this.initializeWorkers();
    }
    
    initializeWorkers() {
        for (let i = 0; i < this.poolSize; i++) {
            const worker = new Worker(this.workerScript);
            worker.id = i;
            worker.busy = false;
            
            worker.onmessage = (event) => {
                this.handleWorkerMessage(worker, event);
            };
            
            this.workers.push(worker);
        }
    }
    
    handleWorkerMessage(worker, event) {
        const { taskId, result, error } = event.data;
        
        if (error) {
            this.rejectTask(taskId, error);
        } else {
            this.resolveTask(taskId, result);
        }
        
        worker.busy = false;
        this.busyWorkers.delete(worker.id);
        this.processQueue();
    }
    
    execute(task) {
        return new Promise((resolve, reject) => {
            const taskId = Date.now() + Math.random();
            const taskWithCallbacks = {
                ...task,
                taskId,
                resolve,
                reject
            };
            
            this.queue.push(taskWithCallbacks);
            this.processQueue();
        });
    }
    
    processQueue() {
        if (this.queue.length === 0) return;
        
        const availableWorker = this.workers.find(w => !w.busy);
        if (!availableWorker) return;
        
        const task = this.queue.shift();
        availableWorker.busy = true;
        this.busyWorkers.add(availableWorker.id);
        
        availableWorker.postMessage(task);
    }
    
    resolveTask(taskId, result) {
        const task = this.findTask(taskId);
        if (task) {
            task.resolve(result);
        }
    }
    
    rejectTask(taskId, error) {
        const task = this.findTask(taskId);
        if (task) {
            task.reject(error);
        }
    }
    
    findTask(taskId) {
        return this.queue.find(t => t.taskId === taskId);
    }
    
    terminate() {
        this.workers.forEach(worker => worker.terminate());
        this.workers = [];
        this.queue = [];
    }
}

// Usage
const pool = new WorkerPool('worker.js', 4);

// Execute multiple tasks
const tasks = [
    { type: 'FIBONACCI', data: 40 },
    { type: 'FIBONACCI', data: 35 },
    { type: 'FIBONACCI', data: 30 },
    { type: 'FIBONACCI', data: 25 }
];

Promise.all(tasks.map(task => pool.execute(task)))
    .then(results => {
        console.log('All results:', results);
        pool.terminate();
    });
```

**SharedArrayBuffer and Atomics:**

3. **Shared Memory with Atomics:**
```javascript
// main.js
const sharedBuffer = new SharedArrayBuffer(1024);
const sharedArray = new Int32Array(sharedBuffer);

// Initialize shared data
sharedArray[0] = 0; // Counter
sharedArray[1] = 100; // Target value

// Create workers with shared memory
const worker1 = new Worker('worker.js');
const worker2 = new Worker('worker.js');

// Send shared buffer to workers
worker1.postMessage({ sharedBuffer, workerId: 1 });
worker2.postMessage({ sharedBuffer, workerId: 2 });

// Monitor progress
const interval = setInterval(() => {
    const current = Atomics.load(sharedArray, 0);
    console.log('Current value:', current);
    
    if (current >= sharedArray[1]) {
        clearInterval(interval);
        console.log('Target reached!');
        worker1.terminate();
        worker2.terminate();
    }
}, 100);

// worker.js
self.onmessage = function(event) {
    const { sharedBuffer, workerId } = event.data;
    const sharedArray = new Int32Array(sharedBuffer);
    
    // Worker increments counter
    for (let i = 0; i < 50; i++) {
        // Atomic increment
        const current = Atomics.add(sharedArray, 0, 1);
        console.log(`Worker ${workerId} incremented to ${current + 1}`);
        
        // Simulate work
        for (let j = 0; j < 1000000; j++) {
            // Busy wait
        }
    }
};
```

4. **Atomic Operations:**
```javascript
class AtomicCounter {
    constructor(initialValue = 0) {
        this.buffer = new SharedArrayBuffer(4);
        this.counter = new Int32Array(this.buffer);
        this.counter[0] = initialValue;
    }
    
    increment() {
        return Atomics.add(this.counter, 0, 1);
    }
    
    decrement() {
        return Atomics.sub(this.counter, 0, 1);
    }
    
    get() {
        return Atomics.load(this.counter, 0);
    }
    
    set(value) {
        Atomics.store(this.counter, 0, value);
        return value;
    }
    
    compareAndSwap(expected, replacement) {
        return Atomics.compareExchange(this.counter, 0, expected, replacement);
    }
    
    exchange(value) {
        return Atomics.exchange(this.counter, 0, value);
    }
}

// Usage
const counter = new AtomicCounter(0);

// Multiple workers can safely increment
const worker1 = new Worker('worker.js');
const worker2 = new Worker('worker.js');

worker1.postMessage({ counter: counter.buffer, workerId: 1 });
worker2.postMessage({ counter: counter.buffer, workerId: 2 });
```

**Advanced Async Patterns:**

5. **Async Queue with Concurrency Control:**
```javascript
class AsyncQueue {
    constructor(concurrency = 1) {
        this.concurrency = concurrency;
        this.running = 0;
        this.queue = [];
    }
    
    async add(task) {
        return new Promise((resolve, reject) => {
            this.queue.push({ task, resolve, reject });
            this.process();
        });
    }
    
    async process() {
        if (this.running >= this.concurrency || this.queue.length === 0) {
            return;
        }
        
        this.running++;
        const { task, resolve, reject } = this.queue.shift();
        
        try {
            const result = await task();
            resolve(result);
        } catch (error) {
            reject(error);
        } finally {
            this.running--;
            this.process();
        }
    }
    
    async waitForAll() {
        while (this.running > 0 || this.queue.length > 0) {
            await new Promise(resolve => setTimeout(resolve, 10));
        }
    }
}

// Usage
const queue = new AsyncQueue(3); // Max 3 concurrent tasks

const tasks = [
    () => fetch('/api/data1'),
    () => fetch('/api/data2'),
    () => fetch('/api/data3'),
    () => fetch('/api/data4'),
    () => fetch('/api/data5')
];

// Add all tasks
const promises = tasks.map(task => queue.add(task));

// Wait for all to complete
Promise.all(promises)
    .then(results => {
        console.log('All tasks completed:', results);
    })
    .catch(error => {
        console.error('Task failed:', error);
    });
```

6. **Semaphore for Resource Control:**
```javascript
class Semaphore {
    constructor(count) {
        this.count = count;
        this.waiting = [];
    }
    
    async acquire() {
        return new Promise((resolve) => {
            if (this.count > 0) {
                this.count--;
                resolve();
            } else {
                this.waiting.push(resolve);
            }
        });
    }
    
    release() {
        if (this.waiting.length > 0) {
            const resolve = this.waiting.shift();
            resolve();
        } else {
            this.count++;
        }
    }
}

// Usage
const semaphore = new Semaphore(2); // Allow 2 concurrent operations

async function limitedOperation(id) {
    await semaphore.acquire();
    
    try {
        console.log(`Operation ${id} started`);
        await new Promise(resolve => setTimeout(resolve, 1000));
        console.log(`Operation ${id} completed`);
    } finally {
        semaphore.release();
    }
}

// Run multiple operations
for (let i = 0; i < 5; i++) {
    limitedOperation(i);
}
```

**Best Practices:**
- Use Web Workers for CPU-intensive tasks
- Implement proper error handling in workers
- Use SharedArrayBuffer for high-performance data sharing
- Implement proper synchronization with Atomics
- Use semaphores for resource control
- Implement proper cleanup and termination
- Monitor worker performance and memory usage
- Use appropriate concurrency levels
- Implement proper error recovery
- Use proper debugging techniques for concurrent code
- Consider using libraries like Comlink for easier worker communication
- Implement proper testing for concurrent code
- Use proper logging and monitoring
- Consider using WebAssembly for performance-critical tasks
- Implement proper resource management
- Use appropriate data structures for concurrent access

### 74. What are JavaScript memory management techniques?
**Answer:**
Garbage collection, memory profiling, weak references, and advanced memory optimization strategies.

**Detailed Explanation:**
JavaScript memory management involves understanding garbage collection, memory profiling, weak references, and implementing strategies to optimize memory usage. This is crucial for building high-performance applications and avoiding memory leaks.

**Garbage Collection:**

1. **Understanding Garbage Collection:**
```javascript
// Objects become eligible for garbage collection when no references exist
function createObject() {
    const obj = { data: 'large data' };
    return obj;
}

// obj is eligible for GC after function returns
const myObj = createObject();
myObj = null; // Now eligible for GC

// Circular references can prevent GC
function createCircularReference() {
    const obj1 = { name: 'obj1' };
    const obj2 = { name: 'obj2' };
    
    obj1.ref = obj2;
    obj2.ref = obj1;
    
    return obj1;
}

// These objects reference each other, preventing GC
const circular = createCircularReference();
// To allow GC, break the circular reference
circular.ref = null;
```

2. **Memory Leak Prevention:**
```javascript
class EventManager {
    constructor() {
        this.listeners = new Map();
    }
    
    addEventListener(element, event, handler) {
        if (!this.listeners.has(element)) {
            this.listeners.set(element, []);
        }
        
        this.listeners.get(element).push({ event, handler });
        element.addEventListener(event, handler);
    }
    
    removeEventListener(element, event, handler) {
        if (this.listeners.has(element)) {
            const handlers = this.listeners.get(element);
            const index = handlers.findIndex(h => h.event === event && h.handler === handler);
            
            if (index !== -1) {
                handlers.splice(index, 1);
                element.removeEventListener(event, handler);
            }
        }
    }
    
    removeAllListeners(element) {
        if (this.listeners.has(element)) {
            const handlers = this.listeners.get(element);
            handlers.forEach(({ event, handler }) => {
                element.removeEventListener(event, handler);
            });
            this.listeners.delete(element);
        }
    }
    
    cleanup() {
        this.listeners.forEach((handlers, element) => {
            handlers.forEach(({ event, handler }) => {
                element.removeEventListener(event, handler);
            });
        });
        this.listeners.clear();
    }
}

// Usage
const eventManager = new EventManager();
const button = document.getElementById('myButton');

const handler = () => console.log('Button clicked');
eventManager.addEventListener(button, 'click', handler);

// Later, remove listener to prevent memory leak
eventManager.removeEventListener(button, 'click', handler);
```

**Memory Profiling:**

3. **Memory Usage Monitoring:**
```javascript
class MemoryMonitor {
    constructor() {
        this.snapshots = [];
        this.intervalId = null;
    }
    
    startMonitoring(interval = 1000) {
        this.intervalId = setInterval(() => {
            this.takeSnapshot();
        }, interval);
    }
    
    stopMonitoring() {
        if (this.intervalId) {
            clearInterval(this.intervalId);
            this.intervalId = null;
        }
    }
    
    takeSnapshot() {
        const snapshot = {
            timestamp: Date.now(),
            memory: process.memoryUsage(),
            heapUsed: process.memoryUsage().heapUsed,
            heapTotal: process.memoryUsage().heapTotal,
            external: process.memoryUsage().external
        };
        
        this.snapshots.push(snapshot);
        
        // Keep only last 100 snapshots
        if (this.snapshots.length > 100) {
            this.snapshots.shift();
        }
        
        return snapshot;
    }
    
    getMemoryTrend() {
        if (this.snapshots.length < 2) return null;
        
        const first = this.snapshots[0];
        const last = this.snapshots[this.snapshots.length - 1];
        
        return {
            heapUsedChange: last.heapUsed - first.heapUsed,
            heapTotalChange: last.heapTotal - first.heapTotal,
            timeSpan: last.timestamp - first.timestamp
        };
    }
    
    detectMemoryLeak() {
        const trend = this.getMemoryTrend();
        if (!trend) return false;
        
        // Consider it a leak if heap usage increases by more than 10MB over time
        return trend.heapUsedChange > 10 * 1024 * 1024;
    }
}

// Usage
const monitor = new MemoryMonitor();
monitor.startMonitoring(5000); // Check every 5 seconds

// Later, check for memory leaks
setTimeout(() => {
    if (monitor.detectMemoryLeak()) {
        console.warn('Potential memory leak detected!');
    }
    monitor.stopMonitoring();
}, 60000);
```

**Weak References:**

4. **WeakMap and WeakSet Usage:**
```javascript
// WeakMap for metadata storage
const elementMetadata = new WeakMap();

function addMetadata(element, metadata) {
    elementMetadata.set(element, metadata);
}

function getMetadata(element) {
    return elementMetadata.get(element);
}

// Usage
const button = document.createElement('button');
addMetadata(button, { clickCount: 0, lastClicked: null });

button.addEventListener('click', () => {
    const metadata = getMetadata(button);
    metadata.clickCount++;
    metadata.lastClicked = new Date();
});

// When button is removed from DOM, metadata is automatically cleaned up

// WeakSet for object tracking
const processedObjects = new WeakSet();

function processObject(obj) {
    if (processedObjects.has(obj)) {
        console.log('Object already processed');
        return;
    }
    
    console.log('Processing object:', obj);
    processedObjects.add(obj);
}

// Usage
const obj1 = { name: 'John' };
const obj2 = { name: 'Jane' };

processObject(obj1); // Processing object: { name: 'John' }
processObject(obj1); // Object already processed
processObject(obj2); // Processing object: { name: 'Jane' }
```

5. **WeakRef for Advanced Memory Management:**
```javascript
class WeakRefCache {
    constructor() {
        this.cache = new Map();
    }
    
    set(key, value) {
        const weakRef = new WeakRef(value);
        this.cache.set(key, weakRef);
    }
    
    get(key) {
        const weakRef = this.cache.get(key);
        if (!weakRef) return undefined;
        
        const value = weakRef.deref();
        if (value === undefined) {
            // Object was garbage collected
            this.cache.delete(key);
            return undefined;
        }
        
        return value;
    }
    
    has(key) {
        return this.get(key) !== undefined;
    }
    
    cleanup() {
        // Remove entries for garbage collected objects
        for (const [key, weakRef] of this.cache.entries()) {
            if (weakRef.deref() === undefined) {
                this.cache.delete(key);
            }
        }
    }
}

// Usage
const cache = new WeakRefCache();

const obj1 = { data: 'large data 1' };
const obj2 = { data: 'large data 2' };

cache.set('key1', obj1);
cache.set('key2', obj2);

console.log(cache.get('key1')); // { data: 'large data 1' }

// Remove reference to obj1
obj1 = null;

// Force garbage collection (if available)
if (global.gc) {
    global.gc();
}

// obj1 may be garbage collected, so cache.get('key1') might return undefined
console.log(cache.get('key1')); // undefined (if GC occurred)
```

**Advanced Memory Optimization:**

6. **Object Pool Pattern:**
```javascript
class ObjectPool {
    constructor(createFn, resetFn, initialSize = 10) {
        this.createFn = createFn;
        this.resetFn = resetFn;
        this.pool = [];
        
        // Pre-populate pool
        for (let i = 0; i < initialSize; i++) {
            this.pool.push(this.createFn());
        }
    }
    
    acquire() {
        if (this.pool.length > 0) {
            return this.pool.pop();
        }
        
        // Create new object if pool is empty
        return this.createFn();
    }
    
    release(obj) {
        this.resetFn(obj);
        this.pool.push(obj);
    }
    
    size() {
        return this.pool.length;
    }
}

// Usage
const particlePool = new ObjectPool(
    () => ({ x: 0, y: 0, vx: 0, vy: 0, active: false }),
    (particle) => {
        particle.x = 0;
        particle.y = 0;
        particle.vx = 0;
        particle.vy = 0;
        particle.active = false;
    }
);

// Use particles
const particle1 = particlePool.acquire();
particle1.x = 100;
particle1.y = 100;
particle1.active = true;

// Later, release particle back to pool
particlePool.release(particle1);
```

7. **Memory-Efficient Data Structures:**
```javascript
class CompactArray {
    constructor(initialCapacity = 16) {
        this.buffer = new ArrayBuffer(initialCapacity * 4); // 4 bytes per int
        this.view = new Int32Array(this.buffer);
        this.length = 0;
    }
    
    push(value) {
        if (this.length >= this.view.length) {
            this.resize();
        }
        
        this.view[this.length] = value;
        this.length++;
    }
    
    get(index) {
        if (index < 0 || index >= this.length) {
            throw new Error('Index out of bounds');
        }
        return this.view[index];
    }
    
    resize() {
        const newCapacity = this.view.length * 2;
        const newBuffer = new ArrayBuffer(newCapacity * 4);
        const newView = new Int32Array(newBuffer);
        
        // Copy existing data
        for (let i = 0; i < this.length; i++) {
            newView[i] = this.view[i];
        }
        
        this.buffer = newBuffer;
        this.view = newView;
    }
    
    clear() {
        this.length = 0;
    }
}

// Usage
const compactArray = new CompactArray();
for (let i = 0; i < 1000; i++) {
    compactArray.push(i);
}

console.log(compactArray.get(0)); // 0
console.log(compactArray.get(999)); // 999
```

**Best Practices:**
- Use WeakMap/WeakSet for metadata storage
- Implement proper cleanup in event listeners
- Use object pools for frequently created objects
- Monitor memory usage in production
- Avoid circular references
- Use compact data structures when possible
- Implement proper resource management
- Use WeakRef for advanced memory management
- Profile memory usage regularly
- Implement proper error handling
- Use appropriate data structures
- Consider memory implications of algorithms
- Implement proper testing for memory leaks
- Use proper debugging tools
- Consider using WebAssembly for memory-intensive operations
- Implement proper logging and monitoring
- Use appropriate garbage collection strategies
- Consider using memory-efficient libraries
- Implement proper resource cleanup
- Use appropriate caching strategies

### 75. How do you implement advanced JavaScript security measures?
**Answer:**
Content Security Policy, XSS prevention, CSRF protection, and secure coding practices.

**Detailed Explanation:**
Advanced JavaScript security involves implementing comprehensive security measures to protect applications from various attacks. This includes Content Security Policy, XSS prevention, CSRF protection, and following secure coding practices.

**Content Security Policy (CSP):**

1. **Basic CSP Implementation:**
```javascript
// Set CSP header
function setCSPHeader() {
    const csp = [
        "default-src 'self'",
        "script-src 'self' 'unsafe-inline' https://trusted-cdn.com",
        "style-src 'self' 'unsafe-inline' https://fonts.googleapis.com",
        "img-src 'self' data: https://trusted-images.com",
        "connect-src 'self' https://api.trusted.com",
        "font-src 'self' https://fonts.gstatic.com",
        "object-src 'none'",
        "base-uri 'self'",
        "form-action 'self'"
    ].join('; ');
    
    return {
        'Content-Security-Policy': csp,
        'X-Content-Type-Options': 'nosniff',
        'X-Frame-Options': 'DENY',
        'X-XSS-Protection': '1; mode=block'
    };
}

// Usage in Express.js
app.use((req, res, next) => {
    const securityHeaders = setCSPHeader();
    Object.entries(securityHeaders).forEach(([key, value]) => {
        res.setHeader(key, value);
    });
    next();
});
```

2. **Dynamic CSP with Nonces:**
```javascript
const crypto = require('crypto');

class CSPManager {
    constructor() {
        this.nonces = new Map();
    }
    
    generateNonce() {
        return crypto.randomBytes(16).toString('base64');
    }
    
    getCSPHeader() {
        const nonce = this.generateNonce();
        this.nonces.set('script', nonce);
        
        const csp = [
            "default-src 'self'",
            `script-src 'self' 'nonce-${nonce}'`,
            "style-src 'self' 'unsafe-inline'",
            "img-src 'self' data:",
            "connect-src 'self'"
        ].join('; ');
        
        return csp;
    }
    
    getNonce(type) {
        return this.nonces.get(type);
    }
}

// Usage
const cspManager = new CSPManager();
const csp = cspManager.getCSPHeader();
const nonce = cspManager.getNonce('script');

// In HTML template
const html = `
    <script nonce="${nonce}">
        // This script will be allowed by CSP
        console.log('Script executed');
    </script>
`;
```

**XSS Prevention:**

3. **Input Sanitization:**
```javascript
class XSSProtection {
    static sanitizeHTML(input) {
        const allowedTags = ['b', 'i', 'em', 'strong', 'p', 'br'];
        const allowedAttributes = ['class', 'id'];
        
        // Remove script tags and event handlers
        let sanitized = input
            .replace(/<script\b[^<]*(?:(?!<\/script>)<[^<]*)*<\/script>/gi, '')
            .replace(/on\w+\s*=\s*["'][^"']*["']/gi, '')
            .replace(/javascript:/gi, '')
            .replace(/vbscript:/gi, '')
            .replace(/data:/gi, '');
        
        // Remove disallowed tags
        const tagRegex = /<\/?([a-zA-Z][a-zA-Z0-9]*)\b[^<>]*>/gi;
        sanitized = sanitized.replace(tagRegex, (match, tagName) => {
            if (allowedTags.includes(tagName.toLowerCase())) {
                return match;
            }
            return '';
        });
        
        return sanitized;
    }
    
    static escapeHTML(input) {
        const map = {
            '&': '&amp;',
            '<': '&lt;',
            '>': '&gt;',
            '"': '&quot;',
            "'": '&#x27;',
            '/': '&#x2F;'
        };
        
        return input.replace(/[&<>"'\/]/g, (char) => map[char]);
    }
    
    static validateInput(input, type) {
        switch (type) {
            case 'email':
                const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
                return emailRegex.test(input);
            
            case 'url':
                try {
                    const url = new URL(input);
                    return ['http:', 'https:'].includes(url.protocol);
                } catch {
                    return false;
                }
            
            case 'alphanumeric':
                return /^[a-zA-Z0-9]+$/.test(input);
            
            default:
                return true;
        }
    }
}

// Usage
const userInput = '<script>alert("XSS")</script><p>Hello World</p>';
const sanitized = XSSProtection.sanitizeHTML(userInput);
console.log(sanitized); // <p>Hello World</p>

const escaped = XSSProtection.escapeHTML('<script>alert("XSS")</script>');
console.log(escaped); // &lt;script&gt;alert(&quot;XSS&quot;)&lt;/script&gt;
```

4. **Safe DOM Manipulation:**
```javascript
class SafeDOM {
    static createElement(tagName, attributes = {}, textContent = '') {
        const element = document.createElement(tagName);
        
        // Set attributes safely
        Object.entries(attributes).forEach(([key, value]) => {
            if (this.isSafeAttribute(key, value)) {
                element.setAttribute(key, value);
            }
        });
        
        // Set text content safely
        if (textContent) {
            element.textContent = textContent;
        }
        
        return element;
    }
    
    static isSafeAttribute(name, value) {
        const dangerousAttributes = ['onclick', 'onload', 'onerror', 'onmouseover'];
        const dangerousValues = ['javascript:', 'vbscript:', 'data:'];
        
        if (dangerousAttributes.includes(name.toLowerCase())) {
            return false;
        }
        
        if (dangerousValues.some(dangerous => value.toLowerCase().includes(dangerous))) {
            return false;
        }
        
        return true;
    }
    
    static safeInnerHTML(element, html) {
        // Create a temporary element to parse HTML
        const temp = document.createElement('div');
        temp.innerHTML = html;
        
        // Remove dangerous elements
        const dangerousElements = temp.querySelectorAll('script, iframe, object, embed');
        dangerousElements.forEach(el => el.remove());
        
        // Remove dangerous attributes
        const allElements = temp.querySelectorAll('*');
        allElements.forEach(el => {
            const attributes = Array.from(el.attributes);
            attributes.forEach(attr => {
                if (!this.isSafeAttribute(attr.name, attr.value)) {
                    el.removeAttribute(attr.name);
                }
            });
        });
        
        element.innerHTML = temp.innerHTML;
    }
}

// Usage
const safeElement = SafeDOM.createElement('div', {
    class: 'safe-div',
    id: 'safe-id'
}, 'Safe content');

document.body.appendChild(safeElement);
```

**CSRF Protection:**

5. **CSRF Token Implementation:**
```javascript
const crypto = require('crypto');

class CSRFProtection {
    constructor() {
        this.tokens = new Map();
        this.secret = crypto.randomBytes(32).toString('hex');
    }
    
    generateToken(sessionId) {
        const token = crypto.randomBytes(32).toString('hex');
        this.tokens.set(sessionId, {
            token,
            timestamp: Date.now()
        });
        return token;
    }
    
    validateToken(sessionId, token) {
        const stored = this.tokens.get(sessionId);
        if (!stored) return false;
        
        // Check if token is expired (1 hour)
        const isExpired = Date.now() - stored.timestamp > 3600000;
        if (isExpired) {
            this.tokens.delete(sessionId);
            return false;
        }
        
        return stored.token === token;
    }
    
    invalidateToken(sessionId) {
        this.tokens.delete(sessionId);
    }
}

// Usage in Express.js
const csrf = new CSRFProtection();

app.use((req, res, next) => {
    const sessionId = req.sessionID;
    const token = csrf.generateToken(sessionId);
    res.locals.csrfToken = token;
    next();
});

app.post('/api/data', (req, res) => {
    const sessionId = req.sessionID;
    const token = req.body.csrfToken;
    
    if (!csrf.validateToken(sessionId, token)) {
        return res.status(403).json({ error: 'Invalid CSRF token' });
    }
    
    // Process request
    res.json({ success: true });
});
```

6. **SameSite Cookie Protection:**
```javascript
// Set secure cookies
function setSecureCookie(res, name, value, options = {}) {
    const defaultOptions = {
        httpOnly: true,
        secure: process.env.NODE_ENV === 'production',
        sameSite: 'strict',
        maxAge: 3600000 // 1 hour
    };
    
    const cookieOptions = { ...defaultOptions, ...options };
    res.cookie(name, value, cookieOptions);
}

// Usage
app.post('/login', (req, res) => {
    // Authenticate user
    const sessionId = generateSessionId();
    setSecureCookie(res, 'sessionId', sessionId);
    res.json({ success: true });
});
```

**Secure Coding Practices:**

7. **Input Validation and Sanitization:**
```javascript
class SecurityValidator {
    static validateUserInput(input, rules) {
        const errors = [];
        
        for (const [field, rule] of Object.entries(rules)) {
            const value = input[field];
            
            if (rule.required && !value) {
                errors.push(`${field} is required`);
                continue;
            }
            
            if (value && rule.type && typeof value !== rule.type) {
                errors.push(`${field} must be ${rule.type}`);
                continue;
            }
            
            if (value && rule.minLength && value.length < rule.minLength) {
                errors.push(`${field} must be at least ${rule.minLength} characters`);
                continue;
            }
            
            if (value && rule.maxLength && value.length > rule.maxLength) {
                errors.push(`${field} must be no more than ${rule.maxLength} characters`);
                continue;
            }
            
            if (value && rule.pattern && !rule.pattern.test(value)) {
                errors.push(`${field} format is invalid`);
                continue;
            }
        }
        
        return {
            isValid: errors.length === 0,
            errors
        };
    }
    
    static sanitizeObject(obj) {
        const sanitized = {};
        
        for (const [key, value] of Object.entries(obj)) {
            if (typeof value === 'string') {
                sanitized[key] = XSSProtection.escapeHTML(value);
            } else if (typeof value === 'object' && value !== null) {
                sanitized[key] = this.sanitizeObject(value);
            } else {
                sanitized[key] = value;
            }
        }
        
        return sanitized;
    }
}

// Usage
const userData = {
    name: '<script>alert("XSS")</script>John',
    email: 'john@example.com',
    age: 30
};

const rules = {
    name: { required: true, type: 'string', minLength: 2, maxLength: 50 },
    email: { required: true, type: 'string', pattern: /^[^\s@]+@[^\s@]+\.[^\s@]+$/ },
    age: { required: true, type: 'number', min: 18, max: 120 }
};

const validation = SecurityValidator.validateUserInput(userData, rules);
if (!validation.isValid) {
    console.log('Validation errors:', validation.errors);
}

const sanitized = SecurityValidator.sanitizeObject(userData);
console.log(sanitized); // { name: '&lt;script&gt;alert(&quot;XSS&quot;)&lt;/script&gt;John', ... }
```

8. **Secure API Endpoints:**
```javascript
class SecureAPI {
    static rateLimit(requests, windowMs) {
        const requests = new Map();
        
        return (req, res, next) => {
            const clientId = req.ip;
            const now = Date.now();
            
            if (!requests.has(clientId)) {
                requests.set(clientId, []);
            }
            
            const clientRequests = requests.get(clientId);
            
            // Remove old requests
            const validRequests = clientRequests.filter(
                timestamp => now - timestamp < windowMs
            );
            
            if (validRequests.length >= requests) {
                return res.status(429).json({ error: 'Too many requests' });
            }
            
            validRequests.push(now);
            requests.set(clientId, validRequests);
            
            next();
        };
    }
    
    static validateAPIKey(req, res, next) {
        const apiKey = req.headers['x-api-key'];
        
        if (!apiKey) {
            return res.status(401).json({ error: 'API key required' });
        }
        
        // Validate API key (implement your validation logic)
        if (!this.isValidAPIKey(apiKey)) {
            return res.status(401).json({ error: 'Invalid API key' });
        }
        
        next();
    }
    
    static isValidAPIKey(apiKey) {
        // Implement your API key validation logic
        return apiKey.length === 32 && /^[a-f0-9]+$/.test(apiKey);
    }
}

// Usage
app.use('/api', SecureAPI.rateLimit(100, 60000)); // 100 requests per minute
app.use('/api', SecureAPI.validateAPIKey);

app.get('/api/data', (req, res) => {
    res.json({ data: 'secure data' });
});
```

**Best Practices:**
- Implement Content Security Policy (CSP)
- Use HTTPS in production
- Validate and sanitize all inputs
- Implement proper authentication and authorization
- Use secure cookies with appropriate flags
- Implement rate limiting
- Use proper error handling without information disclosure
- Keep dependencies updated
- Implement proper logging and monitoring
- Use secure coding practices
- Implement proper session management
- Use appropriate security headers
- Implement proper input validation
- Use secure communication protocols
- Implement proper access controls
- Use secure data storage practices
- Implement proper error handling
- Use security testing tools
- Implement proper backup and recovery procedures
- Use secure development practices
- Implement proper security monitoring

### 76. What are JavaScript performance profiling techniques?
**Answer:**
Chrome DevTools profiling, memory snapshots, performance monitoring, and optimization strategies.

**Detailed Explanation:**
JavaScript performance profiling involves analyzing and optimizing code execution, memory usage, and runtime performance. This includes using browser DevTools, performance monitoring tools, and implementing optimization strategies.

**Chrome DevTools Profiling:**

1. **Performance Tab Usage:**
```javascript
// Example code for profiling
function expensiveOperation() {
    const start = performance.now();
    
    // Simulate expensive operation
    let result = 0;
    for (let i = 0; i < 1000000; i++) {
        result += Math.sqrt(i);
    }
    
    const end = performance.now();
    console.log(`Operation took ${end - start} milliseconds`);
    
    return result;
}

// Profile this function in Chrome DevTools
// 1. Open DevTools (F12)
// 2. Go to Performance tab
// 3. Click Record
// 4. Call expensiveOperation()
// 5. Stop recording
// 6. Analyze the flame graph

expensiveOperation();
```

2. **Memory Tab Analysis:**
```javascript
// Memory leak example
class MemoryLeakExample {
    constructor() {
        this.data = new Array(1000000).fill('data');
        this.listeners = [];
    }
    
    addListener(callback) {
        this.listeners.push(callback);
    }
    
    // This method doesn't remove listeners, causing memory leak
    triggerEvent() {
        this.listeners.forEach(callback => callback());
    }
}

// Profile memory usage
// 1. Open DevTools
// 2. Go to Memory tab
// 3. Take heap snapshot
// 4. Create objects and take another snapshot
// 5. Compare snapshots to find memory leaks

const leakExample = new MemoryLeakExample();
leakExample.addListener(() => console.log('Event triggered'));
leakExample.triggerEvent();
```

**Performance Monitoring:**

3. **Performance Observer API:**
```javascript
class PerformanceMonitor {
    constructor() {
        this.observer = new PerformanceObserver((list) => {
            list.getEntries().forEach(entry => {
                this.handleEntry(entry);
            });
        });
        
        this.observer.observe({ entryTypes: ['measure', 'navigation', 'resource'] });
    }
    
    handleEntry(entry) {
        switch (entry.entryType) {
            case 'measure':
                console.log(`Custom measure: ${entry.name} - ${entry.duration}ms`);
                break;
            
            case 'navigation':
                console.log(`Page load: ${entry.loadEventEnd - entry.loadEventStart}ms`);
                break;
            
            case 'resource':
                console.log(`Resource loaded: ${entry.name} - ${entry.duration}ms`);
                break;
        }
    }
    
    measure(name, fn) {
        performance.mark(`${name}-start`);
        const result = fn();
        performance.mark(`${name}-end`);
        performance.measure(name, `${name}-start`, `${name}-end`);
        return result;
    }
    
    async measureAsync(name, fn) {
        performance.mark(`${name}-start`);
        const result = await fn();
        performance.mark(`${name}-end`);
        performance.measure(name, `${name}-start`, `${name}-end`);
        return result;
    }
}

// Usage
const monitor = new PerformanceMonitor();

// Measure synchronous function
const result = monitor.measure('sync-operation', () => {
    return expensiveOperation();
});

// Measure asynchronous function
monitor.measureAsync('async-operation', async () => {
    const response = await fetch('/api/data');
    return response.json();
});
```

4. **Custom Performance Metrics:**
```javascript
class PerformanceMetrics {
    constructor() {
        this.metrics = new Map();
        this.startTimes = new Map();
    }
    
    startTimer(name) {
        this.startTimes.set(name, performance.now());
    }
    
    endTimer(name) {
        const startTime = this.startTimes.get(name);
        if (!startTime) {
            console.warn(`Timer ${name} was not started`);
            return;
        }
        
        const duration = performance.now() - startTime;
        this.metrics.set(name, duration);
        this.startTimes.delete(name);
        
        console.log(`${name}: ${duration.toFixed(2)}ms`);
        return duration;
    }
    
    getMetrics() {
        return Object.fromEntries(this.metrics);
    }
    
    getAverageMetric(name, samples = 10) {
        const values = Array.from(this.metrics.entries())
            .filter(([key]) => key.startsWith(name))
            .map(([, value]) => value)
            .slice(-samples);
        
        return values.reduce((sum, val) => sum + val, 0) / values.length;
    }
    
    clearMetrics() {
        this.metrics.clear();
        this.startTimes.clear();
    }
}

// Usage
const metrics = new PerformanceMetrics();

// Measure multiple operations
for (let i = 0; i < 5; i++) {
    metrics.startTimer(`operation-${i}`);
    
    // Simulate work
    const start = performance.now();
    while (performance.now() - start < Math.random() * 100) {
        // Busy wait
    }
    
    metrics.endTimer(`operation-${i}`);
}

console.log('All metrics:', metrics.getMetrics());
console.log('Average operation time:', metrics.getAverageMetric('operation'));
```

**Memory Profiling:**

5. **Memory Usage Monitoring:**
```javascript
class MemoryProfiler {
    constructor() {
        this.snapshots = [];
        this.intervalId = null;
    }
    
    startMonitoring(interval = 1000) {
        this.intervalId = setInterval(() => {
            this.takeSnapshot();
        }, interval);
    }
    
    stopMonitoring() {
        if (this.intervalId) {
            clearInterval(this.intervalId);
            this.intervalId = null;
        }
    }
    
    takeSnapshot() {
        const snapshot = {
            timestamp: Date.now(),
            memory: process.memoryUsage(),
            heapUsed: process.memoryUsage().heapUsed,
            heapTotal: process.memoryUsage().heapTotal,
            external: process.memoryUsage().external
        };
        
        this.snapshots.push(snapshot);
        
        // Keep only last 100 snapshots
        if (this.snapshots.length > 100) {
            this.snapshots.shift();
        }
        
        return snapshot;
    }
    
    getMemoryTrend() {
        if (this.snapshots.length < 2) return null;
        
        const first = this.snapshots[0];
        const last = this.snapshots[this.snapshots.length - 1];
        
        return {
            heapUsedChange: last.heapUsed - first.heapUsed,
            heapTotalChange: last.heapTotal - first.heapTotal,
            timeSpan: last.timestamp - first.timestamp
        };
    }
    
    detectMemoryLeak() {
        const trend = this.getMemoryTrend();
        if (!trend) return false;
        
        // Consider it a leak if heap usage increases by more than 10MB over time
        return trend.heapUsedChange > 10 * 1024 * 1024;
    }
    
    getMemoryReport() {
        const current = this.snapshots[this.snapshots.length - 1];
        const trend = this.getMemoryTrend();
        
        return {
            current: current,
            trend: trend,
            isLeaking: this.detectMemoryLeak(),
            snapshots: this.snapshots.length
        };
    }
}

// Usage
const profiler = new MemoryProfiler();
profiler.startMonitoring(5000); // Check every 5 seconds

// Later, check for memory leaks
setTimeout(() => {
    const report = profiler.getMemoryReport();
    if (report.isLeaking) {
        console.warn('Potential memory leak detected!');
    }
    profiler.stopMonitoring();
}, 60000);
```

**Optimization Strategies:**

6. **Code Optimization Techniques:**
```javascript
class PerformanceOptimizer {
    static debounce(func, wait) {
        let timeout;
        return function executedFunction(...args) {
            const later = () => {
                clearTimeout(timeout);
                func.apply(this, args);
            };
            clearTimeout(timeout);
            timeout = setTimeout(later, wait);
        };
    }
    
    static throttle(func, limit) {
        let inThrottle;
        return function executedFunction(...args) {
            if (!inThrottle) {
                func.apply(this, args);
                inThrottle = true;
                setTimeout(() => inThrottle = false, limit);
            }
        };
    }
    
    static memoize(fn) {
        const cache = new Map();
        return function(...args) {
            const key = JSON.stringify(args);
            
            if (cache.has(key)) {
                return cache.get(key);
            }
            
            const result = fn.apply(this, args);
            cache.set(key, result);
            return result;
        };
    }
    
    static lazyLoad(loader) {
        let promise = null;
        return function() {
            if (!promise) {
                promise = loader();
            }
            return promise;
        };
    }
}

// Usage
const expensiveFunction = (n) => {
    console.log('Computing...');
    return n * n * n;
};

const memoizedFunction = PerformanceOptimizer.memoize(expensiveFunction);
console.log(memoizedFunction(5)); // Computing... 125
console.log(memoizedFunction(5)); // 125 (from cache)

const debouncedSearch = PerformanceOptimizer.debounce((query) => {
    console.log('Searching for:', query);
}, 300);

// debouncedSearch will only execute after 300ms of inactivity
debouncedSearch('a');
debouncedSearch('ab');
debouncedSearch('abc'); // Only this will execute
```

7. **Bundle Analysis:**
```javascript
// webpack-bundle-analyzer configuration
const BundleAnalyzerPlugin = require('webpack-bundle-analyzer').BundleAnalyzerPlugin;

module.exports = {
    plugins: [
        new BundleAnalyzerPlugin({
            analyzerMode: 'static',
            openAnalyzer: false,
            reportFilename: 'bundle-report.html'
        })
    ]
};

// Performance budget in webpack.config.js
module.exports = {
    performance: {
        hints: 'warning',
        maxEntrypointSize: 250000,
        maxAssetSize: 250000,
        assetFilter: function(assetFilename) {
            return assetFilename.endsWith('.js');
        }
    }
};
```

**Best Practices:**
- Use Chrome DevTools for profiling
- Monitor memory usage regularly
- Implement performance budgets
- Use performance monitoring tools
- Optimize critical rendering path
- Implement lazy loading
- Use code splitting
- Monitor bundle sizes
- Implement proper caching
- Use performance metrics
- Profile in production-like environments
- Use performance testing tools
- Implement proper error handling
- Use performance optimization techniques
- Monitor performance regressions
- Implement proper logging
- Use performance monitoring services
- Implement proper testing
- Use performance best practices
- Monitor performance metrics
- Implement proper optimization strategies

### 77. How do you implement advanced JavaScript build tools and bundling?
**Answer:**
Webpack, Rollup, Vite, tree shaking, code splitting, and advanced bundling strategies.

**Detailed Explanation:**
Modern bundlers transform and optimize your codebase for browsers and Node runtimes. They resolve modules, transpile, split code into chunks, eliminate dead code, and inline/extern assets for optimal delivery.

**Common Bundlers and When to Use Them:**

1. **Webpack (mature, feature-rich):**
```javascript
// webpack.config.js
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
    mode: 'production',
    entry: './src/index.tsx',
    output: {
        filename: '[name].[contenthash].js',
        path: path.resolve(__dirname, 'dist'),
        clean: true
    },
    module: {
        rules: [
            { test: /\.tsx?$/, use: 'ts-loader', exclude: /node_modules/ },
            { test: /\.css$/, use: ['style-loader', 'css-loader'] },
            { test: /\.(png|svg|jpg|gif)$/i, type: 'asset' }
        ]
    },
    resolve: { extensions: ['.tsx', '.ts', '.js'] },
    optimization: {
        splitChunks: { chunks: 'all' },
        runtimeChunk: 'single'
    },
    plugins: [
        new HtmlWebpackPlugin({ template: './public/index.html' })
    ]
};
```

2. **Rollup (libraries/esm-first):**
```javascript
// rollup.config.mjs
import terser from '@rollup/plugin-terser';
import typescript from '@rollup/plugin-typescript';

export default {
    input: 'src/index.ts',
    output: [
        { file: 'dist/index.esm.js', format: 'esm' },
        { file: 'dist/index.cjs.js', format: 'cjs' }
    ],
    plugins: [typescript(), terser()],
    external: ['react']
};
```

3. **Vite (dev speed, ESM dev server, Rollup prod):**
```javascript
// vite.config.ts
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
    plugins: [react()],
    build: {
        target: 'es2019',
        sourcemap: true,
        rollupOptions: {
            output: { manualChunks: { vendor: ['react', 'react-dom'] } }
        }
    }
});
```

**Tree Shaking and Dead Code Elimination:**
```javascript
// Prefer ESM for treeshaking
import { specificUtil } from 'lib'; // imports only what you need

// Avoid side effects in modules or declare sideEffects in package.json
// package.json
{
  "name": "mylib",
  "sideEffects": false
}
```

**Code Splitting Patterns:**
```javascript
// Dynamic import-based route splitting
const UsersPage = () => import('./pages/Users');

// React lazy
const Users = React.lazy(() => import('./pages/Users'));

// Webpack: named chunks for better caching
import(/* webpackChunkName: "users" */ './pages/Users');
```

**Asset Optimization:**
- **Images:** use responsive images, AVIF/WebP, and `asset/resource`.
- **CSS:** purge unused selectors, minify, and extract to separate files.
- **Fonts:** subset and preload critical fonts.

**Bundle Analysis and Budgets:**
```javascript
// webpack-bundle-analyzer
const { BundleAnalyzerPlugin } = require('webpack-bundle-analyzer');
plugins: [ new BundleAnalyzerPlugin({ analyzerMode: 'static' }) ]

// Performance budgets (webpack)
performance: { maxEntrypointSize: 250000, maxAssetSize: 250000 }
```

**Best Practices:**
- Use ESM for treeshaking, avoid commonjs in app code.
- Split vendor and app chunks; keep runtime separate.
- Cache-bust with contenthash; long-term cache static assets.
- Generate source maps for prod debugging, restrict access.
- Analyze bundles regularly and set budgets.
- Prefer Vite for SPA dev, Rollup for libraries, Webpack for complex apps.

### 78. What are JavaScript advanced debugging techniques?
**Answer:**
Source maps, breakpoints, conditional breakpoints, watch expressions, and advanced debugging tools.

**Detailed Explanation:**
Advanced debugging leverages modern DevTools, programmatic hooks, and logging patterns to quickly isolate issues in complex apps.

**DevTools Power Techniques:**

1. **Breakpoints:**
```javascript
// Manual breakpoint
debugger;

// Conditional breakpoint (DevTools UI):
// Right-click gutter → Add conditional breakpoint: i % 7 === 0
for (let i = 0; i < 1000; i++) {
    // work
}
```

2. **Watch Expressions and Scope Inspection:**
```javascript
// In Sources → Watch, add: state.user?.roles.includes('admin')
// Inspect Call Stack to identify async boundaries
```

3. **Source Maps:**
```javascript
// Ensure build generates source maps
// Vite: build.sourcemap = true
// Webpack: devtool: 'source-map'
```

**Network and Performance Debugging:**
- Use Network tab: check CORS, headers, caching, waterfall.
- Performance tab: record CPU, FPS, Long Tasks; find blocking scripts.
- Coverage tab: detect unused JS/CSS for pruning.

**Programmatic Debugging:**
```javascript
// Structured logging
const log = (label, data) => console.log(`[${label}]`, JSON.stringify(data));

// Timing
console.time('expensive');
doExpensiveWork();
console.timeEnd('expensive');

// Assert invariants
console.assert(Array.isArray(items), 'items must be an array');
```

**Node.js Debugging:**
```bash
node --inspect-brk server.js
# Open chrome://inspect → Targets
```

**Best Practices:**
- Reproduce reliably; minimize variables.
- Add invariant checks and feature flags.
- Prefer small repro repos and unit tests for regressions.
- Keep source maps gated in prod; avoid leaking.

### 79. How do you implement advanced JavaScript architecture patterns?
**Answer:**
Micro-frontends, monorepos, component libraries, and advanced architectural patterns.

**Detailed Explanation:**
Large-scale JS systems benefit from modular boundaries, typed contracts, versioning discipline, and shared tooling.

**Micro-frontends:**
```javascript
// Module Federation (webpack)
// host webpack.config.js
const ModuleFederationPlugin = require('webpack').container.ModuleFederationPlugin;
plugins: [
  new ModuleFederationPlugin({
    name: 'host',
    remotes: { users: 'users@https://cdn/app-users/remoteEntry.js' }
  })
];

// In code
const UsersApp = React.lazy(() => import('users/App'));
```

**Monorepos:**
```bash
# pnpm workspaces or yarn workspaces
pnpm init -y
echo 'packages/*' > pnpm-workspace.yaml
```
```json
// package.json (root)
{
  "private": true,
  "workspaces": ["packages/*"]
}
```

**Design Systems / Component Libraries:**
```bash
# Storybook for component documentation
npx sb init --builder vite
```

**Event-driven architecture (frontend):**
```javascript
// Typed event bus
class EventBus {
    listeners = new Map();
    on(type, cb) { (this.listeners.get(type) ?? this.listeners.set(type, []).get(type)).push(cb); }
    emit(type, payload) { for (const cb of this.listeners.get(type) ?? []) cb(payload); }
}
```

**Best Practices:**
- Strong boundaries via types and lint rules.
- Independent deployability for micro-frontends.
- Single source of truth for UI tokens.
- Automated versioning (changesets), CI, and release pipelines.

### 80. What are JavaScript advanced optimization techniques?
**Answer:**
Dead code elimination, tree shaking, minification, compression, and advanced optimization strategies.

**Detailed Explanation:**
Optimization spans network, CPU, memory, and rendering.

**Network-level:**
- HTTP/2 multiplexing, HTTP/3/QUIC, preconnect, preload, DNS-prefetch.
- Compress with Brotli, cache aggressively with immutable contenthash assets.

**Code-level:**
```javascript
// Remove optional chaining hot-paths where safe
// Replace polymorphic functions with predictable shapes
// Hoist invariants out of loops
```

**Rendering:**
- Avoid layout thrashing (read before write), batch DOM updates.
- Use requestAnimationFrame, IntersectionObserver for lazy work.

**Images:**
- Use `srcset`/`sizes`, AVIF/WebP, responsive loaders.

**Build-time:**
- Minify (Terser/Esbuild), treeshake ESM, code split, inline critical CSS.

**Runtime profiling:**
```javascript
performance.mark('task-start');
doTask();
performance.mark('task-end');
performance.measure('task', 'task-start', 'task-end');
```

**Best Practices:**
- Measure first; set SLOs for LCP/INP/CLS.
- Optimize critical path; defer non-critical.
- Keep main thread idle; offload with Workers.

### 81. How do you implement advanced JavaScript error handling?
**Answer:**
Global error handlers, error boundaries, custom error types, and advanced error recovery strategies.

**Detailed Explanation:**
Robust error handling spans sync/async paths, global hooks, user messaging, and observability.

**Custom Error Types and Classification:**
```javascript
class AppError extends Error { constructor(message, meta) { super(message); this.meta = meta; this.name = 'AppError'; } }
class NetworkError extends AppError { constructor(status, url) { super(`HTTP ${status} ${url}`, { status, url }); this.name = 'NetworkError'; } }
class ValidationError extends AppError { constructor(field, msg) { super(`Invalid ${field}: ${msg}`, { field }); this.name = 'ValidationError'; } }
```

**Global Handlers:**
```javascript
window.addEventListener('error', e => report(e.error));
window.addEventListener('unhandledrejection', e => report(e.reason));
```

**Retry and Circuit Breakers:**
```javascript
async function withRetry(fn, attempts = 3) { let last; for (let i=0;i<attempts;i++){ try { return await fn(); } catch(e){ last=e; await new Promise(r=>setTimeout(r, 2**i*250)); } } throw last; }
```

**UI Error Boundaries (React-like):**
```javascript
class ErrorBoundary extends React.Component { state = { hasError: false };
  static getDerivedStateFromError(){ return { hasError: true }; }
  componentDidCatch(error, info){ report(error, info); }
  render(){ return this.state.hasError ? <Fallback/> : this.props.children; } }
```

**Best Practices:**
- Fail fast; classify errors; add context.
- Never swallow errors silently; surface actionable messages.
- Record correlation IDs; link logs, traces, and user sessions.

### 82. What are JavaScript advanced testing strategies?
**Answer:**
Unit testing, integration testing, end-to-end testing, visual regression testing, and advanced testing patterns.

**Detailed Explanation:**
Build a layered strategy: fast unit tests, realistic integration, and selective E2E, with contract tests between services.

**Contract Testing (consumer-driven):**
```javascript
// Example idea: pact tests
// Ensure frontend expectations match backend responses
```

**Visual Regression:**
```javascript
// Playwright + percy/screener to capture diffs across viewports/themes
```

**Test Data Factories and Fixtures:**
```javascript
const userFactory = (overrides={}) => ({ id: 1, name: 'User', email: 'u@example.com', ...overrides });
```

**Best Practices:**
- Keep tests deterministic and isolated; no shared state.
- Use MSW/fakes for network; avoid flakiness.
- Track coverage; enforce thresholds on changed files.

### 83. How do you implement advanced JavaScript data structures?
**Answer:**
Custom data structures, algorithms, and advanced data manipulation techniques.

**Detailed Explanation:**
Implement specialized structures for performance-critical paths.

**LRU Cache:**
```javascript
class LRUCache {
  constructor(capacity){ this.capacity = capacity; this.map = new Map(); }
  get(key){ if(!this.map.has(key)) return undefined; const val = this.map.get(key); this.map.delete(key); this.map.set(key, val); return val; }
  set(key,val){ if(this.map.has(key)) this.map.delete(key); this.map.set(key,val); if(this.map.size>this.capacity){ const oldest = this.map.keys().next().value; this.map.delete(oldest); } }
}
```

**Trie (prefix tree):**
```javascript
class TrieNode { constructor(){ this.children = {}; this.end = false; } }
class Trie { constructor(){ this.root = new TrieNode(); }
  insert(word){ let node=this.root; for(const ch of word){ node = node.children[ch] ??= new TrieNode(); } node.end=true; }
  startsWith(prefix){ let node=this.root; for(const ch of prefix){ if(!(ch in node.children)) return false; node=node.children[ch]; } return true; }
}
```

**Priority Queue (binary heap):**
```javascript
class MinHeap{ constructor(){ this.h=[]; }
  push(v){ this.h.push(v); this.bubbleUp(); }
  pop(){ if(this.h.length===0) return undefined; const r=this.h[0]; const v=this.h.pop(); if(this.h.length){ this.h[0]=v; this.bubbleDown(); } return r; }
  bubbleUp(){ let i=this.h.length-1; while(i>0){ const p=(i-1)>>1; if(this.h[p]<=this.h[i]) break; [this.h[p],this.h[i]]=[this.h[i],this.h[p]]; i=p; } }
  bubbleDown(){ let i=0; while(true){ const l=i*2+1,r=i*2+2; let s=i; if(l<this.h.length&&this.h[l]<this.h[s]) s=l; if(r<this.h.length&&this.h[r]<this.h[s]) s=r; if(s===i) break; [this.h[i],this.h[s]]=[this.h[s],this.h[i]]; i=s; } }
}
```

**Best Practices:**
- Choose structures based on complexity targets.
- Prefer typed arrays for numeric data.
- Benchmark alternatives with realistic inputs.

### 84. What are JavaScript advanced async patterns?
**Answer:**
Advanced Promise patterns, async iterators, reactive programming, and complex async workflows.

**Detailed Explanation:**
Coordinate multiple async sources with backpressure, cancellation, and retries.

**Concurrency Control:**
```javascript
async function pLimit(concurrency){
  const q=[]; let a=0;
  const run=async (fn,resolve,reject)=>{ a++; try{ resolve(await fn()); } catch(e){ reject(e); } finally{ a--; next(); } };
  const next=()=>{ if(a>=concurrency) return; const item=q.shift(); if(!item) return; run(...item); };
  return (fn)=> new Promise((res,rej)=>{ q.push([fn,res,rej]); next(); });
}
```

**Cancellation (AbortController):**
```javascript
const controller = new AbortController();
fetch('/api', { signal: controller.signal });
controller.abort();
```

**Async Iterators:**
```javascript
async function* stream(url){ const r=await fetch(url); for await (const chunk of r.body){ yield chunk; } }
```

**Reactive Streams:**
```javascript
// RxJS example idea: fromEvent(input,'input').pipe(debounceTime(300), switchMap(q=>search(q)))
```

**Best Practices:**
- Use timeouts and cancellation.
- Fail fast and retry with jitter.
- Bound concurrency; avoid thundering herds.

### 85. How do you implement advanced JavaScript monitoring and observability?
**Answer:**
Application performance monitoring, error tracking, logging strategies, and advanced observability patterns.

**Detailed Explanation:**
Observability correlates logs, metrics, and traces to understand system behavior in production.

**RUM (Real User Monitoring):**
```javascript
// Web Vitals
import { onLCP, onINP, onCLS } from 'web-vitals';
onLCP(v => sendMetric('LCP', v.value));
onINP(v => sendMetric('INP', v.value));
onCLS(v => sendMetric('CLS', v.value));
```

**Error Tracking:**
```javascript
window.addEventListener('error', e => sendError(e.error));
window.addEventListener('unhandledrejection', e => sendError(e.reason));
```

**Distributed Tracing (frontend to backend):**
```javascript
// Inject trace headers
const traceId = crypto.randomUUID();
fetch('/api/data', { headers: { 'x-trace-id': traceId } });
```

**Structured Logging:**
```javascript
function log(level, message, meta={}){
  console[level]({ ts: new Date().toISOString(), message, ...meta });
}
```

**Dashboards and Alerts:**
- Export metrics to Prometheus/Grafana, Datadog, or OpenTelemetry.
- Set SLOs and alert on error budget burn.

**Best Practices:**
- Use correlation IDs to connect client logs with backend traces.
- Sample selectively to control cost.
- Sanitize PII before sending telemetry.

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