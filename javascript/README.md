# JavaScript Interview Questions

## 🎯 Difficulty Levels
- **🟢 Beginner**: Basic JavaScript concepts and syntax
- **🟡 Intermediate**: Functions, objects, and DOM manipulation
- **🔴 Advanced**: Async programming, closures, and modern ES6+ features
- **🟣 Expert**: Performance optimization, design patterns, and advanced concepts

## 📋 Questions

### 🟢 Beginner Level

#### 1. What is JavaScript and what are its key features?
**Answer:**
JavaScript is a high-level, interpreted programming language that is primarily used for web development. Key features include:

- **Dynamic typing**: Variables can hold values of any type
- **Prototype-based inheritance**: Objects can inherit properties from other objects
- **First-class functions**: Functions are treated as first-class citizens
- **Event-driven**: Responds to user interactions and events
- **Asynchronous**: Supports non-blocking operations

```javascript
// Dynamic typing
let variable = 42;        // Number
variable = "Hello";      // String
variable = true;         // Boolean

// First-class functions
function greet(name) {
    return `Hello, ${name}!`;
}

const sayHello = greet;  // Function assigned to variable
console.log(sayHello("World")); // "Hello, World!"
```

**Key Concepts:**
- Language characteristics
- Dynamic typing
- First-class functions
- Event-driven programming

#### 2. What are the different data types in JavaScript?
**Answer:**
JavaScript has primitive and reference data types:

```javascript
// Primitive types
let number = 42;                    // Number
let string = "Hello World";         // String
let boolean = true;                 // Boolean
let undefined = undefined;          // Undefined
let nullValue = null;              // Null
let symbol = Symbol('id');          // Symbol (ES6+)
let bigInt = 123n;                  // BigInt (ES2020+)

// Reference types
let object = { name: "John", age: 30 };
let array = [1, 2, 3, 4, 5];
let function = function() { return "Hello"; };

// Type checking
console.log(typeof number);        // "number"
console.log(typeof string);       // "string"
console.log(typeof boolean);       // "boolean"
console.log(typeof undefined);     // "undefined"
console.log(typeof nullValue);     // "object" (quirk!)
console.log(typeof object);        // "object"
console.log(typeof array);         // "object"
console.log(typeof function);      // "function"
```

**Key Concepts:**
- Primitive vs reference types
- Type coercion
- typeof operator
- Null vs undefined

#### 3. What is the difference between var, let, and const?
**Answer:**
These are different ways to declare variables in JavaScript:

```javascript
// var - Function scoped, hoisted, can be redeclared
function example() {
    console.log(x); // undefined (hoisted but not initialized)
    var x = 5;
    var x = 10; // Can be redeclared
    console.log(x); // 10
}

// let - Block scoped, hoisted but not initialized, cannot be redeclared
function example2() {
    console.log(y); // ReferenceError: Cannot access 'y' before initialization
    let y = 5;
    let y = 10; // SyntaxError: Identifier 'y' has already been declared
}

// const - Block scoped, must be initialized, cannot be reassigned
const z = 5;
z = 10; // TypeError: Assignment to constant variable

// Block scope example
{
    var a = 1;
    let b = 2;
    const c = 3;
}
console.log(a); // 1 (accessible)
console.log(b); // ReferenceError: b is not defined
console.log(c); // ReferenceError: c is not defined
```

**Key Concepts:**
- Variable hoisting
- Scope (function vs block)
- Temporal dead zone
- Immutability

#### 4. What are functions and how do you create them?
**Answer:**
Functions are reusable blocks of code that perform specific tasks:

```javascript
// Function declaration
function greet(name) {
    return `Hello, ${name}!`;
}

// Function expression
const greet2 = function(name) {
    return `Hello, ${name}!`;
};

// Arrow function (ES6+)
const greet3 = (name) => {
    return `Hello, ${name}!`;
};

// Arrow function (shorthand)
const greet4 = name => `Hello, ${name}!`;

// Function with default parameters
function greetWithDefault(name = "World") {
    return `Hello, ${name}!`;
}

// Function with rest parameters
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3, 4)); // 10

// Immediately Invoked Function Expression (IIFE)
(function() {
    console.log("IIFE executed immediately");
})();
```

**Key Concepts:**
- Function types
- Arrow functions
- Default parameters
- Rest parameters
- IIFE

#### 5. What are objects and how do you work with them?
**Answer:**
Objects are collections of key-value pairs:

