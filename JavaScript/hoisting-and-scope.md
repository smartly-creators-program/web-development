# Hoisting & Scope in JavaScript

---

## 📖 Table of Contents

1. [What is Scope?](#what-is-scope)
2. [Types of Scope](#types-of-scope)
3. [What is Hoisting?](#what-is-hoisting)
4. [Hoisting with Variables](#hoisting-with-variables)
5. [Hoisting with Functions](#hoisting-with-functions)
6. [Common Mistakes & How to Avoid Them](#common-mistakes--how-to-avoid-them)
7. [Quick Summary](#quick-summary)

---

## 🔭 What is Scope?

**Scope** determines **where** a variable is accessible (visible) in your code.

Think of it like rooms in a house:
- A variable declared in the **living room** can be accessed by everyone in the house.
- A variable declared inside a **bedroom** can only be used inside that bedroom.

```js
let house = "I'm accessible everywhere"; // outside any block

function bedroom() {
  let secret = "Only I can see this"; // inside a function
  console.log(house);   // ✅ works — can access outer variable
  console.log(secret);  // ✅ works — inside its own scope
}

console.log(house);   // ✅ works
console.log(secret);  // ❌ ReferenceError: secret is not defined
```

---

## 🗂 Types of Scope

### 1. Global Scope

A variable declared **outside all functions and blocks** lives in the global scope. It can be accessed from anywhere in the code.

```js
let language = "JavaScript";

function greet() {
  console.log("I love " + language); // ✅ accessible here
}

greet(); // Output: I love JavaScript
```

---

### 2. Function Scope

Variables declared **inside a function** using `var`, `let`, or `const` are only accessible within that function.

```js
function sayHello() {
  let message = "Hello, World!";
  console.log(message); // ✅ works
}

sayHello();
console.log(message); // ❌ ReferenceError: message is not defined
```

---

### 3. Block Scope

A **block** is any code wrapped in `{}` — like an `if` statement, a `for` loop, etc.

`let` and `const` are **block-scoped**, meaning they only exist inside the `{}` they were declared in.

```js
if (true) {
  let blockVar = "I'm block-scoped";
  const alsoBlock = "Me too!";
  console.log(blockVar); // ✅ works
}

console.log(blockVar); // ❌ ReferenceError
```

> ⚠️ `var` does **not** respect block scope — it leaks out of `{}` (except functions).

```js
if (true) {
  var leaked = "I escape blocks!";
}

console.log(leaked); // ✅ "I escape blocks!" — var ignores block scope
```

---

### 4. Lexical Scope (Scope Chain)

JavaScript looks for variables **outward** from the current scope, not inward. An inner function can access variables from its outer function.

```js
function outer() {
  let outerVar = "I'm from outer";

  function inner() {
    console.log(outerVar); // ✅ inner can access outer's variables
  }

  inner();
}

outer();
```

This lookup chain is called the **scope chain**.

---

## 🚀 What is Hoisting?

**Hoisting** is JavaScript's default behavior of moving declarations to the **top of their scope** before code runs.

This happens automatically — you don't do anything special. The JavaScript engine reads your file in two passes:
1. **First pass:** Scans for all declarations and registers them.
2. **Second pass:** Executes the code line by line.

> 💡 Only **declarations** are hoisted — not initializations (assignments).

---

## 📦 Hoisting with Variables

### `var` — Hoisted, but initialized as `undefined`

```js
console.log(name); // undefined (not an error!)
var name = "Alice";
console.log(name); // "Alice"
```

Behind the scenes, JavaScript reads it as:

```js
var name;            // declaration hoisted to top
console.log(name);   // undefined
name = "Alice";      // assignment stays in place
console.log(name);   // "Alice"
```

---

### `let` and `const` — Hoisted, but NOT initialized (Temporal Dead Zone)

`let` and `const` are hoisted but placed in a **Temporal Dead Zone (TDZ)** — you cannot access them before their declaration line.

```js
console.log(age); // ❌ ReferenceError: Cannot access 'age' before initialization
let age = 25;
```

This is actually **safer** behavior — it prevents you from accidentally using a variable before it's set.

---

### Quick Comparison Table

| Keyword | Hoisted? | Initialized? | Scope |
|---------|----------|--------------|-------|
| `var`   | ✅ Yes   | `undefined`  | Function |
| `let`   | ✅ Yes   | ❌ TDZ       | Block |
| `const` | ✅ Yes   | ❌ TDZ       | Block |

---

## ⚙️ Hoisting with Functions

### Function Declarations — Fully Hoisted ✅

Function declarations are hoisted **completely** — both the name and the body.

```js
greet(); // ✅ Works! Output: "Hello!"

function greet() {
  console.log("Hello!");
}
```

You can call the function **before** it's defined in the file.

---

### Function Expressions — NOT Fully Hoisted ❌

If you assign a function to a variable, only the variable is hoisted (as `undefined`), not the function body.

```js
sayBye(); // ❌ TypeError: sayBye is not a function

var sayBye = function() {
  console.log("Bye!");
};
```

---

### Arrow Functions — NOT Hoisted ❌

Arrow functions behave the same as function expressions.

```js
hello(); // ❌ TypeError

const hello = () => {
  console.log("Hey there!");
};
```

---

## ⚠️ Common Mistakes & How to Avoid Them

### Mistake 1: Relying on `var` hoisting

```js
// ❌ Confusing
console.log(score); // undefined — no error, but misleading
var score = 100;

// ✅ Better — use let/const, declare before use
let score = 100;
console.log(score); // 100
```

**Fix:** Always declare your variables at the **top** of their scope. Prefer `let` and `const` over `var`.

---

### Mistake 2: Variable leaking from blocks with `var`

```js
// ❌ Unexpected behavior
for (var i = 0; i < 3; i++) {}
console.log(i); // 3 — i leaked out of the loop!

// ✅ Use let
for (let j = 0; j < 3; j++) {}
console.log(j); // ❌ ReferenceError — j stays in the loop
```

---

### Mistake 3: Calling a function expression before defining it

```js
// ❌ This will break
const result = add(2, 3);

const add = (a, b) => a + b;

// ✅ Define first, then call
const add = (a, b) => a + b;
const result = add(2, 3); // 5
```

---

## ✅ Quick Summary

| Concept | What it means |
|---|---|
| **Scope** | Where a variable can be accessed |
| **Global Scope** | Accessible everywhere |
| **Function Scope** | Accessible only inside a function |
| **Block Scope** | Accessible only inside `{}` (`let` / `const`) |
| **Scope Chain** | JS looks outward to find variables |
| **Hoisting** | Declarations are moved to top before execution |
| **`var` hoisting** | Hoisted and initialized as `undefined` |
| **`let`/`const` hoisting** | Hoisted but in TDZ — can't use before declaration |
| **Function declaration** | Fully hoisted — callable before it appears |
| **Function expression / Arrow** | Not fully hoisted — must define before calling |

---

## 🧠 Key Takeaways

- Always use `let` or `const` — avoid `var` in modern JavaScript.
- Declare variables at the **top** of their scope for clarity.
- Use **function declarations** if you need to call them anywhere in a file.
- Understanding scope and hoisting helps you **avoid bugs** and write **predictable code**.

---
