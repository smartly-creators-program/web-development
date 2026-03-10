# 🌐 How a Browser Renders a Webpage

## 📌 Introduction

When you type a website URL into your browser and press **Enter**, the page does not appear instantly.  
Behind the scenes, the browser performs a series of steps to convert **HTML, CSS, and JavaScript** into **pixels on your screen**.

This entire process is known as the **Browser Rendering Process** or the **Critical Rendering Path**.

Understanding this helps you:
- Build faster websites
- Avoid performance issues
- Write better HTML, CSS, and JavaScript

---

## 🧠 High-Level Overview

The browser renders a webpage in the following stages:

URL Entered <br>
↓ <br>
Server Response <br>
↓<br>
HTML → DOM<br>
↓<br>
CSS → CSSOM<br>
↓<br>
Render Tree<br>
↓<br>
Layout (Reflow)<br>
↓<br>
Painting<br>
↓<br>
Compositing<br>
↓<br>
Pixels on Screen<br>


---

## 2️⃣ HTML Parsing → DOM

![DOM Flowchart](./assets/dom%20graph.png)

The browser reads the HTML file line by line...

## 1️⃣ Request & Response

When you enter a URL:

1. The browser checks its **cache** (memory, disk, service worker)
2. If not found, it sends an **HTTP request** to the server
3. The server responds with:
   - HTML
   - CSS
   - JavaScript
   - Images, fonts, etc.

Browser ──HTTP Request──▶ Server<br>
Browser ◀─HTML/CSS/JS──── Server


---

## 2️⃣ HTML Parsing → DOM

The browser reads the HTML file **line by line** and converts it into a **DOM (Document Object Model)**.

### Example HTML

```html
<h1>Hello</h1>
<p>World</p>

```


## DOM Structure (Tree)

Document<br>
 ├── h1<br>
 │    └── "Hello"<br>
 └── p<br>
    &nbsp;&nbsp;  └── "World"<br>

🔹 The DOM represents the structure and content of the webpage.

⚠️ If the browser encounters a **script** tag:

HTML parsing pauses

JavaScript executes first
(unless defer or async is used)

## 3️⃣ CSS Parsing → CSSOM

The browser parses CSS into a CSSOM (CSS Object Model).

Example CSS<br>
p {<br>
  color: red;<br>
}<br>

CSS Rules<br>
 └── p<br>
    &nbsp;&nbsp;   └── color: red<br>

🔹 CSSOM defines how elements should look<br>
⛔ Rendering cannot start until CSSOM is ready<br>
This is why CSS is render-blocking<br>


## 4️⃣ Render Tree Construction

The browser now combines:

- DOM (structure)

- CSSOM (styles)

To create the Render Tree.

DOM + CSSOM<br>
    &nbsp;&nbsp; ↓<br>
Render Tree<br>

### Important Rules

- Only visible elements are included

- display: none → ❌ excluded

- visibility: hidden → ✅ included (but invisible)

### 📌 Render Tree = What needs to be drawn on screen

## 5️⃣ Layout (Reflow)

The browser calculates:

- Element positions

- Width and height

- Spacing and alignment

Render Tree<br>
   &nbsp;&nbsp;  ↓<br>
Layout<br>
(Position & Size Calculation)

### 📏 This step answers:

“Where exactly should each element be placed?”

### ⚠️ Layout is expensive and triggered by:

- Window resize

- DOM changes

- Width/height changes

## 6️⃣ Painting

The browser fills in pixels:

- Colors

- Text

- Borders

- Shadows

- Images

Layout<br>
   &nbsp;&nbsp;↓<br>
Paint>br
(Pixels are drawn)

### 🎨 Painting is the step where the page becomes visible.

## 7️⃣ Compositing

Modern browsers split the page into layers.

Each layer:

- Is painted separately

- Is combined using the GPU

Painted Layers<br>
      &nbsp;&nbsp;↓<br>
Compositing<br>
      &nbsp;&nbsp;↓<br>
Final Screen Output<br>

### ✨ This improves:

- Animations

- Scrolling

- Performance

Properties like transform and opacity trigger only compositing (very fast).

## ✅ Best Practices

- Use defer for scripts

- Keep DOM small

- Avoid layout thrashing

- Prefer transform over top/left

- Minify and combine CSS

## 📝 Summary
- HTML → DOM
- CSS → CSSOM
- DOM + CSSOM → Render Tree
- Render Tree → Layout
- Layout → Paint
- Paint → Composite


### ➡️ HTML + CSS + JavaScript → Pixels