```javascript
// Object literal
const person = {
    name: "John",
    age: 30,
    city: "New York",
    greet: function() {
        return `Hello, I'm ${this.name}`;
    }
};

// Accessing properties
console.log(person.name);        // "John"
console.log(person["age"]);      // 30
console.log(person.greet());     // "Hello, I'm John"

// Adding properties
person.email = "john@example.com";
person["phone"] = "123-456-7890";

// Object methods
const person2 = {
    firstName: "Jane",
    lastName: "Doe",
    get fullName() {
        return `${this.firstName} ${this.lastName}`;
    },
    set fullName(value) {
        [this.firstName, this.lastName] = value.split(" ");
    }
};

// Object destructuring
const { name, age } = person;
console.log(name, age); // "John" 30

// Object spread operator
const updatedPerson = { ...person, age: 31 };

// Object methods
console.log(Object.keys(person));     // ["name", "age", "city", "greet"]
console.log(Object.values(person));  // ["John", 30, "New York", function]
console.log(Object.entries(person));  // [["name", "John"], ["age", 30], ...]
```

**Key Concepts:**
- Object properties
- Methods
- Getters and setters
- Destructuring
- Spread operator
- Object methods

### 🟡 Intermediate Level

#### 6. What are closures and how do they work?
**Answer:**
A closure is a function that has access to variables in its outer (enclosing) scope even after the outer function has returned:

```javascript
// Basic closure example
function outerFunction(x) {
    // Outer function's variable
    let outerVariable = x;
    
    // Inner function (closure)
    function innerFunction(y) {
        console.log(outerVariable + y);
    }
    
    return innerFunction;
}

const closure = outerFunction(10);
closure(5); // 15 - still has access to outerVariable

// Practical closure example - Counter
function createCounter() {
    let count = 0;
    
    return {
        increment: function() {
            count++;
            return count;
        },
        decrement: function() {
            count--;
            return count;
        },
        getCount: function() {
            return count;
        }
    };
}

const counter = createCounter();
console.log(counter.increment()); // 1
console.log(counter.increment()); // 2
console.log(counter.getCount());  // 2

// Closure with private variables
function createBankAccount(initialBalance) {
    let balance = initialBalance;
    
    return {
        deposit: function(amount) {
            balance += amount;
            return balance;
        },
        withdraw: function(amount) {
            if (amount <= balance) {
                balance -= amount;
                return balance;
            }
            throw new Error("Insufficient funds");
        },
        getBalance: function() {
            return balance;
        }
    };
}

const account = createBankAccount(1000);
console.log(account.deposit(500)); // 1500
console.log(account.getBalance()); // 1500
```

**Key Concepts:**
- Lexical scoping
- Function scope
- Private variables
- Memory management

#### 7. What is the difference between == and ===?
**Answer:**
These are comparison operators with different behaviors:

```javascript
// == (loose equality) - performs type coercion
console.log(5 == "5");        // true (string "5" converted to number 5)
console.log(true == 1);       // true (boolean true converted to 1)
console.log(null == undefined); // true (special case)
console.log(0 == false);      // true (boolean false converted to 0)
console.log("" == false);     // true (both converted to 0)

// === (strict equality) - no type coercion
console.log(5 === "5");       // false (different types)
console.log(true === 1);      // false (different types)
console.log(null === undefined); // false (different types)
console.log(0 === false);     // false (different types)
console.log("" === false);    // false (different types)

// Best practices
const value = "5";
if (value === 5) {
    console.log("Strict comparison");
} else if (value == 5) {
    console.log("Loose comparison");
}

// Object comparison
const obj1 = { a: 1 };
const obj2 = { a: 1 };
const obj3 = obj1;

console.log(obj1 == obj2);   // false (different objects)
console.log(obj1 === obj2);  // false (different objects)
console.log(obj1 === obj3);  // true (same reference)
```

**Key Concepts:**
- Type coercion
- Strict vs loose equality
- Object comparison
- Best practices

#### 8. How do you work with arrays in JavaScript?
**Answer:**
Arrays are ordered collections of values with many built-in methods:

```javascript
// Array creation
const fruits = ["apple", "banana", "orange"];
const numbers = new Array(1, 2, 3, 4, 5);
const empty = [];

// Array methods
const numbers = [1, 2, 3, 4, 5];

// forEach - iterate over elements
numbers.forEach((num, index) => {
    console.log(`${index}: ${num}`);
});

// map - transform elements
const doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

// filter - select elements
const evens = numbers.filter(num => num % 2 === 0);
console.log(evens); // [2, 4]

// reduce - accumulate values
const sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum); // 15

