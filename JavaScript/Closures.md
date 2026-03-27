# Closures in JavaScript

---

## 📖 Table of Contents

1. [What is a Closure?](#what-is-a-closure)
2. [How Closures Work](#how-closures-work)
3. [Real-World Analogies](#real-world-analogies)
4. [Practical Examples](#practical-examples)
5. [Common Use Cases](#common-use-cases)
6. [Common Mistakes](#common-mistakes)
7. [Quick Summary](#quick-summary)

---

## 🔒 What is a Closure?

A **closure** is a function that **remembers the variables from its outer scope** even after that outer function has finished running.

In simple terms:
> A closure is a function that carries its own **backpack** 🎒 — it keeps variables from where it was created, even when called somewhere else.

```js
function outer() {
  let message = "Hello!"; // variable in outer scope

  function inner() {
    console.log(message); // inner function "closes over" message
  }

  return inner;
}

const myClosure = outer(); // outer() has finished running
myClosure(); // ✅ Still prints "Hello!" — closure remembered message!
```

Even though `outer()` is done, the `inner` function still has access to `message`. That's a closure!

---

## ⚙️ How Closures Work

To understand closures, you need to know two things:

1. **Functions can be returned** from other functions
2. **Inner functions remember** the scope (variables) of their outer function

When JavaScript creates a function, it also attaches a reference to all the variables in scope at that moment. This bundle — the function + its remembered variables — is the **closure**.

```js
function makeGreeting(name) {
  // 'name' is remembered by the returned function
  return function () {
    console.log("Hi, " + name + "!");
  };
}

const greetAlice = makeGreeting("Alice");
const greetBob = makeGreeting("Bob");

greetAlice(); // Hi, Alice!
greetBob();   // Hi, Bob!
```

Each call to `makeGreeting()` creates a **separate closure** with its own `name` value. They don't interfere with each other.

---

## 🌍 Real-World Analogies

### 🎒 The Backpack Analogy

Think of a closure like a function carrying a **backpack**:

- When a function is created inside another function, it packs the outer variables into its backpack.
- Even when the outer function is gone, the inner function still has its backpack.
- It can reach in and use those variables anytime.

---

### 📬 The Mailbox Analogy

Imagine a post office worker who remembers your address even after you leave:

```js
function postOffice(address) {
  return function (letter) {
    console.log(`Sending "${letter}" to ${address}`);
  };
}

const myMailbox = postOffice("123 Main Street");
myMailbox("Happy Birthday card"); // Sending "Happy Birthday card" to 123 Main Street
myMailbox("Invoice");             // Sending "Invoice" to 123 Main Street
```

`address` is remembered every time you use `myMailbox`, even though `postOffice()` already ran.

---

## 💡 Practical Examples

### 1. Counter Function

A classic closure example — a private counter that can only be changed through specific functions:

```js
function makeCounter() {
  let count = 0; // private variable

  return {
    increment() {
      count++;
      console.log("Count:", count);
    },
    decrement() {
      count--;
      console.log("Count:", count);
    },
    getCount() {
      return count;
    }
  };
}

const counter = makeCounter();
counter.increment(); // Count: 1
counter.increment(); // Count: 2
counter.decrement(); // Count: 1
console.log(counter.getCount()); // 1
console.log(counter.count);      // undefined — count is private! 🔒
```

`count` is **hidden** from the outside world. Only the returned methods can access it. This is called **data privacy**.

---

### 2. Function Factory

Closures let you create **customized functions** from a template:

```js
function multiplier(factor) {
  return function (number) {
    return number * factor;
  };
}

const double = multiplier(2);
const triple = multiplier(3);
const tenTimes = multiplier(10);

console.log(double(5));   // 10
console.log(triple(5));   // 15
console.log(tenTimes(5)); // 50
```

Each function remembers its own `factor` value through a closure.

---

### 3. Remembering User Preferences

```js
function createTheme(color) {
  return function (element) {
    console.log(`Applying ${color} theme to ${element}`);
  };
}

const darkTheme = createTheme("dark");
const lightTheme = createTheme("light");

darkTheme("navbar");   // Applying dark theme to navbar
darkTheme("footer");   // Applying dark theme to footer
lightTheme("sidebar"); // Applying light theme to sidebar
```

---

## 🛠 Common Use Cases

### 1. Data Privacy / Encapsulation

Hide variables from the global scope — only expose what's necessary:

```js
function bankAccount(initialBalance) {
  let balance = initialBalance; // private

  return {
    deposit(amount) {
      balance += amount;
      console.log(`Deposited ₹${amount}. Balance: ₹${balance}`);
    },
    withdraw(amount) {
      if (amount > balance) {
        console.log("Insufficient funds!");
      } else {
        balance -= amount;
        console.log(`Withdrew ₹${amount}. Balance: ₹${balance}`);
      }
    }
  };
}

const myAccount = bankAccount(1000);
myAccount.deposit(500);   // Deposited ₹500. Balance: ₹1500
myAccount.withdraw(200);  // Withdrew ₹200. Balance: ₹1300
console.log(myAccount.balance); // undefined — balance is private 🔒
```

---

### 2. Event Handlers

Closures are used heavily in event listeners to remember context:

```js
function setupButton(buttonName) {
  let clickCount = 0;

  document.getElementById(buttonName).addEventListener("click", function () {
    clickCount++;
    console.log(`${buttonName} clicked ${clickCount} times`);
  });
}

setupButton("submitBtn");
// Each click remembers and updates clickCount for that specific button
```

---

### 3. setTimeout with Closures

```js
function delayedGreeting(name) {
  setTimeout(function () {
    console.log("Hello, " + name + "!"); // name is remembered via closure
  }, 2000);
}

delayedGreeting("Alice"); // After 2 seconds: Hello, Alice!
delayedGreeting("Bob");   // After 2 seconds: Hello, Bob!
```

---

## ⚠️ Common Mistakes

### Mistake 1: Closures in Loops with `var`

This is one of the most famous JS beginner bugs:

```js
// ❌ Wrong — all buttons alert "5"
for (var i = 0; i < 5; i++) {
  setTimeout(function () {
    console.log(i); // always prints 5
  }, 1000);
}
```

**Why?** `var` is function-scoped, so all closures share the **same** `i`. By the time the timeout runs, `i` is already `5`.

```js
// ✅ Fix 1 — use let (block-scoped, each loop gets its own i)
for (let i = 0; i < 5; i++) {
  setTimeout(function () {
    console.log(i); // prints 0, 1, 2, 3, 4 ✅
  }, 1000);
}

// ✅ Fix 2 — use an IIFE (Immediately Invoked Function Expression)
for (var i = 0; i < 5; i++) {
  (function (j) {
    setTimeout(function () {
      console.log(j); // prints 0, 1, 2, 3, 4 ✅
    }, 1000);
  })(i);
}
```

---

### Mistake 2: Thinking the Variable is Copied

Closures remember the **reference** to a variable, not a snapshot of its value:

```js
function makeAdder() {
  let x = 10;

  function add(y) {
    return x + y; // x is a reference, not a copy
  }

  x = 20; // changing x AFTER defining add
  return add;
}

const adder = makeAdder();
console.log(adder(5)); // 25, NOT 15 — closure sees the latest value of x
```

---

### Mistake 3: Memory Leaks

Closures keep variables alive in memory. Be careful not to create unnecessary closures in performance-critical code:

```js
// ❌ Potential memory issue — largeData stays in memory
function processData() {
  const largeData = new Array(1000000).fill("data");

  return function () {
    console.log(largeData.length); // largeData can't be garbage collected
  };
}
```

Only use closures when you truly need the variable to persist.

---

## ✅ Quick Summary

| Concept | Explanation |
|---|---|
| **Closure** | A function that remembers variables from its outer scope |
| **Lexical Scope** | The scope defined at the time of function creation |
| **Data Privacy** | Using closures to hide variables from outside access |
| **Function Factory** | Using closures to generate customized functions |
| **Shared Reference** | Closures remember the reference, not a copy of the value |
| **`var` in loops** | Dangerous — use `let` instead to avoid shared closure bugs |

---

## 🧠 Key Takeaways

- A closure is created every time a function is created inside another function.
- The inner function **remembers** the outer function's variables even after it's done.
- Closures are used for **data privacy**, **function factories**, and **event handling**.
- Always use `let` or `const` in loops to avoid closure-related bugs.
- Closures keep variables alive in memory — use them wisely.

---

