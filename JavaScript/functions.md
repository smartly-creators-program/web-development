# JavaScript Functions

## Introduction
A **function** in **JavaScript** is a **reusable block of code** that performs a **specific task**.  
Functions help **reduce code repetition** and make programs **easier to read and maintain**.  
They allow you to **write code once** and **use it multiple times** with **different inputs**, making programs more **organized**, **efficient**, and **easier to manage**.


## Why Use Functions?
- Avoid repeating code
- Improve readability
- Make code reusable
- Easy to debug and maintain

## Function Syntax
```js
function functionName() {
  // code to execute
}
```
## Simple Function Example

A simple function is a block of code that runs when it is called.

```js
function greet() {
  console.log("Hello, Welcome to JavaScript!");
}

greet();

// Output:
// Hello, Welcome to JavaScript!
```
**Explanation:**
- `greet` is a function that prints a message
- The code inside runs when `greet()` is called
- The message is displayed in the console

## Function with Parameters

Parameters are values that allow a function to receive input and work with different data.

```js
function greetUser(name) {
  console.log("Hello " + name);
}

greetUser("Sindhuja");

// Output:
// Hello Sindhuja
```
**Explanation:**
- `name` is a parameter that receives input
- `"Sindhuja"` is passed as an argument to the function
- The function prints a personalized message

## Function with Multiple Parameters

A function can accept more than one parameter to work with multiple values.

```js
function add(a, b) {
  console.log(a + b);
}

add(5, 3);

// Output:
// 8
```
**Explanation:**
- `a` and `b` are parameters used as inputs
- `5` and `3` are passed as arguments
- The function adds the values and prints the result

## Function with Return Statement

The `return` statement sends a value back to where the function is called.  
It allows the result of a function to be stored or used later.

```js
function multiply(a, b) {
  return a * b;
}

let result = multiply(4, 5);
console.log(result);

// Output:
// 20
```
**Explanation:**
- `a` and `b` are parameters used in the calculation
- `return` sends the result back from the function
- The returned value is stored in `result` and printed

## Function Expression

A function can be stored inside a variable.  
This is called a **function expression**.

```js
const greet = function () {
  console.log("Hello from function expression");
};

greet();

// Output:
// Hello from function expression
```
**Explanation:**
- The function has no name (anonymous function)
- It is stored in the variable `greet`
- The function runs when `greet()` is called

## Arrow Function (ES6)

Arrow functions provide a shorter and cleaner syntax compared to normal functions.

```js
const greet = () => {
  console.log("Hello from arrow function");
};

greet();

// Output:
// Hello from arrow function
```
**Explanation:**
- `=>` is called the arrow
- Arrow functions are shorter than normal functions
- Commonly used in modern JavaScript
## Arrow Function with Parameters

Arrow functions can accept parameters and return values.

```js
const add = (a, b) => a + b;

console.log(add(10, 20));

// Output:
// 30
```
**Explanation:**
- `a` and `b` are parameters
- The result is returned automatically
- Used for simple one-line logic
## Default Parameters

Default parameters are used when no argument is passed to a function.

```js
function greet(name = "Guest") {
  console.log("Hello " + name);
}

greet();
greet("Sindhuja");

// Output:
// Hello Guest
// Hello Sindhuja
```
**Explanation:**
- `"Guest"` is the default value
- Used when no argument is provided
- Helps avoid `undefined`
``
## Function Calling Another Function

A function can call another function inside it to reuse code.

```js
function square(num) {
  return num * num;
}

function printSquare(value) {
  console.log(square(value));
}

printSquare(5);

// Output:
// 25
```
**Explanation:**
- `square()` calculates the value
- `printSquare()` uses `square()`
- Improves code reusability

## Common Mistakes

### 1. Forgetting to Call the Function

```js
function test() {
  console.log("Hello");
}

test;   // ❌ function not executed
test(); // ✅ correct
```
**Explanation:**
- Writing test only refers to the function
- test() actually calls and executes the function
 ### 2. Missing `return` Statement

```js
function add(a, b) {
  a + b;
}

console.log(add(2, 3));

// Output:
// undefined
```
**Explanation:**
- The function does not return any value
- Without return, JavaScript returns undefined
### 3. Using Function Before Declaration (Function Expression)

```js
sayHello(); // ❌ error

const sayHello = function () {
  console.log("Hello");
};
```
**Explanation:**
- Function expressions are not hoisted
- The function cannot be used before it is defined
## Interview Questions

### 1. What is a function in JavaScript?
A function is a reusable block of code that performs a specific task.


### 2. What is the difference between parameters and arguments?
- Parameters are variables defined in the function
- Arguments are values passed to the function when calling it

### 3. What is the purpose of the `return` statement?
The `return` statement sends a value back from the function and stops its execution.


### 4. What is a function expression?
A function expression is a function stored inside a variable.


### 5. What is the difference between a normal function and an arrow function?
Arrow functions have a shorter syntax and do not have their own `this`.


### 6. What happens if a function does not return anything?
If a function does not return a value, it returns `undefined` by default.

## Conclusion

Functions are one of the most important concepts in JavaScript as they help organize code into reusable and manageable blocks. By using functions, we can avoid repetition, improve readability, and make programs easier to maintain. Parameters allow functions to accept input, while the `return` statement sends results back for further use. Arrow functions provide a shorter and cleaner syntax in modern JavaScript. Understanding functions is essential for writing efficient, clean, and professional JavaScript code.