// find - find first matching element
const found = numbers.find(num => num > 3);
console.log(found); // 4

// some - check if any element matches
const hasEven = numbers.some(num => num % 2 === 0);
console.log(hasEven); // true

// every - check if all elements match
const allPositive = numbers.every(num => num > 0);
console.log(allPositive); // true

// Array manipulation
const arr = [1, 2, 3];
arr.push(4);        // [1, 2, 3, 4]
arr.pop();          // [1, 2, 3]
arr.unshift(0);     // [0, 1, 2, 3]
arr.shift();        // [1, 2, 3]
arr.splice(1, 1);   // [1, 3] - remove 1 element at index 1
arr.splice(1, 0, 2); // [1, 2, 3] - insert 2 at index 1
```

**Key Concepts:**
- Array methods
- Functional programming
- Immutability
- Performance considerations

#### 9. What are Promises and how do you handle asynchronous operations?
**Answer:**
Promises are objects representing the eventual completion or failure of an asynchronous operation:

```javascript
// Basic Promise
const promise = new Promise((resolve, reject) => {
    const success = Math.random() > 0.5;
    
    setTimeout(() => {
        if (success) {
            resolve("Operation successful!");
        } else {
            reject(new Error("Operation failed!"));
        }
    }, 1000);
});

// Promise handling
promise
    .then(result => {
        console.log(result);
    })
    .catch(error => {
        console.error(error.message);
    })
    .finally(() => {
        console.log("Operation completed");
    });

// Async/await syntax
async function handleAsyncOperation() {
    try {
        const result = await promise;
        console.log(result);
    } catch (error) {
        console.error(error.message);
    } finally {
        console.log("Operation completed");
    }
}

// Promise.all - wait for all promises
const promises = [
    fetch('/api/users'),
    fetch('/api/posts'),
    fetch('/api/comments')
];

Promise.all(promises)
    .then(responses => {
        return Promise.all(responses.map(response => response.json()));
    })
    .then(data => {
        console.log('All data loaded:', data);
    })
    .catch(error => {
        console.error('One or more requests failed:', error);
    });

// Promise.allSettled - wait for all promises to settle
Promise.allSettled(promises)
    .then(results => {
        results.forEach((result, index) => {
            if (result.status === 'fulfilled') {
                console.log(`Promise ${index} succeeded:`, result.value);
            } else {
                console.log(`Promise ${index} failed:`, result.reason);
            }
        });
    });
```

**Key Concepts:**
- Asynchronous programming
- Promise states
- Error handling
- Promise chaining
- Async/await

#### 10. What are JavaScript modules and how do you use them?
**Answer:**
Modules allow you to split code into separate files and import/export functionality:

```javascript
// math.js - Exporting functions
export function add(a, b) {
    return a + b;
}

export function subtract(a, b) {
    return a - b;
}

export const PI = 3.14159;

// Default export
export default function multiply(a, b) {
    return a * b;
}

// utils.js - Multiple exports
export const formatDate = (date) => {
    return date.toLocaleDateString();
};

export const formatCurrency = (amount) => {
    return `$${amount.toFixed(2)}`;
};

// Importing in another file
import multiply, { add, subtract, PI } from './math.js';
import { formatDate, formatCurrency } from './utils.js';

// Using imported functions
console.log(add(5, 3)); // 8
console.log(multiply(4, 6)); // 24
console.log(formatCurrency(123.45)); // $123.45

// Namespace import
import * as math from './math.js';
console.log(math.add(1, 2)); // 3
console.log(math.PI); // 3.14159

// Dynamic imports
async function loadModule() {
    const { default: multiply } = await import('./math.js');
    console.log(multiply(3, 4)); // 12
}
```

**Key Concepts:**
- Module system
- Import/export syntax
- Default vs named exports
- Dynamic imports
- Module bundlers

### 🔴 Advanced Level

#### 11. What are JavaScript design patterns and how do you implement them?
**Answer:**
Design patterns are reusable solutions to common programming problems:

```javascript
// 1. Singleton Pattern
class DatabaseConnection {
    constructor() {
        if (DatabaseConnection.instance) {
            return DatabaseConnection.instance;
        }
        
        this.connection = this.createConnection();
        DatabaseConnection.instance = this;
    }
    
    createConnection() {
        return { connected: true, id: Math.random() };
    }
}

const db1 = new DatabaseConnection();
const db2 = new DatabaseConnection();
console.log(db1 === db2); // true - same instance

