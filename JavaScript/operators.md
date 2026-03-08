# JavaScript: Operators (Detailed Guide with Examples)

## Introduction

Operators in JavaScript are special symbols used to perform operations on values and variables.  
They help us do calculations, compare values, apply logic, and control program flow.

**Example:**
```javascript
let sum = 10 + 5;
```
Here, + is an operator and 10, 5 are operands.
## Types of Operators
## 1. Arithmetic Operators

Arithmetic operators are used to perform mathematical calculations on numbers.

### Operators

- **Addition (`+`)**  
  Adds two values

- **Subtraction (`-`)**  
  Subtracts one value from another

- **Multiplication (`*`)**  
  Multiplies two values

- **Division (`/`)**  
  Divides one value by another

- **Modulus (`%`)**  
  Returns the remainder of a division

- **Exponentiation (`**`)**  
  Raises a number to the power of another number
### Example

```javascript
let a = 10;
let b = 3;

console.log(a + b);  // Addition → 13
console.log(a - b);  // Subtraction → 7
console.log(a * b);  // Multiplication → 30
console.log(a / b);  // Division → 3.33
console.log(a % b);  // Modulus → 1
console.log(a ** b); // Exponentiation → 1000

```
## 2. Assignment Operators

Assignment operators are used to assign values to variables.  
Some assignment operators also perform an operation and then assign the result.

### Operators

- **Assignment (`=`)**  
  Assigns a value to a variable

- **Addition Assignment (`+=`)**  
  Adds a value and assigns the result

- **Subtraction Assignment (`-=`)**  
  Subtracts a value and assigns the result

- **Multiplication Assignment (`*=`)**  
  Multiplies a value and assigns the result

- **Division Assignment (`/=`)**  
  Divides a value and assigns the result

- **Modulus Assignment (`%=`)**  
  Finds remainder and assigns the result

### Example

```javascript
let x = 10;

x = 10;   // Assignment
x += 5;   // x = x + 5 → 15
x -= 3;   // x = x - 3 → 12
x *= 2;   // x = x * 2 → 24
x /= 4;   // x = x / 4 → 6
x %= 4;   // x = x % 4 → 2
```
## 3. Comparison Operators

Comparison operators are used to compare two values.  
They always return a boolean value: `true` or `false`.

### Operators

- **Equal (`==`)**  
  Compares two values after type conversion

- **Strict Equal (`===`)**  
  Compares both value and type without type conversion

- **Not Equal (`!=`)**  
  Checks if two values are not equal (with type conversion)

- **Strict Not Equal (`!==`)**  
  Checks both value and type are not equal

- **Greater Than (`>`)**  
  Checks if the left value is greater than the right value

- **Less Than (`<`)**  
  Checks if the left value is less than the right value

- **Greater Than or Equal (`>=`)**  
  Checks if the left value is greater than or equal to the right value

- **Less Than or Equal (`<=`)**  
  Checks if the left value is less than or equal to the right value


### Example

```javascript
console.log(5 == "5");    // true  → Equal (type conversion)
console.log(5 === "5");   // false → Strict Equal
console.log(10 != "10");  // false → Not Equal
console.log(10 !== "10"); // true  → Strict Not Equal
console.log(10 > 5);      // true  → Greater Than
console.log(10 <= 10);    // true  → Less Than or Equal
```
## 4. Logical Operators

Logical operators are used to combine multiple conditions and return a boolean value.

### Operators

- **Logical AND (`&&`)**  
  Returns `true` if **both** conditions are true

- **Logical OR (`||`)**  
  Returns `true` if **at least one** condition is true

- **Logical NOT (`!`)**  
  Reverses the boolean value of a condition
### Example

```javascript
const age = 20;
const hasID = true;

console.log(age >= 18 && hasID); // true  → AND
console.log(age < 18 || hasID);  // true  → OR
console.log(!hasID);             // false → NOT
```
## 5. Unary Operators

Unary operators operate on a single operand and return a new value.

### Operators

- **Typeof (`typeof`)**  
  Returns the data type of a value

- **Increment (`++`)**  
  Increases a numeric value by `1`

- **Decrement (`--`)**  
  Decreases a numeric value by `1`

- **Logical NOT (`!`)**  
  Converts a value to boolean and reverses it
