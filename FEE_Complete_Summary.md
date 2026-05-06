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

| Method | Description |
|--------|-------------|
| `innerHTML` | Write HTML into an element |
| `innerText` | Write plain text into an element |
| `document.write()` | Write to HTML output (⚠️ overwrites page if used after load) |
| `window.alert()` | Display alert box |
| `console.log()` | Write to browser console (debugging) |
| `window.print()` | Print current window content |

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
Number('5')   // 5
String(10)    // '10'
Boolean(1)    // true
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
- `bind()` creates a new function with a fixed `this` context

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

---

## 12. Arrays & Array Methods

An **array** is an ordered collection of values (any type), indexed from `0`.

```js
let arr = [10, 20, 30, 40, 50];
```

### Key Array Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `map(fn)` | Transform each element | New array |
| `filter(fn)` | Keep elements passing condition | New array |
| `reduce(fn, init)` | Accumulate to single value | Single value |
| `forEach(fn)` | Run function per element | `undefined` |
| `some(fn)` | Any element passes? | `true`/`false` |
| `every(fn)` | All elements pass? | `true`/`false` |
| `find(fn)` | First matching element | Value or `undefined` |
| `findIndex(fn)` | Index of first match | Index or `-1` |

```js
let nums = [1, 2, 3, 4, 5];

nums.map(x => x * 2);        // [2, 4, 6, 8, 10]
nums.filter(x => x > 3);     // [4, 5]
nums.reduce((s, x) => s + x, 0); // 15
nums.some(x => x > 4);       // true
nums.every(x => x > 0);      // true
nums.find(x => x === 3);     // 3
nums.findIndex(x => x === 3); // 2
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

---

## 14. Destructuring

### Array Destructuring
```js
let [a, b, c] = [10, 20, 30];
// a=10, b=20, c=30

// Skip elements
let [x, , z] = [1, 2, 3];  // x=1, z=3

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

| Method | Purpose | Example |
|--------|---------|---------|
| `JSON.stringify(obj)` | Object → JSON string | `'{"name":"John","age":30}'` |
| `JSON.parse(str)` | JSON string → Object | `{ name: "John", age: 30 }` |

---

## 16. DOM Manipulation

### What is the DOM?
**Document Object Model** — represents HTML as a **tree structure**. Each HTML element is a **node**. JS uses DOM to access, modify, add, or remove elements.

### Selecting Elements

| Method | Returns |
|--------|---------|
| `getElementById("id")` | Single element |
| `querySelector("CSS selector")` | First matching element |
| `querySelectorAll("CSS selector")` | NodeList (all matches) |

```js
const box = document.getElementById("box");
const btn = document.querySelector(".btn");
const items = document.querySelectorAll("li");
items.forEach(item => console.log(item));
```

### Reading & Writing Content
```js
element.textContent            // Read plain text
element.innerHTML              // Read HTML content
element.textContent = "Hello"; // Write text
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
const div = document.createElement("div");
div.textContent = "New Element";

// Append
document.body.appendChild(div);

// Delete
element.remove();
// OR
parent.removeChild(child);
```

---

## 17. Event Handling & Propagation

### addEventListener()
```js
element.addEventListener("event", handlerFunction);

btn.addEventListener("click", function() {
  alert("Clicked!");
});
```

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
```

### Pop-up Windows
```js
window.open("https://example.com");
window.close();
```

### Timers

| Method | Behavior |
|--------|----------|
| `setTimeout(fn, ms)` | Run **once** after delay |
| `setInterval(fn, ms)` | Run **repeatedly** at interval |
| `clearInterval(id)` | Stop interval |

```js
setTimeout(() => console.log("Hello"), 2000);  // After 2s

let id = setInterval(() => console.log("Tick"), 1000);
clearInterval(id);  // Stop it
```

---

## 19. Web Storage & Cookies

### LocalStorage (Permanent)
- Data persists even after browser closes
- Shared across tabs (same origin)

```js
localStorage.setItem("key", "value");
localStorage.getItem("key");
localStorage.removeItem("key");
localStorage.clear();
```

### SessionStorage (Temporary)
- Data deleted when tab is closed
- NOT shared across tabs

```js
sessionStorage.setItem("user", "Admin");
sessionStorage.getItem("user");
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