// 2. Factory Pattern
class Car {
    constructor(type, model) {
        this.type = type;
        this.model = model;
    }
}

class CarFactory {
    static createCar(type) {
        switch (type) {
            case 'sedan':
                return new Car('sedan', 'Toyota Camry');
            case 'suv':
                return new Car('suv', 'Honda CR-V');
            case 'sports':
                return new Car('sports', 'Porsche 911');
            default:
                throw new Error('Unknown car type');
        }
    }
}

const sedan = CarFactory.createCar('sedan');
console.log(sedan); // Car { type: 'sedan', model: 'Toyota Camry' }

// 3. Observer Pattern
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
    
    emit(event, data) {
        if (this.events[event]) {
            this.events[event].forEach(callback => callback(data));
        }
    }
    
    off(event, callback) {
        if (this.events[event]) {
            this.events[event] = this.events[event].filter(cb => cb !== callback);
        }
    }
}

const emitter = new EventEmitter();
emitter.on('userLogin', (user) => {
    console.log(`User ${user.name} logged in`);
});

emitter.emit('userLogin', { name: 'John', id: 1 });

// 4. Module Pattern
const UserModule = (() => {
    let users = [];
    
    return {
        addUser: (user) => {
            users.push(user);
        },
        getUsers: () => [...users],
        getUserById: (id) => {
            return users.find(user => user.id === id);
        },
        removeUser: (id) => {
            users = users.filter(user => user.id !== id);
        }
    };
})();

UserModule.addUser({ id: 1, name: 'John' });
console.log(UserModule.getUsers()); // [{ id: 1, name: 'John' }]
```

**Key Concepts:**
- Design patterns
- Code reusability
- Separation of concerns
- Maintainability
- Scalability

#### 12. How do you optimize JavaScript performance?
**Answer:**
Advanced performance optimization techniques:

```javascript
// 1. Debouncing and Throttling
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

function throttle(func, limit) {
    let inThrottle;
    return function() {
        const args = arguments;
        const context = this;
        if (!inThrottle) {
            func.apply(context, args);
            inThrottle = true;
            setTimeout(() => inThrottle = false, limit);
        }
    };
}

// Usage
const debouncedSearch = debounce((query) => {
    console.log('Searching for:', query);
}, 300);

const throttledScroll = throttle(() => {
    console.log('Scroll event');
}, 100);

// 2. Memoization
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

// Fibonacci with memoization
const fibonacci = memoize((n) => {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
});

console.log(fibonacci(40)); // Much faster with memoization

// 3. Lazy Loading
class LazyLoader {
    constructor() {
        this.observers = new Map();
        this.setupIntersectionObserver();
    }
    
    setupIntersectionObserver() {
        this.observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    this.loadContent(entry.target);
                }
            });
        });
    }
    
    observe(element, loadFunction) {
        this.observers.set(element, loadFunction);
        this.observer.observe(element);
    }
    
    loadContent(element) {
        const loadFunction = this.observers.get(element);
        if (loadFunction) {
            loadFunction();
            this.observer.unobserve(element);
            this.observers.delete(element);
        }
    }
}

// 4. Virtual Scrolling
class VirtualScroll {
    constructor(container, itemHeight, items) {
        this.container = container;
        this.itemHeight = itemHeight;
        this.items = items;
        this.visibleItems = Math.ceil(container.clientHeight / itemHeight);
        this.scrollTop = 0;
        
        this.setupScrollListener();
        this.render();
    }
    
    setupScrollListener() {
        this.container.addEventListener('scroll', () => {
            this.scrollTop = this.container.scrollTop;
            this.render();
        });
    }
    
    render() {
        const startIndex = Math.floor(this.scrollTop / this.itemHeight);
        const endIndex = Math.min(startIndex + this.visibleItems, this.items.length);
        
        const visibleItems = this.items.slice(startIndex, endIndex);
        const offsetY = startIndex * this.itemHeight;
        
        this.container.innerHTML = `
            <div style="height: ${this.items.length * this.itemHeight}px; position: relative;">
                <div style="transform: translateY(${offsetY}px);">
                    ${visibleItems.map((item, index) => 
                        `<div style="height: ${this.itemHeight}px;">${item}</div>`
                    ).join('')}
                </div>
            </div>
        `;
    }
}
```

**Key Concepts:**
- Performance optimization
- Memory management
- Asynchronous processing
- Caching strategies
- Monitoring and profiling

#### 13. What are JavaScript Proxies and how do you use them?
**Answer:**
Proxies allow you to intercept and customize operations on objects:

```javascript
// Basic Proxy
const user = {
    name: 'John',
    age: 30,
    email: 'john@example.com'
};

