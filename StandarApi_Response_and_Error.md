# API Response & Error Handling (Beginner Friendly)

## What is a Response?

A **response** is the data that the server sends back to the client (frontend).

**Example:**

- Client asks → "Give user data"
- Server replies → "Here is the data"

That reply is called a **Response**.

---

## Standard Response Format

```js
class ApiResponse {
  constructor(statusCode, data, message = "Success") {
    this.statusCode = statusCode;
    this.data = data;
    this.message = message;
    this.success = statusCode < 400;   // true if success
  }
}
```

Fields explained:

- `statusCode` → tells what happened (200, 404, etc.)
- `data` → actual result (user, products, list, etc.)
- `message` → simple explanation
- `success` → true/false flag (very helpful for frontend)

### How a successful response looks

```json
{
  "statusCode": 200,
  "data": {
    "name": "Mohit"
  },
  "message": "Success",
  "success": true
}
```

## What is an Error?

An **error** happens when something goes wrong.

**Examples:**

- User not found
- Invalid input
- Server crash
- Unauthorized access

## Standard Format of Error

```js
class ApiError extends Error {
  constructor(statusCode, message = "Something went wrong", errors = [], stack = "") {
    super(message);
    this.statusCode = statusCode;
    this.data = null;
    this.message = message;
    this.success = false;
    this.errors = errors;

    if (stack) {
      this.stack = stack;
    } else {
      Error.captureStackTrace(this, this.constructor);
    }
  }
}
```

Fields explained:

- `statusCode` → type of error (400, 401, 404, 500…)
- `message` → what went wrong (human readable)
- `errors` → detailed errors (optional – array)
- `success` = `false` → clearly shows failure
- `stack` → debugging info (for developers – usually in development only)

### Example of Error Response

```json
{
  "statusCode": 404,
  "data": null,
  "message": "User not found",
  "success": false,
  "errors": []
}
```

## Why Should We Standardize Response & Error?

### Without standard format (common bad examples)

```json
{ "msg": "ok" }
```

```json
{ "data": { ... } }
```

```json
{ "error": "something broke" }
```

**Problems:**

- Confusing for frontend developers
- No fixed structure → different handling every time
- Hard to debug
- Inconsistent user experience

### With Standard Format

**Success:**

```json
{
  "statusCode": 200,
  "data": { ... },
  "message": "Success",
  "success": true
}
```

**Error:**

```json
{
  "statusCode": 400,
  "data": null,
  "message": "Invalid input",
  "success": false,
  "errors": [ "email is required", "password too short" ]
}
```

## Benefits

1. **Easy for Frontend**

   ```js
   if (response.success) {
     // show data, success toast, etc.
   } else {
     // show error message, red border, etc.
   }
   ```

2. **Easy Debugging**  
   Always same structure → easy to find issue

3. **Clean & Professional Code**  
   Looks serious — used in real companies & good open-source projects

4. **Reusable Everywhere**

   ```js
   // response.js
   export { ApiResponse };
   export { ApiError };
   ```

