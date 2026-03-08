# HTML Forms — A Complete Beginner's Guide

## What is an HTML Form?

An HTML form is a section of a webpage that collects **user input** and sends it to a server or processes it on the client side.

Forms are everywhere on the web — login pages, search bars, contact forms, registration pages, and checkout flows all rely on HTML forms.

---

## Basic Structure of a Form

```html
<form action="/submit" method="POST">
  <!-- form elements go here -->
</form>
```

### Key Attributes

| Attribute | Description |
|-----------|-------------|
| `action`  | The URL where the form data is sent |
| `method`  | How the data is sent — `GET` or `POST` |

- **GET** — Appends data to the URL (e.g., for search queries). Data is visible in the URL.
- **POST** — Sends data in the request body. More secure for sensitive information.

---

## Common Form Elements

### 1. Text Input

```html
<label for="username">Username:</label>
<input type="text" id="username" name="username" placeholder="Enter your name">
```

The `<label>` element is linked to the input via the `for` attribute (matching the input's `id`). This improves accessibility and usability.

---

### 2. Password Input

```html
<label for="password">Password:</label>
<input type="password" id="password" name="password">
```

Characters are hidden automatically.

---

### 3. Email Input

```html
<label for="email">Email:</label>
<input type="email" id="email" name="email" placeholder="you@example.com">
```

Browsers automatically validate that the input looks like a valid email address.

---

### 4. Textarea (Multi-line Text)

```html
<label for="message">Message:</label>
<textarea id="message" name="message" rows="5" cols="40" placeholder="Write something..."></textarea>
```

Use `<textarea>` when users need to write longer content.

---

### 5. Checkbox

```html
<input type="checkbox" id="terms" name="terms" value="agreed">
<label for="terms">I agree to the Terms & Conditions</label>
```

Checkboxes let users select one or more options independently.

---

### 6. Radio Buttons

```html
<p>Choose your skill level:</p>
<input type="radio" id="beginner" name="level" value="beginner">
<label for="beginner">Beginner</label>

<input type="radio" id="intermediate" name="level" value="intermediate">
<label for="intermediate">Intermediate</label>

<input type="radio" id="advanced" name="level" value="advanced">
<label for="advanced">Advanced</label>
```

Radio buttons with the **same `name`** form a group — only one can be selected at a time.

---

### 7. Dropdown (Select)

```html
<label for="country">Country:</label>
<select id="country" name="country">
  <option value="">-- Select --</option>
  <option value="in">India</option>
  <option value="us">United States</option>
  <option value="uk">United Kingdom</option>
</select>
```

---

### 8. File Upload

```html
<label for="resume">Upload Resume:</label>
<input type="file" id="resume" name="resume" accept=".pdf,.doc">
```

The `accept` attribute restricts which file types can be selected.

---

### 9. Submit Button

```html
<button type="submit">Submit</button>
```

Or using an input:

```html
<input type="submit" value="Submit">
```

---

## A Complete Example Form

```html
<form action="/register" method="POST">

  <label for="fullname">Full Name:</label>
  <input type="text" id="fullname" name="fullname" placeholder="John Doe" required>

  <label for="email">Email:</label>
  <input type="email" id="email" name="email" placeholder="john@example.com" required>

  <label for="password">Password:</label>
  <input type="password" id="password" name="password" required>

  <label for="gender">Gender:</label>
  <select id="gender" name="gender">
    <option value="">-- Select --</option>
    <option value="male">Male</option>
    <option value="female">Female</option>
    <option value="other">Other</option>
  </select>

  <input type="checkbox" id="terms" name="terms" required>
  <label for="terms">I agree to the Terms & Conditions</label>

  <button type="submit">Register</button>

</form>
```

---

## Form Validation

HTML5 provides built-in validation attributes — no JavaScript needed for basic checks.

| Attribute     | Description                                      |
|---------------|--------------------------------------------------|
| `required`    | Field must not be empty                          |
| `minlength`   | Minimum number of characters                     |
| `maxlength`   | Maximum number of characters                     |
| `min` / `max` | Minimum/maximum value for number or date inputs  |
| `pattern`     | Validates against a regular expression           |
| `type`        | Validates format (e.g., `email`, `url`, `number`)|

**Example:**

```html
<input type="text" name="username" minlength="3" maxlength="15" required>
<input type="number" name="age" min="18" max="99">
```

---

## Important Tips

- Always use `<label>` elements with inputs — it improves accessibility for screen readers and makes clicking the label focus the input.
- Use `POST` for sensitive data like passwords; never `GET`.
- Use `required` and appropriate `type` values for basic validation before relying on JavaScript or server-side checks.
- Group related fields using `<fieldset>` and describe the group with `<legend>`:

```html
<fieldset>
  <legend>Contact Information</legend>
  <label for="phone">Phone:</label>
  <input type="tel" id="phone" name="phone">
</fieldset>
```

---

## Summary

| Element        | Purpose                        |
|----------------|--------------------------------|
| `<form>`       | Container for all form elements|
| `<input>`      | Accepts various types of input |
| `<textarea>`   | Multi-line text input          |
| `<select>`     | Dropdown menu                  |
| `<label>`      | Describes an input field       |
| `<button>`     | Triggers form submission       |
| `<fieldset>`   | Groups related fields          |

HTML Forms are the foundation of user interaction on the web. Mastering them is an essential step toward building dynamic, user-friendly websites.

---