const userProxy = new Proxy(user, {
    get(target, property) {
        console.log(`Getting ${property}`);
        return target[property];
    },
    
    set(target, property, value) {
        console.log(`Setting ${property} to ${value}`);
        
        // Validation
        if (property === 'age' && (value < 0 || value > 150)) {
            throw new Error('Invalid age');
        }
        
        if (property === 'email' && !value.includes('@')) {
            throw new Error('Invalid email format');
        }
        
        target[property] = value;
        return true;
    },
    
    has(target, property) {
        console.log(`Checking if ${property} exists`);
        return property in target;
    },
    
    deleteProperty(target, property) {
        console.log(`Deleting ${property}`);
        delete target[property];
        return true;
    }
});

// Usage
console.log(userProxy.name); // Getting name, John
userProxy.age = 25; // Setting age to 25
console.log('age' in userProxy); // Checking if age exists, true

// Advanced Proxy with validation
class Validator {
    constructor() {
        this.rules = new Map();
    }
    
    addRule(property, rule) {
        if (!this.rules.has(property)) {
            this.rules.set(property, []);
        }
        this.rules.get(property).push(rule);
    }
    
    validate(property, value) {
        const rules = this.rules.get(property) || [];
        for (const rule of rules) {
            if (!rule(value)) {
                throw new Error(`Validation failed for ${property}`);
            }
        }
    }
}

const validator = new Validator();
validator.addRule('age', (age) => age >= 0 && age <= 150);
validator.addRule('email', (email) => email.includes('@'));

const createValidatedObject = (initialData) => {
    return new Proxy(initialData, {
        set(target, property, value) {
            validator.validate(property, value);
            target[property] = value;
            return true;
        }
    });
};

const person = createValidatedObject({});
person.age = 25; // OK
person.email = 'test@example.com'; // OK
// person.age = -5; // Throws error
```

**Key Concepts:**
- Proxy API
- Object interception
- Validation
- Reactive programming
- Advanced JavaScript features

### 🟣 Expert Level

#### 14. How do you implement advanced JavaScript concepts like Generators?
**Answer:**
Generators are functions that can be paused and resumed:

```javascript
// Basic Generator
function* numberGenerator() {
    console.log('Generator started');
    yield 1;
    console.log('First yield');
    yield 2;
    console.log('Second yield');
    yield 3;
    console.log('Generator ended');
}

const gen = numberGenerator();
console.log(gen.next()); // { value: 1, done: false }
console.log(gen.next()); // { value: 2, done: false }
console.log(gen.next()); // { value: 3, done: false }
console.log(gen.next()); // { value: undefined, done: true }

// Async Generators
async function* asyncGenerator() {
    for (let i = 0; i < 3; i++) {
        await new Promise(resolve => setTimeout(resolve, 1000));
        yield i;
    }
}

async function consumeAsyncGenerator() {
    for await (const value of asyncGenerator()) {
        console.log(value);
    }
}

// Generator with data processing
function* dataProcessor(data) {
    for (const item of data) {
        if (item > 0) {
            yield item * 2;
        }
    }
}

const numbers = [1, -2, 3, -4, 5];
const processor = dataProcessor(numbers);
console.log([...processor]); // [2, 6, 10]

// Fibonacci Generator
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

// Generator for infinite sequences
function* infiniteSequence() {
    let i = 0;
    while (true) {
        yield i++;
    }
}

const infinite = infiniteSequence();
console.log(infinite.next().value); // 0
console.log(infinite.next().value); // 1
console.log(infinite.next().value); // 2
```

**Key Concepts:**
- Generator functions
- Yield keyword
- Iterator protocol
- Async generators
- Infinite sequences

#### 15. How do you implement advanced JavaScript testing and debugging?
**Answer:**
Comprehensive testing and debugging strategies:

```javascript
// 1. Advanced Testing Framework
class TestFramework {
    constructor() {
        this.tests = [];
        this.beforeEach = null;
        this.afterEach = null;
    }
    
    test(name, fn) {
        this.tests.push({ name, fn });
    }
    
    beforeEach(fn) {
        this.beforeEach = fn;
    }
    
    afterEach(fn) {
        this.afterEach = fn;
    }
    
