# 📘 Frontend Engineering (FEE) — Complete Summary Notes

> **Course**: Frontend Engineering-I |
>
> Compiled from Lectures 1–45 (All PPTs)

---

## Table of Contents

1. [Introduction to JavaScript](#1-introduction-to-javascript)
2. [Adding JS to HTML & Chrome DevTools](#2-adding-js-to-html--chrome-devtools)
3. [JavaScript Syntax, Variables & Data Types](#3-javascript-syntax-variables--data-types)
4. [Operators](#4-operators)
5. [Null vs Undefined](#5-null-vs-undefined)
6. [Type Coercion](#6-type-coercion)
7. [Control Flow — Conditionals & Loops](#7-control-flow--conditionals--loops)
8. [Functions & Scoping](#8-functions--scoping)
9. [Hoisting](#9-hoisting)
10. [Closures](#10-closures)
11. [Higher-Order Functions](#11-higher-order-functions)
12. [Arrays & Array Methods](#12-arrays--array-methods)
13. [Objects & Object Manipulation](#13-objects--object-manipulation)
14. [Destructuring](#14-destructuring)
15. [JSON Handling](#15-json-handling)
16. [DOM Manipulation](#16-dom-manipulation)
17. [Event Handling & Propagation](#17-event-handling--propagation)
18. [BOM (Browser Object Model)](#18-bom-browser-object-model)
19. [Web Storage & Cookies](#19-web-storage--cookies)
20. [Asynchronous JavaScript](#20-asynchronous-javascript)
21. [Promises](#21-promises)
22. [Async / Await](#22-async--await)
23. [Fetch API & AJAX](#23-fetch-api--ajax)
24. [Event Loop & Concurrency Model](#24-event-loop--concurrency-model)
25. [Introduction to Git](#25-introduction-to-git)

---

## 1. Introduction to JavaScript

**What is JavaScript?**
- A **lightweight, cross-platform, single-threaded** programming language for creating dynamic web content.
- **Interpreted** (line-by-line), but modern engines (V8) also use **JIT compilation**.
- **Weakly/dynamically typed** — no need to declare data types.
- Both **imperative and declarative**.
- Created in **1995 by Brendan Eich**. Standardized as **ECMAScript (ES)** in 1997.

**Client-Side vs Server-Side:**

| Aspect | Client-Side | Server-Side |
|--------|-------------|-------------|
| Runs in | Browser | Server (Node.js) |
| Controls | DOM, UI, user events | Databases, files, APIs |
| Libraries | React, Angular, Vue | Express, Node.js |

**Key Features:**
- DOM manipulation
- Functions are first-class objects
- Date/time handling, form validation
- No compiler needed
- Standard library: `Array`, `Date`, `Math`, operators, control structures

**Applications:** Web development, web apps, server apps (Node.js), games, mobile apps (React Native), machine learning (ml5.js), smartwatches (PebbleJS).

**Limitations:**
- **Security risks** — XSS attacks via AJAX / injected scripts
- **Performance** — slower than compiled languages for complex tasks
- **Weak error handling** — no compile-time type checking

---

## 2. Adding JS to HTML & Chrome DevTools

### Three Ways to Add JavaScript

**1. Internal JS (inside `<head>`):**
```html
<head>
  <script>
    function myFun() {
      document.getElementById("demo").innerHTML = "Changed!";
    }
  </script>
</head>
```

**2. Internal JS (inside `<body>`):**
```html
<body>
  <script>
    function myFun() {
      document.getElementById("demo").innerHTML = "Changed!";
    }
  </script>
</body>
```

**3. External JS:**
```html
<script src="script.js"></script>
```
- Can use full URL, file path, or just filename
- Advantages: separation of concerns, caching, maintainability

### JavaScript Output Methods

| Method | Description | Returns |
|--------|-------------|--------|
| `innerHTML` | Read/write HTML into an element | `string` (when reading) |
| `innerText` | Read/write plain text into an element | `string` (when reading) |
| `document.write()` | Write to HTML output (⚠️ overwrites page if used after load) | `undefined` |
| `window.alert()` | Display alert box | `undefined` |
| `console.log()` | Write to browser console (debugging) | `undefined` |
| `window.print()` | Print current window content | `undefined` |

### Chrome DevTools (F12 / Ctrl+Shift+I)

| Panel | Purpose |
|-------|---------|
| **Elements** | Inspect/modify HTML & CSS live |
| **Console** | Execute JS, view logs/errors |
| **Sources** | Debug JS, set breakpoints |
| **Network** | Monitor HTTP requests, analyze load times |
| **Performance** | Profile execution time, CPU/memory usage |
| **Security** | Inspect TLS/SSL, mixed content |
| **Lighthouse** | Audit performance, accessibility, SEO |

---

## 3. JavaScript Syntax, Variables & Data Types

### Variables

| Keyword | Scope | Reassignable | Hoisted |
|---------|-------|--------------|---------|
| `var` | Function/Global | ✅ | ✅ (as `undefined`) |
| `let` | Block | ✅ | ✅ (TDZ — not initialized) |
| `const` | Block | ❌ | ✅ (TDZ — not initialized) |

```js
var x = 10;     // function-scoped, hoisted
let y = "Hello"; // block-scoped
const PI = 3.14; // block-scoped, cannot reassign
```

### 8 JavaScript Data Types

| Type | Example |
|------|---------|
| **String** | `"Hello"`, `'World'` |
| **Number** | `42`, `3.14` |
| **BigInt** | `123456789n` |
| **Boolean** | `true`, `false` |
| **Object** | `{ name: "John" }` |
| **Array** (object) | `["a", "b", "c"]` |
| **Undefined** | `let x;` → `undefined` |
| **Null** | `let x = null;` |
| **Symbol** | `Symbol()` |

---

## 4. Operators

### Arithmetic Operators

| Operator | Operation | Example |
|----------|-----------|---------|
| `+` | Addition | `5 + 3` → `8` |
| `-` | Subtraction | `5 - 3` → `2` |
| `*` | Multiplication | `5 * 3` → `15` |
| `/` | Division | `6 / 2` → `3` |
| `%` | Modulus | `5 % 2` → `1` |
| `**` | Exponentiation | `2 ** 3` → `8` |
| `++` | Increment | `x++` |
| `--` | Decrement | `x--` |

### Assignment Operators
`=`, `+=`, `-=`, `*=`, `/=`, `%=`, `**=`

### Comparison Operators

| Operator | Description |
|----------|-------------|
| `==` | Equal (loose — type coercion) |
| `===` | Strict equal (value + type) |
| `!=` | Not equal (loose) |
| `!==` | Strict not equal |
| `>`, `<`, `>=`, `<=` | Relational |

### Logical Operators
- `&&` — AND
- `||` — OR
- `!` — NOT

### Logical Assignment (ES2021)
- `&&=`, `||=`, `??=`

---

## 5. Null vs Undefined

| | `undefined` | `null` |
|---|-------------|--------|
| **Meaning** | Variable declared but not assigned | Intentional absence of value |
| **Assignment** | Automatic | Manual |
| **typeof** | `"undefined"` | `"object"` (historical bug) |
| **Use case** | Check if variable initialized | Explicitly clear a variable |

```js
null == undefined   // true  (loose equality)
null === undefined  // false (different types)
```

---

## 6. Type Coercion

### Implicit (Automatic)
```js
5 + '5'      // '55'   (number → string)
'5' - 2      // 3      (string → number)
true + 1     // 2      (boolean → number)
```

### Explicit (Manual)
```js
Number('5')        // 5        → Returns: number
String(10)         // '10'     → Returns: string
Boolean(1)         // true     → Returns: boolean
parseInt("42px")   // 42       → Returns: number or NaN
parseFloat("3.14") // 3.14     → Returns: number or NaN
isNaN(NaN)         // true     → Returns: true / false
isFinite(42)       // true     → Returns: true / false
```

### Falsy Values
`false`, `0`, `''`, `null`, `undefined`, `NaN`

### Best Practices
- Use `===` (strict equality) instead of `==`
- Use explicit conversion functions for clarity

---

## 7. Control Flow — Conditionals & Loops

### Conditionals

**if / else if / else:**
```js
if (condition1) {
  // ...
} else if (condition2) {
  // ...
} else {
  // ...
}
```

**switch:**
```js
switch (expression) {
  case x: /* ... */ break;
  case y: /* ... */ break;
  default: /* ... */
}
```

**Ternary Operator:**
```js
condition ? expr1 : expr2;
```

### Loops

| Loop | Use Case |
|------|----------|
| `for` | Known number of iterations |
| `while` | Unknown iterations, condition-based |
| `do...while` | Execute at least once |
| `for...in` | Iterate over object keys / array indices |
| `for...of` | Iterate over iterable values (arrays, strings) |

```js
// for
for (let i = 0; i < 5; i++) { console.log(i); }

// while
while (i < 5) { console.log(i); i++; }

// do...while
do { console.log(i); i++; } while (i < 5);

// for...in (object keys)
for (let key in person) { console.log(key, person[key]); }

// for...of (array values)
for (let val of arr) { console.log(val); }
```

**Loop Scope:** Variables declared with `let`/`const` inside a loop are **block-scoped** — not visible outside.

---

## 8. Functions & Scoping

### Function Types

**1. Function Declaration (hoisted):**
```js
function greet(name) {
  return "Hello " + name;
}
```

**2. Function Expression (NOT hoisted):**
```js
const greet = function(name) {
  return "Hello " + name;
};
```

**3. Arrow Function (ES6):**
```js
const greet = (name) => "Hello " + name;

// No params
const hi = () => "Hi!";

// Single param (parentheses optional)
const square = x => x * x;

// Multiple params
const add = (a, b) => a + b;
```

### Parameters vs Arguments
- **Parameters** = placeholders in function definition
- **Arguments** = actual values passed during call

### Argument Types
| Type | Description |
|------|-------------|
| Required | Must be supplied; missing = `undefined` |
| Default (ES6) | Fallback value: `function greet(name = "Guest")` |
| Keyword-like | Use objects: `function create({name, age})` |
| Variable-length (Rest) | `function sum(...values)` |

### Scope

| Scope | Description |
|-------|-------------|
| **Global** | Declared outside all functions; accessible everywhere |
| **Local/Function** | Declared inside a function; accessible only within |
| **Block** | `let`/`const` inside `{}` — accessible only within block |
| **Lexical** | Inner functions access outer function's variables |

### Call by Value vs Reference

| Type | Data Types | Effect |
|------|-----------|--------|
| **Value** | Number, String, Boolean | Copy sent; original unchanged |
| **Reference** | Array, Object | Reference sent; original IS changed |

### Recursive Functions
A function that calls itself. Must have a **base case**.
```js
function factorial(n) {
  if (n === 1) return 1;
  return n * factorial(n - 1);
}
```

### Function Binding (`this`)
- `this` refers to the object a method belongs to
- In regular functions: refers to global object (`window`)
- `bind(thisArg)` — **Returns:** a new function with `this` permanently bound
- `call(thisArg, args...)` — **Returns:** result of the function call (invokes immediately)
- `apply(thisArg, [args])` — **Returns:** result of the function call (invokes immediately)

### Arrow Functions & Lexical `this`

Arrow functions **do NOT have their own `this`**. They inherit `this` from the **enclosing (lexical) scope**.

```js
// ❌ Regular function — `this` is the global object (or undefined in strict mode)
const person = {
  name: "Alice",
  greet: function() {
    setTimeout(function() {
      console.log(this.name);  // undefined! (`this` = window)
    }, 1000);
  }
};

// ✅ Arrow function — `this` is inherited from greet()
const person2 = {
  name: "Alice",
  greet: function() {
    setTimeout(() => {
      console.log(this.name);  // "Alice" ✅ (lexical `this`)
    }, 1000);
  }
};
```

**Key Differences:**

| Feature | Regular Function | Arrow Function |
|---------|-----------------|----------------|
| `this` | Own `this` (depends on caller) | **Lexical** `this` (from enclosing scope) |
| `arguments` | Has own `arguments` object | ❌ No `arguments` (use rest `...args`) |
| Constructor | Can use `new` | ❌ Cannot use `new` |
| Methods | ✅ Use for object methods | ❌ Avoid for object methods |

> **Rule of thumb:** Use arrow functions for callbacks (e.g. `setTimeout`, `map`, `forEach`). Use regular functions for object methods and constructors.

---

## 9. Hoisting

**Definition:** JS moves declarations to the top of their scope during compilation.

| Declaration | Behavior |
|-------------|----------|
| `var` | Hoisted, initialized as `undefined` |
| `let` / `const` | Hoisted but **NOT initialized** (Temporal Dead Zone) |
| Function declaration | **Fully hoisted** (can call before declaration) |
| Function expression | Hoisted as variable only (not callable before) |

```js
console.log(x);  // undefined (var is hoisted)
var x = 5;

console.log(y);  // ReferenceError (let is in TDZ)
let y = 10;

greet();  // Works! (function declaration is fully hoisted)
function greet() { console.log("Hi"); }
```

---

## 10. Closures

**Definition:** A closure is when an inner function **retains access** to variables from its outer scope, even after the outer function has finished executing.

```js
function outer() {
  let count = 0;
  function inner() {
    count++;
    return count;
  }
  return inner;
}
const counter = outer();
counter(); // 1
counter(); // 2
```

### Practical Uses
- **Data hiding / encapsulation** — private variables
- **Maintaining state** across function calls
- **Function factories** — functions that return customized functions
- **Callbacks & event handlers**

### Function Factories (Closure Pattern)

A function factory is a function that **returns a new function** customized by its arguments. Uses closures to "remember" the configuration.

```js
// Multiplier factory
function createMultiplier(multiplier) {
  return function(num) {
    return num * multiplier;  // `multiplier` is remembered via closure
  };
}

const double = createMultiplier(2);
const triple = createMultiplier(3);

double(5);  // 10
triple(5);  // 15
```

```js
// Greeting factory
function greetFactory(greeting) {
  return function(name) {
    return `${greeting}, ${name}!`;
  };
}

const sayHello = greetFactory("Hello");
const sayNamaste = greetFactory("Namaste");

sayHello("Alice");    // "Hello, Alice!"
sayNamaste("Bob");    // "Namaste, Bob!"
```

```js
// Private counter using closure
function createCounter() {
  let count = 0;  // private — not accessible from outside
  return {
    increment: () => ++count,
    decrement: () => --count,
    getCount: () => count
  };
}

const counter = createCounter();
counter.increment(); // 1
counter.increment(); // 2
counter.decrement(); // 1
counter.getCount();  // 1
// counter.count → undefined (private!)
```

---

## 11. Higher-Order Functions

**Definition:** A function that takes another function as an argument OR returns a function.

| Method | Purpose |
|--------|---------|
| `map()` | Transform each element → new array |
| `filter()` | Select elements that pass a condition → new array |
| `reduce()` | Reduce array to a single value |
| `forEach()` | Execute function for each element (no return) |
| `setTimeout()` | Execute function after a delay (async) |

### setTimeout & setInterval — Deep Dive

**`setTimeout(callback, delay)`** — executes the callback **once** after `delay` ms. **Returns:** timeout ID (`number`).

```js
// Basic usage
setTimeout(() => console.log("Runs after 2 seconds"), 2000);

// With arguments (pass as extra params)
setTimeout((name, age) => {
  console.log(`${name} is ${age}`);
}, 1000, "Alice", 25);  // "Alice is 25" after 1s

// Cancel before it fires
const id = setTimeout(() => console.log("Never runs"), 5000);
clearTimeout(id);
```

**`setInterval(callback, delay)`** — executes the callback **repeatedly** every `delay` ms. **Returns:** interval ID (`number`).

```js
let count = 0;
const id = setInterval(() => {
  count++;
  console.log(`Tick ${count}`);
  if (count === 5) clearInterval(id);  // Stop after 5 ticks
}, 1000);
```

**⚠️ The `this` Problem with setTimeout:**
```js
const user = {
  name: "Alice",
  greet: function() {
    // ❌ Regular function — `this` is lost inside setTimeout
    setTimeout(function() {
      console.log(this.name);  // undefined
    }, 1000);

    // ✅ Fix 1: Arrow function (lexical this)
    setTimeout(() => {
      console.log(this.name);  // "Alice"
    }, 1000);

    // ✅ Fix 2: bind()
    setTimeout(function() {
      console.log(this.name);  // "Alice"
    }.bind(this), 1000);

    // ✅ Fix 3: Store reference
    const self = this;
    setTimeout(function() {
      console.log(self.name);  // "Alice"
    }, 1000);
  }
};
```

**⏱️ setTimeout with 0ms delay:**
```js
console.log("1");                          // 1st
setTimeout(() => console.log("2"), 0);     // 3rd (async — goes to task queue)
console.log("3");                          // 2nd
// Output: 1 → 3 → 2  (even with 0ms, setTimeout is async!)
```

---

## 12. Arrays & Array Methods

An **array** is an ordered collection of values (any type), indexed from `0`.

```js
let arr = [10, 20, 30, 40, 50];
```

### Basic Methods

| Method | Description | Returns | Example |
|--------|-------------|---------|--------|
| `length` | Number of elements | `number` | `[1,2,3].length` → `3` |
| `toString()` | Array → comma-separated string | `string` | `[1,2,3].toString()` → `"1,2,3"` |
| `at(index)` | Element at index (supports negative) | Element or `undefined` | `[10,20,30].at(-1)` → `30` |
| `join(sep)` | Join elements with separator | `string` | `["a","b"].join("-")` → `"a-b"` |
| `pop()` | Remove **last** element | Removed element or `undefined` | `[1,2,3].pop()` → `3` |
| `push(val)` | Add to **end** | New `length` (`number`) | `[1,2].push(3)` → `3` |
| `shift()` | Remove **first** element | Removed element or `undefined` | `[1,2,3].shift()` → `1` |
| `unshift(val)` | Add to **beginning** | New `length` (`number`) | `[0,1,2].unshift(-1)` → `4` |
| `delete arr[i]` | Delete element (leaves `undefined` hole) | `true` / `false` | `delete arr[1]` → `true` |

### Manipulation Methods

| Method | Description | Returns | Mutates? |
|--------|-------------|---------|----------|
| `concat()` | Merge arrays | New merged `Array` | ❌ |
| `slice(start, end)` | Extract portion | New `Array` (shallow copy) | ❌ |
| `splice(i, n, items)` | Add/remove elements in place | `Array` of **removed elements** (`[]` if none) | ✅ |
| `toSpliced(i, n, items)` | Like splice but immutable | New `Array` | ❌ |
| `flat(depth)` | Flatten nested arrays | New flattened `Array` | ❌ |
| `copyWithin(target, start, end)` | Copy part to another position | The **modified array** (same ref) | ✅ |
| `sort(compareFn)` | Sort elements in place | The **sorted array** (same ref) | ✅ |
| `reverse()` | Reverse elements in place | The **reversed array** (same ref) | ✅ |
| `toSorted(compareFn)` | Like sort but immutable | New sorted `Array` | ❌ |
| `toReversed()` | Like reverse but immutable | New reversed `Array` | ❌ |
| `fill(value, start, end)` | Fill with static value | The **modified array** (same ref) | ✅ |
| `Array.isArray(val)` | Check if value is array | `true` / `false` | ❌ |

```js
[1,2].concat([3,4]);            // [1,2,3,4]
[1,2,3,4].slice(1,3);           // [2,3]
arr.splice(1, 2, "a");          // returns removed: e.g. [2,3]
arr.toSpliced(1, 1, "x");       // returns new array
[1,[2,[3]]].flat(2);            // [1,2,3]
[1,2,3,4].copyWithin(0,2);     // [3,4,3,4]
[3,1,2].sort();                 // [1,2,3] (mutates & returns same array)
[1,2,3].reverse();              // [3,2,1] (mutates & returns same array)
Array.isArray([1,2]);           // true
Array.isArray("hello");         // false
```

### Search Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `indexOf(val)` | First index of value | Index or `-1` |
| `lastIndexOf(val)` | Last index of value | Index or `-1` |
| `includes(val)` | Check if value exists | `true`/`false` |
| `find(fn)` | First element passing test | Value or `undefined` |
| `findIndex(fn)` | Index of first match | Index or `-1` |
| `findLast(fn)` | **Last** element passing test | Value or `undefined` |
| `findLastIndex(fn)` | Index of **last** match | Index or `-1` |

### Iteration / Functional Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `forEach(fn)` | Run function per element | `undefined` |
| `map(fn)` | Transform each element | New array |
| `filter(fn)` | Keep elements passing condition | New array |
| `reduce(fn, init)` | Accumulate to single value (left→right) | Single value |
| `reduceRight(fn, init)` | Accumulate (right→left) | Single value |
| `every(fn)` | All elements pass? | `true`/`false` |
| `some(fn)` | Any element passes? | `true`/`false` |
| `flatMap(fn)` | Map then flatten by 1 level | New array |

### Utility Methods

| Method | Description | Example |
|--------|-------------|---------|
| `Array.from(iterable)` | Create array from iterable | `Array.from("hi")` → `["h","i"]` |
| `keys()` | Iterator of indices | `[...arr.keys()]` |
| `entries()` | Iterator of `[index, value]` | `[...arr.entries()]` |
| `with(index, value)` | Replace at index → **new array** | `[1,2,3].with(1, 99)` → `[1,99,3]` |

```js
let nums = [1, 2, 3, 4, 5];

nums.map(x => x * 2);             // [2, 4, 6, 8, 10]
nums.filter(x => x > 3);          // [4, 5]
nums.reduce((s, x) => s + x, 0);  // 15
nums.some(x => x > 4);            // true
nums.every(x => x > 0);           // true
nums.find(x => x === 3);          // 3
nums.findIndex(x => x === 3);     // 2
[1,2,3].flatMap(x => [x, x*2]);   // [1,2,2,4,3,6]
["a","b","c"].reduceRight((s,x) => s+x, ""); // "cba"
```

---

## 13. Objects & Object Manipulation

Objects store data as **key–value pairs**.

```js
let person = { name: "Alice", age: 25, city: "London" };
```

### Accessing Properties

| Method | Syntax | Use Case |
|--------|--------|----------|
| **Dot notation** | `person.name` | Simple, readable |
| **Bracket notation** | `person["name"]` | Dynamic keys, keys with spaces |

### Object Manipulation
```js
// Add property
person.email = "alice@mail.com";

// Update property
person.age = 26;

// Delete property
delete person.city;
```

### Dynamic Property Names
```js
let key = "score";
let obj = { [key]: 100 };  // { score: 100 }
```

### Object Methods

| Method | Description | Returns |
|--------|-------------|--------|
| `Object.keys(obj)` | Get all keys | `Array` of strings |
| `Object.values(obj)` | Get all values | `Array` of values |
| `Object.entries(obj)` | Get key-value pairs | `Array` of `[key, value]` arrays |
| `Object.assign(target, src)` | Copy/merge properties | The **target object** (modified) |
| `Object.freeze(obj)` | Prevent all modifications | The **same object** (frozen) |
| `Object.isFrozen(obj)` | Check if object is frozen | `true` / `false` |
| `Object.create(proto)` | Create object with given prototype | New `Object` |
| `delete obj.prop` | Delete a property | `true` / `false` |
| `obj.hasOwnProperty(key)` | Check if own property exists | `true` / `false` |

```js
Object.keys(person);       // ["name", "age", "email"]  → Array of strings
Object.values(person);     // ["Alice", 26, "..."]     → Array of values
Object.entries(person);    // [["name","Alice"], ...]   → Array of [key,value]
Object.assign({}, person); // { ...clone }              → returns target object
Object.freeze(person);     // person (now frozen — no add/edit/delete)
delete person.city;        // true                      → boolean
person.hasOwnProperty("name"); // true                  → boolean
```

---

## 14. Destructuring

### Array Destructuring
```js
let [a, b, c] = [10, 20, 30];
// a=10, b=20, c=30

// Skip elements
let [x, , z] = [1, 2, 3];  // x=1, z=3

// Default values
let [a = 10, b = 20] = [5];  // a=5, b=20

// Rest operator
let [first, ...rest] = [10, 20, 30, 40];
// first=10, rest=[20, 30, 40]

// Swapping
[a, b] = [b, a];
```

### Object Destructuring
```js
let { name, age } = { name: "Alice", age: 25, city: "London" };

// Renaming
let { name: fullName, age: years } = person;

// Default values
let { a = 10, b = 20 } = { a: 5 };  // a=5, b=20

// Nested destructuring
const { section1: { alpha } } = marks;

// Rest operator
let { x, ...rest } = { x: 10, y: 20, z: 30 };
```

---

## 15. JSON Handling

**JSON (JavaScript Object Notation):** Lightweight data-interchange format. Keys and string values must be in **double quotes**.

```json
{ "name": "John", "age": 30, "isStudent": false }
```

| Method | Purpose | Returns |
|--------|---------|---------|
| `JSON.stringify(obj)` | Object → JSON string | `string` |
| `JSON.parse(str)` | JSON string → Object | Parsed value (`Object`, `Array`, etc.) |

---

## 16. DOM Manipulation

### What is the DOM?
**Document Object Model** — represents HTML as a **tree structure**. Each HTML element is a **node**. JS uses DOM to access, modify, add, or remove elements.

### Selecting Elements

| Method | Returns |
|--------|---------|
| `getElementById("id")` | `Element` or `null` |
| `getElementsByClassName("class")` | **Live** `HTMLCollection` (never `null`) |
| `getElementsByTagName("tag")` | **Live** `HTMLCollection` (never `null`) |
| `querySelector("CSS selector")` | First matching `Element` or `null` |
| `querySelectorAll("CSS selector")` | **Static** `NodeList` (never `null`) |

```js
const box = document.getElementById("box");
const items = document.getElementsByClassName("item"); // HTMLCollection
const paras = document.getElementsByTagName("p");       // HTMLCollection
const btn = document.querySelector(".btn");
const allLis = document.querySelectorAll("li");          // NodeList
allLis.forEach(item => console.log(item));
```

### Reading & Writing Content
```js
element.textContent            // Read plain text
element.innerText              // Read visible text (respects CSS hiding)
element.innerHTML              // Read HTML content
element.textContent = "Hello"; // Write text
element.innerText = "Hi";      // Write visible text
element.innerHTML = "<b>Hi</b>"; // Write HTML (⚠️ XSS risk)
```

### Changing Styles
```js
element.style.color = "red";
element.style.backgroundColor = "yellow";
// CSS properties use camelCase in JS
```

### Creating, Appending & Deleting Nodes
```js
// Create
const div = document.createElement("div");  // Returns: new Element
div.textContent = "New Element";

// Append
document.body.appendChild(div);     // Returns: the appended Node
document.body.append(div, "text");  // Returns: undefined
document.body.prepend(div);         // Returns: undefined

// Insert
parent.insertBefore(newNode, refNode); // Returns: the inserted Node

// Delete
element.remove();                   // Returns: undefined
parent.removeChild(child);          // Returns: the removed Node
parent.replaceChild(newChild, old); // Returns: the replaced (old) Node
```

### Class Manipulation
```js
element.classList.add("active");      // Returns: undefined
element.classList.remove("active");   // Returns: undefined
element.classList.toggle("active");   // Returns: true (added) / false (removed)
element.classList.contains("active"); // Returns: true / false
```

### Attributes
```js
element.setAttribute("data-id", "42");  // Returns: undefined
element.getAttribute("data-id");        // Returns: string or null
element.removeAttribute("data-id");     // Returns: undefined
element.hasAttribute("data-id");        // Returns: true / false
```

---

## 17. Event Handling & Propagation

### addEventListener()
```js
element.addEventListener("event", handlerFunction);

btn.addEventListener("click", function(event) {
  alert("Clicked!");
  console.log(event.target);        // Element that triggered the event
  console.log(event.currentTarget); // Element the listener is attached to
});
```

### Event Methods

| Method | Purpose | Returns |
|--------|---------|--------|
| `addEventListener(type, fn)` | Attach event handler | `undefined` |
| `removeEventListener(type, fn)` | Remove event handler | `undefined` |
| `preventDefault()` | Stop default browser action (e.g. form submit, link navigation) | `undefined` |
| `stopPropagation()` | Stop event from bubbling/capturing further | `undefined` |
| `stopImmediatePropagation()` | Stop all handlers + propagation | `undefined` |

### Event Properties

| Property | Returns |
|----------|---------|
| `event.target` | `Element` that **triggered** the event |
| `event.currentTarget` | `Element` the **listener is attached to** |
| `event.type` | `string` (e.g. `"click"`, `"submit"`) |
| `event.key` | `string` (keyboard key pressed) |
| `event.clientX` / `event.clientY` | `number` (mouse coordinates) |

### Event Propagation

| Type | Direction | Default? |
|------|-----------|----------|
| **Bubbling** | Child → Parent | ✅ Yes |
| **Capturing** | Parent → Child | ❌ (enable with `true` as 3rd arg) |

```js
// Capturing mode
element.addEventListener("click", handler, true);
```

### Event Delegation
Attach a **single event listener to a parent** instead of each child. Uses bubbling.
```js
document.getElementById("list").addEventListener("click", function(e) {
  if (e.target.tagName === "LI") {
    console.log(e.target.textContent);
  }
});
```
**Benefits:** Better performance, works for dynamically added elements.

### Form Validation
```js
form.addEventListener("submit", function(e) {
  let name = document.getElementById("name").value;
  if (name === "") {
    alert("Name is required");
    e.preventDefault();  // Stop form submission
  }
});
```

### DOM Performance Tips
- Minimize DOM access
- Use event delegation
- Batch DOM updates
- Avoid reflows
- Use `classList` instead of `style`

---

## 18. BOM (Browser Object Model)

BOM allows JS to interact with the browser (window, URL, screen, etc.).

### Window Object (Global)
```js
window.innerHeight   // Browser window height
window.innerWidth    // Browser window width
```

### User Interaction Methods

| Method | Returns | Purpose |
|--------|---------|---------|
| `alert("msg")` | — | Show message |
| `confirm("msg")` | `true`/`false` | OK/Cancel dialog |
| `prompt("msg")` | User input string | Get user input |

### Navigator Object
```js
navigator.userAgent   // Browser details
navigator.language    // Browser language
navigator.onLine      // Internet status (true/false)
```

### Location Object
```js
location.href       // Full URL
location.hostname   // Domain name
location.pathname   // Page path
location.href = "https://google.com";  // Redirect
location.reload();  // Reload current page
```

### Pop-up Windows
```js
window.open("https://example.com");  // Returns: Window object or null
window.close();                       // Returns: undefined
```

### Timers

| Method | Behavior | Returns |
|--------|----------|--------|
| `setTimeout(fn, ms)` | Run **once** after delay | Timeout ID (`number`) |
| `clearTimeout(id)` | Cancel a `setTimeout` | `undefined` |
| `setInterval(fn, ms)` | Run **repeatedly** at interval | Interval ID (`number`) |
| `clearInterval(id)` | Stop an interval | `undefined` |

```js
let tid = setTimeout(() => console.log("Hello"), 2000);
clearTimeout(tid);  // Cancel it before it fires

let iid = setInterval(() => console.log("Tick"), 1000);
clearInterval(iid);  // Stop it
```

---

## 19. Web Storage & Cookies

### LocalStorage (Permanent)
- Data persists even after browser closes
- Shared across tabs (same origin)

```js
localStorage.setItem("key", "value");   // Returns: undefined
localStorage.getItem("key");            // Returns: string or null
localStorage.removeItem("key");         // Returns: undefined
localStorage.clear();                   // Returns: undefined
localStorage.key(0);                    // Returns: key name (string) or null
localStorage.length;                    // Returns: number of stored items
```

### SessionStorage (Temporary)
- Data deleted when tab is closed
- NOT shared across tabs

```js
sessionStorage.setItem("user", "Admin");  // Returns: undefined
sessionStorage.getItem("user");           // Returns: string or null
sessionStorage.removeItem("user");        // Returns: undefined
sessionStorage.clear();                   // Returns: undefined
```

### Cookies
- Sent to server with every HTTP request
- Used for authentication & tracking

```js
document.cookie = "username=Rohan";
document.cookie = "age=22; expires=Fri, 31 Dec 2026 12:00:00 UTC";
```

### Comparison

| Feature | LocalStorage | SessionStorage | Cookies |
|---------|-------------|----------------|---------|
| Persistence | Permanent | Tab session | Expiry-based |
| Size | ~5-10 MB | ~5 MB | ~4 KB |
| Sent to server | ❌ | ❌ | ✅ |
| Shared across tabs | ✅ | ❌ | ✅ |

---

## 📋 Methods Covered in 1 Marks

### 1. Array Methods

#### 🔹 Basic Methods

| Method | Description | Example |
|--------|-------------|---------|
| `length` | Returns number of elements | `[1,2,3].length` → `3` |
| `toString()` | Converts array to comma-separated string | `[1,2,3].toString()` → `"1,2,3"` |
| `at(index)` | Returns element at index (supports negative) | `[10,20,30].at(-1)` → `30` |
| `join(sep)` | Joins elements with separator | `["a","b"].join("-")` → `"a-b"` |
| `pop()` | Removes & returns **last** element | `arr.pop()` |
| `push(val)` | Adds element to **end**, returns new length | `arr.push(40)` |
| `shift()` | Removes & returns **first** element | `arr.shift()` |
| `unshift(val)` | Adds element to **beginning** | `arr.unshift(0)` |
| `delete` | Deletes element (leaves `undefined` hole) | `delete arr[1]` |

#### 🔹 Manipulation

| Method | Description | Example |
|--------|-------------|---------|
| `concat()` | Merges arrays → new array | `[1,2].concat([3,4])` → `[1,2,3,4]` |
| `slice(start, end)` | Extracts portion → new array (no mutation) | `[1,2,3,4].slice(1,3)` → `[2,3]` |
| `splice(i, n, items)` | Add/remove elements **in place** (mutates) | `arr.splice(1, 2, "a")` |
| `toSpliced(i, n, items)` | Like splice but returns **new array** (no mutation) | `arr.toSpliced(1, 1, "x")` |
| `flat(depth)` | Flattens nested arrays | `[1,[2,[3]]].flat(2)` → `[1,2,3]` |
| `copyWithin(target, start, end)` | Copies part of array to another position (mutates) | `[1,2,3,4].copyWithin(0,2)` → `[3,4,3,4]` |

#### 🔹 Search Methods

| Method | Description | Example |
|--------|-------------|---------|
| `indexOf(val)` | First index of value (or `-1`) | `[1,2,3].indexOf(2)` → `1` |
| `lastIndexOf(val)` | Last index of value (or `-1`) | `[1,2,1].lastIndexOf(1)` → `2` |
| `includes(val)` | Checks if value exists | `[1,2,3].includes(2)` → `true` |
| `find(fn)` | First element passing test | `[5,12,8].find(x => x > 10)` → `12` |
| `findIndex(fn)` | Index of first element passing test | `[5,12,8].findIndex(x => x > 10)` → `1` |
| `findLast(fn)` | **Last** element passing test | `[5,12,8,15].findLast(x => x > 10)` → `15` |
| `findLastIndex(fn)` | Index of **last** element passing test | `[5,12,8,15].findLastIndex(x => x > 10)` → `3` |

#### 🔹 Iteration Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `forEach(fn)` | Runs function for each element | `undefined` |
| `map(fn)` | Transforms each element | New array |
| `filter(fn)` | Keeps elements passing condition | New array |
| `reduce(fn, init)` | Accumulates to single value (left→right) | Single value |
| `reduceRight(fn, init)` | Accumulates to single value (right→left) | Single value |
| `every(fn)` | All pass? | `true`/`false` |
| `some(fn)` | Any pass? | `true`/`false` |
| `flatMap(fn)` | Maps then flattens by 1 level | New array |

```js
// flatMap example
[1, 2, 3].flatMap(x => [x, x * 2]);  // [1, 2, 2, 4, 3, 6]

// reduceRight example
[[1,2],[3,4],[5,6]].reduceRight((acc, val) => acc.concat(val), []);
// [5, 6, 3, 4, 1, 2]
```

#### 🔹 Utility

| Method | Description | Example |
|--------|-------------|---------|
| `Array.from(iterable)` | Creates array from iterable/array-like | `Array.from("hello")` → `["h","e","l","l","o"]` |
| `keys()` | Returns iterator of indices | `[...arr.keys()]` → `[0,1,2]` |
| `entries()` | Returns iterator of `[index, value]` pairs | `[...arr.entries()]` → `[[0,"a"],[1,"b"]]` |
| `with(index, value)` | Replaces element at index → **new array** | `[1,2,3].with(1, 99)` → `[1,99,3]` |

---

### 2. Object Methods / Concepts

**Object Literal:**
```js
let obj = { name: "Alice", age: 25 };
```

**Property Access:**
```js
obj.name        // Dot notation → "Alice"
obj["name"]     // Bracket notation → "Alice"
```

**Dynamic Properties:**
```js
let key = "score";
let obj = { [key]: 100 };  // { score: 100 }
```

**Methods:**

| Method | Description | Example |
|--------|-------------|---------|
| `Object.keys(obj)` | Returns array of keys | `Object.keys({a:1, b:2})` → `["a","b"]` |
| `Object.values(obj)` | Returns array of values | `Object.values({a:1, b:2})` → `[1, 2]` |
| `Object.entries(obj)` | Returns array of `[key, value]` pairs | `Object.entries({a:1})` → `[["a",1]]` |
| `Object.assign(target, src)` | Copies properties from src to target | `Object.assign({}, obj1, obj2)` |

---

### 3. Destructuring

#### 🔹 Array Destructuring
```js
let [a, b] = [10, 20];          // a=10, b=20
let [a, , b] = [1, 2, 3];       // a=1, b=3 (skip middle)
let [a = 10] = [];               // a=10 (default value)
let [x, y] = [1, 2]; [x, y] = [y, x];  // Swap → x=2, y=1
```

#### 🔹 Object Destructuring
```js
let { name } = obj;              // Extract name
let { a: x } = { a: 10 };       // Rename: x=10
let { a = 10 } = {};            // Default: a=10
let { outer: { inner } } = obj; // Nested destructuring
```

---

### 4. JSON Handling

| Method | Purpose | Example |
|--------|---------|---------|
| `JSON.stringify(obj)` | Object → JSON string | `JSON.stringify({a:1})` → `'{"a":1}'` |
| `JSON.parse(str)` | JSON string → Object | `JSON.parse('{"a":1}')` → `{a: 1}` |

---

### 5. DOM Manipulation

#### 🔹 Selectors

| Method | Returns |
|--------|---------|
| `querySelector("css")` | First matching element |
| `querySelectorAll("css")` | NodeList of all matches |
| `getElementById("id")` | Single element by ID |
| `getElementsByClassName("cls")` | HTMLCollection by class |
| `getElementsByTagName("tag")` | HTMLCollection by tag name |

#### 🔹 Content & Style

| Property/Method | Description |
|----------------|-------------|
| `innerHTML` | Gets/sets HTML content (parses tags) |
| `innerText` | Gets/sets visible text content |
| `style.property` | Sets inline CSS (`element.style.color = "red"`) |

#### 🔹 Node Operations

| Method | Description |
|--------|-------------|
| `createElement("tag")` | Creates a new HTML element |
| `appendChild(node)` | Appends child at end (returns node) |
| `append(nodes...)` | Appends multiple nodes/strings (no return) |
| `remove()` | Removes the element from DOM |
| `classList.add("cls")` | Adds a CSS class |
| `classList.remove("cls")` | Removes a CSS class |
| `classList.toggle("cls")` | Toggles a CSS class on/off |
| `setAttribute("attr", "val")` | Sets an HTML attribute |
| `getAttribute("attr")` | Gets an HTML attribute value |

---

### 6. Event Handling

**addEventListener:**
```js
element.addEventListener("click", function(event) {
  console.log(event.target);        // Element that triggered event
  console.log(event.currentTarget); // Element listener is attached to
});
```

**Methods:**

| Method | Purpose |
|--------|---------|
| `preventDefault()` | Stops default browser action (e.g. form submit) |
| `stopPropagation()` | Stops event from bubbling/capturing further |

**🔹 Concepts:**
- **Event Bubbling** — event goes Child → Parent (default)
- **Event Capturing** — event goes Parent → Child (`addEventListener("click", fn, true)`)
- **Event Delegation** — single listener on parent, use `e.target` to identify child

---

### 7. BOM (Browser Object Model)

#### 🔹 Window Methods

| Method | Description |
|--------|-------------|
| `alert("msg")` | Shows alert dialog |
| `confirm("msg")` | OK/Cancel dialog → returns `true`/`false` |
| `prompt("msg")` | Input dialog → returns string or `null` |
| `open(url)` | Opens new browser window/tab |
| `close()` | Closes current window |

#### 🔹 Timer Methods

| Method | Description |
|--------|-------------|
| `setTimeout(fn, ms)` | Runs function **once** after delay |
| `clearTimeout(id)` | Cancels a `setTimeout` |
| `setInterval(fn, ms)` | Runs function **repeatedly** at interval |
| `clearInterval(id)` | Cancels a `setInterval` |

#### 🔹 Other Objects

| Object/Property | Description |
|----------------|-------------|
| `navigator` | Browser info (`userAgent`, `language`, `onLine`) |
| `location.href` | Full URL of current page |
| `location.reload()` | Reloads current page |

---

### 8. Web Storage

**localStorage** (persists after browser close):
```js
localStorage.setItem("key", "value");
localStorage.getItem("key");
localStorage.removeItem("key");
localStorage.clear();
```

**sessionStorage** (deleted when tab closes):
```js
sessionStorage.setItem("user", "Admin");
sessionStorage.getItem("user");
```

**Cookies** (sent to server with every HTTP request):
```js
document.cookie = "username=Rohan; expires=Fri, 31 Dec 2026 12:00:00 UTC";
```

---

## 📋 Methods Covered in 2 Marks

### 1. ARRAY (Methods & Concepts)

#### 🔹 Core Methods
```js
arr.push(4);            // Add to end → [1,2,3,4]
arr.pop();              // Remove from end → [1,2,3]
arr.shift();            // Remove from start → [2,3]
arr.unshift(0);         // Add to start → [0,2,3]

arr.slice(1, 3);        // Extract [1,3) → new array, no mutation
arr.splice(1, 2, "a");  // Remove 2 from index 1, insert "a" → mutates
arr.toSpliced(1, 1, "x"); // Like splice → returns new array, no mutation

[1,2].concat([3,4]);    // Merge → [1,2,3,4]
[1,[2,[3]]].flat(Infinity); // Flatten all levels → [1,2,3]
[1,2,3,4].copyWithin(0, 2); // Copy index 2+ to index 0 → [3,4,3,4]
```

#### 🔹 Iteration / Functional
```js
// map — transform each element → new array
[1,2,3].map(x => x * 2);               // [2, 4, 6]

// filter — keep elements passing test → new array
[1,2,3,4,5].filter(x => x > 3);        // [4, 5]

// reduce — accumulate to single value (left → right)
[1,2,3].reduce((sum, x) => sum + x, 0); // 6

// reduceRight — accumulate (right → left)
["a","b","c"].reduceRight((s, x) => s + x, ""); // "cba"

// forEach — execute function per element (no return value)
[1,2,3].forEach(x => console.log(x));

// some — does ANY element pass? → true/false
[1,2,3].some(x => x > 2);              // true

// every — do ALL elements pass? → true/false
[1,2,3].every(x => x > 0);             // true

// flatMap — map + flatten by 1 level
[1, 2].flatMap(x => [x, x * 10]);      // [1, 10, 2, 20]
```

#### 🔹 Search
```js
[1,2,3,2].indexOf(2);       // 1  (first occurrence)
[1,2,3,2].lastIndexOf(2);   // 3  (last occurrence)
[1,2,3].includes(2);        // true

[5,12,8].find(x => x > 10);          // 12  (first match)
[5,12,8].findIndex(x => x > 10);     // 1   (index of first match)
[5,12,8,15].findLast(x => x > 10);       // 15 (last match)
[5,12,8,15].findLastIndex(x => x > 10);  // 3  (index of last match)
```

#### 🔹 Utility
```js
Array.from("hello");         // ["h","e","l","l","o"]
Array.from({length: 3}, (_, i) => i); // [0, 1, 2]

[...["a","b","c"].keys()];      // [0, 1, 2]
[...["a","b","c"].entries()];   // [[0,"a"], [1,"b"], [2,"c"]]

[1,2,3].with(1, 99);           // [1, 99, 3] — new array
```

---

### 2. OBJECT (Methods & Concepts)

```js
// Object literal
let person = { name: "Alice", age: 25 };

// Access
person.name;          // Dot → "Alice"
person["name"];       // Bracket → "Alice"

// Dynamic properties
let key = "score";
let obj = { [key]: 100 };  // { score: 100 }
```

#### 🔹 Methods
```js
Object.keys({a:1, b:2});      // ["a", "b"]
Object.values({a:1, b:2});    // [1, 2]
Object.entries({a:1, b:2});   // [["a",1], ["b",2]]
Object.assign({}, obj1, obj2); // Merge/clone objects
```

---

### 3. DESTRUCTURING

#### 🔹 Array
```js
let [a, b] = [10, 20];           // a=10, b=20
let [a, , b] = [1, 2, 3];        // a=1, b=3
let [a = 10] = [];                // a=10 (default)
let [x, y] = [1, 2];
[x, y] = [y, x];                 // Swap → x=2, y=1
```

#### 🔹 Object
```js
let { name } = { name: "Alice", age: 25 };  // name="Alice"
let { a: x } = { a: 10 };                   // x=10 (rename)
let { a = 10 } = {};                        // a=10 (default)

// Nested
const { section: { alpha } } = { section: { alpha: 90 } };
```

---

### 4. JSON HANDLING

```js
// Object → JSON string
let jsonStr = JSON.stringify({ name: "John", age: 30 });
// '{"name":"John","age":30}'

// JSON string → Object
let obj = JSON.parse('{"name":"John","age":30}');
// { name: "John", age: 30 }
```

---

### 5. DOM MANIPULATION

#### 🔹 Selectors
```js
document.querySelector(".btn");            // First .btn element
document.querySelectorAll("li");           // All <li> elements
document.getElementById("box");           // Element with id="box"
document.getElementsByClassName("item");   // All elements with class="item"
document.getElementsByTagName("p");        // All <p> elements
```

#### 🔹 Content / Style
```js
element.innerHTML = "<b>Bold</b>";   // Set HTML content
element.innerText = "Plain text";    // Set plain text
element.style.color = "red";        // Set inline CSS
element.style.backgroundColor = "#333";
```

#### 🔹 Node Operations
```js
// Create & append
const div = document.createElement("div");
div.textContent = "Hello";
document.body.appendChild(div);   // Append single node
document.body.append(div, "text"); // Append multiple nodes/strings

// Remove
element.remove();

// Class manipulation
element.classList.add("active");
element.classList.remove("active");
element.classList.toggle("active");  // Add if missing, remove if present

// Attributes
element.setAttribute("data-id", "42");
element.getAttribute("data-id");     // "42"
```

---

### 6. EVENT HANDLING

#### 🔹 Methods
```js
element.addEventListener("click", handler);

function handler(event) {
  event.preventDefault();     // Stop default action
  event.stopPropagation();   // Stop bubbling/capturing
}
```

#### 🔹 Properties
```js
event.target;         // Element that TRIGGERED the event
event.currentTarget;  // Element the LISTENER is attached to
```

#### 🔹 Concepts

| Concept | Description |
|---------|-------------|
| **Event Bubbling** | Event propagates Child → Parent (default) |
| **Event Capturing** | Event propagates Parent → Child (use `true` as 3rd arg) |
| **Event Delegation** | Attach one listener to parent; use `e.target` to identify child |

```js
// Bubbling (default)
child.addEventListener("click", fn);

// Capturing
parent.addEventListener("click", fn, true);

// Delegation
document.getElementById("list").addEventListener("click", (e) => {
  if (e.target.tagName === "LI") {
    console.log(e.target.textContent);
  }
});
```

---

### 7. BOM (Browser Object Model)

#### 🔹 Window Methods
```js
alert("Hello!");              // Message box
let ok = confirm("Sure?");   // OK → true, Cancel → false
let name = prompt("Name?");  // User input or null
window.open("https://example.com");  // Open new tab
window.close();              // Close current window
```

#### 🔹 Timers
```js
let tid = setTimeout(() => console.log("Once"), 2000);
clearTimeout(tid);            // Cancel timeout

let iid = setInterval(() => console.log("Repeat"), 1000);
clearInterval(iid);           // Cancel interval
```

#### 🔹 Objects
```js
navigator.userAgent;    // Browser info string
navigator.language;     // e.g. "en-US"
navigator.onLine;       // true/false

location.href;          // Full URL
location.reload();      // Reload the page
location.href = "https://google.com";  // Redirect
```

---

### 8. WEB STORAGE

```js
// localStorage — persists permanently
localStorage.setItem("key", "value");
localStorage.getItem("key");       // "value"
localStorage.removeItem("key");
localStorage.clear();               // Remove all

// sessionStorage — cleared on tab close
sessionStorage.setItem("user", "Admin");
sessionStorage.getItem("user");

// Cookies — sent to server with every request
document.cookie = "username=Rohan";
document.cookie = "token=abc; expires=Fri, 31 Dec 2026 12:00:00 UTC";
```

---

## 20. Asynchronous JavaScript

JS is **single-threaded** but handles async operations via the **event loop**.

### Why Async?
- Prevents blocking (freezing) the UI
- Essential for API calls, timers, file I/O

### Callback Functions
A function passed to another function, called after an async task completes.
```js
setTimeout(function() {
  console.log("Done!");
}, 2000);
```

**Callback Hell:** Deeply nested callbacks → hard to read/debug. ❌

---

## 21. Promises

A **Promise** is an object representing the future completion/failure of an async operation.

### Promise Lifecycle
`Pending` → `Fulfilled` (resolved) OR `Rejected`

```js
let promise = new Promise((resolve, reject) => {
  // async work...
  resolve("Success");   // on success
  // reject("Error");   // on failure
});
```

### Promise Methods

| Method | Purpose |
|--------|---------|
| `.then(fn)` | Handle fulfilled promise |
| `.catch(fn)` | Handle rejected promise |
| `.finally(fn)` | Run regardless (cleanup) |

```js
promise
  .then(result => console.log(result))
  .catch(error => console.error(error))
  .finally(() => console.log("Done"));
```

### Promise Combinators

| Method | Behavior |
|--------|----------|
| `Promise.all([...])` | Resolves when **all** succeed; rejects if **any** fail |
| `Promise.race([...])` | Resolves with **first** settled promise |

---

## 22. Async / Await

**Modern, clean syntax** for working with Promises. Makes async code look synchronous.

```js
async function fetchData() {
  try {
    let response = await fetch('https://api.example.com/data');
    let data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  }
}
```

### Key Rules
- `async` function **always returns a Promise**
- `await` **pauses execution** until Promise resolves
- `await` can **only be used inside** `async` functions
- Use `try...catch` for error handling

### Execution Order
```js
console.log(1);           // 1st
await someAsyncCall();    // pauses here
console.log(2);           // resumes after await
```

---

## 23. Fetch API & AJAX

### Fetch API
Modern replacement for XMLHttpRequest. Returns a Promise.

```js
// With .then()
fetch("data.json")
  .then(response => response.json())
  .then(data => console.log(data));

// With async/await (recommended)
async function loadData() {
  let response = await fetch("data.json");
  let data = await response.json();
  console.log(data);
}
```

> ⚠️ `fetch()` returns a **Response object**, not data directly. Call `.json()` to extract JSON.

### AJAX (Asynchronous JavaScript and XML)
- Uses `XMLHttpRequest` (older) or Fetch API (modern)
- Updates web pages **without full reload**
- Works with APIs and servers

**AJAX Workflow:**
1. Event occurs (page load, button click)
2. XMLHttpRequest / fetch sends request to server
3. Server processes and responds
4. JS reads response and updates the page

---

## 24. Event Loop & Concurrency Model

### How JavaScript Handles Async

JS is **single-threaded** but uses an **event loop** for concurrency.

**Components:**
- **Call Stack** — executes code synchronously
- **Web APIs** — handle async tasks (timers, HTTP, DOM events)
- **Task Queue (Callback Queue)** — holds callbacks ready to execute
- **Microtask Queue** — holds Promise callbacks (higher priority)
- **Event Loop** — moves tasks from queue to call stack when stack is empty

### Event Loop Phases (Node.js)
1. **Timers** — `setTimeout`, `setInterval`
2. **I/O Callbacks** — file/network operations
3. **Poll** — retrieve new I/O events
4. **Check** — `setImmediate`
5. **Close Callbacks** — close events
6. **Microtasks** — processed between every phase

### Example
```js
console.log('Start');         // 1st
setTimeout(() => {
  console.log('Timeout');     // 3rd (after 2s delay)
}, 2000);
console.log('End');           // 2nd

// Output: Start → End → Timeout
```

---

## 25. Introduction to Git

**Git** = Version Control System (VCS) to track changes and collaborate.

### Core Concepts

| Concept | Description |
|---------|-------------|
| **Repository** | Folder where Git tracks all changes |
| **Commit** | Snapshot of project at a point in time (has unique hash) |
| **Staging Area** | Where you prepare changes before committing |
| **Branch** | Independent line of development |
| **Remote** | Hosted version (GitHub, GitLab, Bitbucket) |

### Standard Git Workflow
```bash
git init                          # Initialize repo
git add .                         # Stage all changes
git commit -m "Add login logic"   # Commit with message
git push origin main              # Push to remote
```

---

## 📝 Quick Revision Cheat Sheet

### Variable Declaration
```
var   → function-scoped, hoisted (as undefined), reassignable
let   → block-scoped, TDZ, reassignable
const → block-scoped, TDZ, NOT reassignable
```

### Function Types
```
function fn() {}          → Declaration (hoisted)
const fn = function() {}  → Expression (NOT hoisted)
const fn = () => {}       → Arrow (NOT hoisted, no own `this`)
```

### Equality
```
==   → loose (type coercion)     '5' == 5  → true
===  → strict (no coercion)      '5' === 5 → false
```

### Array Method Quick-Pick
```
Transform  → map()
Filter     → filter()
Reduce     → reduce()
Search     → find() / findIndex()
Check      → some() / every()
Loop       → forEach()
```

### Async Patterns (Evolution)
```
Callbacks → Promises (.then/.catch) → async/await
```

### Storage Comparison
```
localStorage    → Permanent, ~5-10MB, no server
sessionStorage  → Tab session, ~5MB, no server
cookies         → Expiry-based, ~4KB, sent to server
```

---

> **End of Summary** — Good luck with your FEE exam! 🚀
