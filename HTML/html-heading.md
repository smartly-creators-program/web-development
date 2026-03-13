# HTML Headings & Text Formatting — A Complete Beginner's Guide

## What is Text Formatting in HTML?

Text formatting in HTML means structuring and styling text content using specific HTML tags. It helps make content **readable**, **meaningful**, and **well-organized** for both users and search engines.

---

## HTML Headings

Headings define the **hierarchy and structure** of your content. HTML provides 6 levels of headings — from `<h1>` (most important) to `<h6>` (least important).

```html
<h1>This is Heading 1</h1>
<h2>This is Heading 2</h2>
<h3>This is Heading 3</h3>
<h4>This is Heading 4</h4>
<h5>This is Heading 5</h5>
<h6>This is Heading 6</h6>
```

### Visual Hierarchy

| Tag | Use Case |
|-----|----------|
| `<h1>` | Page title — use **only once** per page |
| `<h2>` | Major section headings |
| `<h3>` | Sub-sections under `<h2>` |
| `<h4>` | Sub-sections under `<h3>` |
| `<h5>` | Rarely used — minor sub-sections |
| `<h6>` | Rarely used — smallest heading |

### Why Headings Matter
- Help search engines (SEO) understand your page structure
- Improve accessibility for screen readers
- Make content easier to scan for readers

> ⚠️ **Important:** Never skip heading levels (e.g., don't jump from `<h1>` to `<h4>`). Always follow the hierarchy.

---

## HTML Text Formatting Tags

### 1. Bold Text

```html
<b>This text is bold</b>
<strong>This text is strongly important</strong>
```

| Tag | Meaning |
|-----|---------|
| `<b>` | Visually bold — no special importance |
| `<strong>` | Bold + semantically important (preferred) |

---

### 2. Italic Text

```html
<i>This text is italic</i>
<em>This text is emphasized</em>
```

| Tag | Meaning |
|-----|---------|
| `<i>` | Visually italic — no special importance |
| `<em>` | Italic + semantically emphasized (preferred) |

---

### 3. Underline Text

```html
<u>This text is underlined</u>
```

> ⚠️ Avoid overusing `<u>` — underlined text is often mistaken for a hyperlink.

---

### 4. Strikethrough Text

```html
<s>This text is struck through</s>
<del>This text was deleted</del>
```

| Tag | Meaning |
|-----|---------|
| `<s>` | Text that is no longer relevant |
| `<del>` | Text that was explicitly deleted (semantic) |

**Example use case:**

```html
<p>Original price: <del>₹999</del> Now: ₹499</p>
```

---

### 5. Highlighted Text

```html
<mark>This text is highlighted</mark>
```

Renders with a yellow background by default. Useful for search results or important notes.

---

### 6. Superscript & Subscript

```html
<!-- Superscript -->
<p>E = mc<sup>2</sup></p>

<!-- Subscript -->
<p>H<sub>2</sub>O</p>
```

| Tag | Use Case |
|-----|----------|
| `<sup>` | Exponents, footnotes, ordinal numbers (1st, 2nd) |
| `<sub>` | Chemical formulas, mathematical notation |

---

### 7. Small Text

```html
<small>This is fine print or legal text</small>
```

Used for copyright notices, disclaimers, or side comments.

---

### 8. Inserted Text

```html
<ins>This text was inserted</ins>
```

Usually rendered with an underline. The semantic opposite of `<del>`.

---

### 9. Code & Preformatted Text

```html
<!-- Inline code -->
<p>Use the <code>console.log()</code> function to print output.</p>

<!-- Preformatted block -->
<pre>
  function greet() {
    console.log("Hello, World!");
  }
</pre>
```

| Tag | Use Case |
|-----|----------|
| `<code>` | Inline code snippets |
| `<pre>` | Preserves whitespace and line breaks |

---

### 10. Blockquote & Inline Quote

```html
<!-- Blockquote (long quote) -->
<blockquote cite="https://example.com">
  "Great developers aren't just builders — they're great explainers."
</blockquote>

<!-- Inline quote -->
<p>He said, <q>HTML is the backbone of the web.</q></p>
```

| Tag | Use Case |
|-----|----------|
| `<blockquote>` | Long quotes from external sources |
| `<q>` | Short inline quotes |

---

### 11. Abbreviations

```html
<p><abbr title="HyperText Markup Language">HTML</abbr> is the standard language for web pages.</p>
```

Hovering over the abbreviation shows the full form as a tooltip.

---

### 12. Line Break & Horizontal Rule

```html
<!-- Line break -->
<p>Line one<br>Line two</p>

<!-- Horizontal rule (divider) -->
<hr>
```

| Tag | Use Case |
|-----|----------|
| `<br>` | Breaks to a new line within the same paragraph |
| `<hr>` | Creates a visible horizontal dividing line |

---

## A Complete Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Text Formatting Demo</title>
</head>
<body>

  <h1>Web Development Guide</h1>

  <h2>Introduction</h2>
  <p>
    <strong>HTML</strong> stands for <em>HyperText Markup Language</em>.
    It is the <mark>backbone of every webpage</mark> on the internet.
  </p>

  <h2>Fun Facts</h2>
  <p>Water is written as H<sub>2</sub>O and Einstein's formula is E=mc<sup>2</sup>.</p>

  <h2>Pricing</h2>
  <p>Old price: <del>₹1999</del> &nbsp; New price: <strong>₹999</strong></p>

  <h2>Code Example</h2>
  <p>To print in JavaScript, use <code>console.log("Hello")</code>.</p>

  <pre>
    function greet(name) {
      return "Hello, " + name;
    }
  </pre>

  <h2>Quote</h2>
  <blockquote>
    "The best way to learn is to teach."
  </blockquote>

  <hr>
  <small>© 2024 Web Development Knowledge Hub</small>

</body>
</html>
```

---

## Quick Reference Table

| Tag | Purpose | Example Output |
|-----|---------|---------------|
| `<h1>`–`<h6>` | Headings | **Big → Small titles** |
| `<b>` / `<strong>` | Bold text | **Bold** |
| `<i>` / `<em>` | Italic text | *Italic* |
| `<u>` | Underline | <u>Underlined</u> |
| `<s>` / `<del>` | Strikethrough | ~~Strikethrough~~ |
| `<mark>` | Highlight | `Highlighted` |
| `<sup>` | Superscript | x² |
| `<sub>` | Subscript | H₂O |
| `<small>` | Small text | fine print |
| `<code>` | Inline code | `code snippet` |
| `<pre>` | Preformatted block | Preserves spacing |
| `<blockquote>` | Long quote | Indented quote |
| `<q>` | Inline quote | "quote" |
| `<abbr>` | Abbreviation tooltip | HTML |
| `<br>` | Line break | New line |
| `<hr>` | Horizontal rule | Divider line |

---

## Key Takeaways

- Always use **semantic tags** (`<strong>`, `<em>`) over purely visual ones (`<b>`, `<i>`) — they carry meaning for browsers and screen readers.
- Use **only one `<h1>`** per page for proper SEO.
- Follow heading hierarchy — never skip levels.
- Use `<code>` and `<pre>` for any technical content or code snippets.

---