### Example
```javascript
let count = 5;

count++;
console.log(count);  // 6  → Increment

count--;
console.log(count);  // 5  → Decrement

console.log(typeof count); // number → Typeof
console.log(!true);        // false  → Logical NOT
```
## 6. Ternary Operator  
The ternary operator is a shorthand way to write simple `if-else` conditions in a single line.

### Syntax
```javascript
condition ? valueIfTrue : valueIfFalse
```
### Example
```javascript
const marks = 75;

const result = marks >= 40 ? "Pass" : "Fail";
console.log(result); // Pass

```
## 7. String Operators

String operators are used to combine or manipulate strings.  
In JavaScript, the `+` operator is commonly used to join strings together. This is called **string concatenation**.

### Operator

- **Concatenation (`+`)**  
  Joins two or more strings into a single string


### Example

```javascript
const firstName = "Kalagotla";
const lastName = "Sindhuja";

const fullName = firstName + " " + lastName;
console.log(fullName); // Kalagotla Sindhuja
```
## 8. Operator Precedence

Operator precedence determines the order in which operators are evaluated in an expression.  
Operators with higher precedence are evaluated before operators with lower precedence.

### Example

```javascript
console.log(10 + 5 * 2);    // 20
console.log((10 + 5) * 2); // 30
```
## Interview Questions

### Q1. What is the difference between `==` and `===`?

**Answer:**  
`==` compares values after performing type conversion, while `===` compares both value and type without type conversion.  
Using `===` is safer and avoids unexpected bugs.



### Q2. What is the ternary operator?

**Answer:**  
The ternary operator is a shorthand for `if-else` statements that allows conditional logic to be written in a single line.


### Q3. What is operator precedence?

**Answer:**  
Operator precedence determines the order in which operators are evaluated in an expression. Operators with higher precedence execute before lower-precedence operators.


### Q4. Which operator is used to combine multiple conditions?

**Answer:**  
Logical operators such as `&&` (AND) and `||` (OR) are used to combine multiple conditions.


### Q5. What does the `typeof` operator do?

**Answer:**  
The `typeof` operator returns the data type of a given value, such as `number`, `string`, or `boolean`.


## Common Mistakes with Operators

### 1. Using `==` instead of `===`

```javascript
console.log(5 == "5");  // true
console.log(5 === "5"); // false
```
**Mistake:**  
Using == can cause unexpected results due to type coercion.

**Best Practice:**  
Always prefer === for comparisons.
```javascript
const value = 5;

if (value === 5) {
  console.log("Values are strictly equal");
}

```
### 2. Forgetting Operator Precedence

```javascript
console.log(10 + 5 * 2); // 20
```
**Mistake:**
Assuming that addition is evaluated before multiplication.

**Why this happens:**
In JavaScript, multiplication (*) has higher precedence than addition (+), so 5 * 2 is evaluated first.

**Best Practice:**
Use parentheses to make the order of operations clear and predictable.
```javascript
console.log((10 + 5) * 2); // 30
```
### 3. Using Assignment (`=`) Instead of Comparison (`===`)

```javascript
let x = 5;

if (x = 10) {
  console.log("Runs");
}
```
**Mistake:**  
Accidentally using the assignment operator (`=`) inside a conditional statement.

**Why this is dangerous:**  
The value `10` is assigned to `x`, and since `10` is a truthy value, the condition always executes.

**Best Practice:**  
Always use comparison operators (`===`) when checking conditions.
```javascript
let x = 5;

if (x === 10) {
  console.log("Runs");
}

```
### 4. Modifying Values with Assignment Operators Unintentionally

```javascript
let x = 10;
x += 5; // x becomes 15
```
**Mistake:**  
Forgetting that assignment operators modify the original variable.

**Why this is dangerous:**  
The original value of the variable is changed, which can lead to unexpected behavior later in the code.

**Best Practice:**  
Be mindful that assignment operators (+=, -=, *=, etc.) update the variable directly.
Use them only when you intentionally want to modify the existing value.
```javascript
let x = 10;
let updatedValue = x + 5; // original x remains unchanged

```
##  Conclusion
Operators are essential in JavaScript for performing calculations, making comparisons, and controlling program logic. Understanding different types of operators and common mistakes helps write clear, correct, and reliable code. Mastering operators builds a strong foundation for learning advanced JavaScript concepts.