    async run() {
        let passed = 0;
        let failed = 0;
        
        for (const test of this.tests) {
            try {
                if (this.beforeEach) this.beforeEach();
                await test.fn();
                console.log(`✅ ${test.name}`);
                passed++;
            } catch (error) {
                console.log(`❌ ${test.name}: ${error.message}`);
                failed++;
            } finally {
                if (this.afterEach) this.afterEach();
            }
        }
        
        console.log(`\nResults: ${passed} passed, ${failed} failed`);
    }
}

// 2. Mocking and Stubbing
class Mock {
    constructor() {
        this.calls = [];
        this.returnValue = undefined;
    }
    
    returns(value) {
        this.returnValue = value;
        return this;
    }
    
    callsWith(...args) {
        this.calls.push(args);
        return this.returnValue;
    }
    
    wasCalledWith(...args) {
        return this.calls.some(call => 
            call.length === args.length && 
            call.every((arg, index) => arg === args[index])
        );
    }
    
    callCount() {
        return this.calls.length;
    }
}

// 3. Assertion Library
class Assert {
    static equal(actual, expected, message) {
        if (actual !== expected) {
            throw new Error(message || `Expected ${expected}, but got ${actual}`);
        }
    }
    
    static notEqual(actual, expected, message) {
        if (actual === expected) {
            throw new Error(message || `Expected not to be ${expected}`);
        }
    }
    
    static true(actual, message) {
        if (actual !== true) {
            throw new Error(message || `Expected true, but got ${actual}`);
        }
    }
    
    static false(actual, message) {
        if (actual !== false) {
            throw new Error(message || `Expected false, but got ${actual}`);
        }
    }
    
    static throws(fn, expectedError, message) {
        try {
            fn();
            throw new Error(message || 'Expected function to throw');
        } catch (error) {
            if (expectedError && !(error instanceof expectedError)) {
                throw new Error(message || `Expected ${expectedError.name}, but got ${error.constructor.name}`);
            }
        }
    }
}

// 4. Performance Testing
class PerformanceTest {
    static async measure(name, fn, iterations = 1000) {
        const times = [];
        
        for (let i = 0; i < iterations; i++) {
            const start = performance.now();
            await fn();
            const end = performance.now();
            times.push(end - start);
        }
        
        const avg = times.reduce((a, b) => a + b, 0) / times.length;
        const min = Math.min(...times);
        const max = Math.max(...times);
        
        console.log(`${name}: avg=${avg.toFixed(2)}ms, min=${min.toFixed(2)}ms, max=${max.toFixed(2)}ms`);
        
        return { avg, min, max, times };
    }
}

// 5. Memory Leak Detection
class MemoryMonitor {
    constructor() {
        this.snapshots = [];
    }
    
    takeSnapshot() {
        if (performance.memory) {
            this.snapshots.push({
                timestamp: Date.now(),
                used: performance.memory.usedJSHeapSize,
                total: performance.memory.totalJSHeapSize,
                limit: performance.memory.jsHeapSizeLimit
            });
        }
    }
    
    detectLeaks() {
        if (this.snapshots.length < 2) return;
        
        const latest = this.snapshots[this.snapshots.length - 1];
        const previous = this.snapshots[this.snapshots.length - 2];
        
        const growth = latest.used - previous.used;
        const growthPercent = (growth / previous.used) * 100;
        
        if (growthPercent > 10) {
            console.warn(`Potential memory leak detected: ${growthPercent.toFixed(2)}% growth`);
        }
    }
}

// Usage example
const testFramework = new TestFramework();

testFramework.test('should add numbers', () => {
    Assert.equal(add(2, 3), 5);
});

testFramework.test('should handle async operations', async () => {
    const result = await fetchData();
    Assert.true(result.success);
});

testFramework.run();
```

**Key Concepts:**
- Testing frameworks
- Mocking and stubbing
- Assertion libraries
- Performance testing
- Memory monitoring
- Debugging techniques

## 🎯 Practice Exercises

### Beginner
1. Create a simple calculator with basic operations
2. Build a todo list application
3. Implement form validation

### Intermediate
1. Create a weather app with API integration
2. Build a photo gallery with lazy loading
3. Implement a search functionality with debouncing

### Advanced
1. Build a real-time chat application
2. Create a data visualization dashboard
3. Implement a state management system

### Expert
1. Design a micro-frontend architecture
2. Build a high-performance web application
3. Create a comprehensive testing suite

## 📚 Additional Resources

- [MDN JavaScript Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [JavaScript.info](https://javascript.info/)
- [You Don't Know JS](https://github.com/getify/You-Dont-Know-JS)
- [JavaScript Design Patterns](https://www.dofactory.com/javascript/design-patterns)
