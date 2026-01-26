# JavaScript: Lexical Scoping & Closures
## 1. Lexical Scoping

Lexical Scope refers to how the JavaScript engine determines the accessibility of variables based on their physical location within the source code.

### The Core Concept
- **Static Determination**  
  Scope is decided at code writing time, not at runtime.

- **Outward Chain**  
  A function can access variables defined in its own scope and any parent scopes, but parent scopes cannot look inward.


Example: Nested Functions

```javascript
function outer() { 
    let username = "hitesh"; 
 
    function inner() { 
        let secret = "my123"; 
        console.log("inner:", username); //  Works (Accesses parent scope)
    } 
 
    function innerTwo() { 
        console.log("innerTwo:", username); //  Works
        console.log(secret); //  ReferenceError (secret is inside inner())
    } 
 
    inner(); 
    innerTwo(); 
} 
outer();
```

### Key Scoping Rules
- **Top-Down Access**: Inner functions have access to outer variables.
- **No Inward Access**: Outer functions cannot access variables defined inside inner functions.
- **Sibling Isolation**: Sibling functions (functions defined at the same level) cannot access each other’s local variables.


## 2. Closures

A Closure is a function that "remembers" its lexical environment even after the outer function has finished executing.

### The Anatomy of a Closure

```javascript
function makeFunc() { 
    const name = "Mozilla"; 
    function displayName() { 
        console.log(name); 
    } 
    return displayName; 
} 

const myFunc = makeFunc(); 
myFunc(); // Still logs "Mozilla"
```

### Why does this happen?

When makeFunc is executed, it returns the displayName function. Normally, local variables like name would be removed from memory once the function finishes. However, because displayName closes over the variable name, JavaScript keeps that specific part of the memory alive.

## 3. Real-World Application: Event Handlers

Closures are powerful for creating reusable logic without repeating code.

The Problem (Redundant Code)
```javascript
document.getElementById("orange").onclick = function() { 
    document.body.style.backgroundColor = "orange"; 
}; // This is repetitive if you have 10 colors.
```

The Solution (Closure-Based)
```javascript
function clickHandler(color) { 
    return function() { 
        document.body.style.backgroundColor = `${color}`; 
    }; 
} 
// clickHandler executes immediately and RETURNS a function
// The returned function "remembers" the specific color passed to it.
document.getElementById("orange").onclick = clickHandler("orange"); 
document.getElementById("green").onclick = clickHandler("green");
```

## 4. Comparison & Interview Guide
### Lexical Scope vs. Closure

#### Lexical Scope

Variable access determined by where the function is defined in the source code.

#### Closure

A function bundled together with references to its surrounding state (lexical environment).

## Interview Trap: Is every nested function a closure?

Answer:
No. Technically, all functions are closures in JS, but in an interview context, it is only a "Closure" if a function is returned (or passed) and continues to access its outer scope after that outer scope has closed.
