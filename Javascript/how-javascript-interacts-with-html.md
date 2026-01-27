# 🧩 How JavaScript Interacts with HTML
## 📌 Introduction

HTML gives structure to a webpage, but on its own it is static.
JavaScript brings that page to life by reading, modifying, and reacting to HTML.

In simple words:

### JavaScript talks to HTML through the DOM.

This interaction allows webpages to:

- Respond to user actions

- Change content dynamically

- Update styles without reloading the page

## 🧠 The Big Picture
HTML  →  DOM  ←  JavaScript


- HTML is converted into a DOM tree by the browser

- JavaScript accesses and modifies this DOM

- Changes in the DOM update what you see on the screen

## 📄 What Role Does HTML Play?

HTML:

- Defines the structure of the webpage

- Creates elements like buttons, text, images, inputs

Example:
```
<button>Click me</button>
```

On its own, this button does nothing.

## ⚙️ What Role Does JavaScript Play?

JavaScript:

- Accesses HTML elements

- Listens for user actions

- Changes content, attributes, and styles

Example:
```
<button onclick="alert('Hello!')">Click me</button>
```

Now the button responds to a click.

## 🌳 The DOM (Document Object Model)

When a browser loads HTML, it creates a tree-like structure called the DOM.

Example HTML:
```
<h1>Hello</h1>
<p>Welcome</p>
```


DOM structure:

Document<br>
 ├── h1<br>
 │  &nbsp;&nbsp;  └── "Hello"<br>
 └── p<br>
    &nbsp;&nbsp;  └── "Welcome"<br>


### 📌 JavaScript does not directly modify HTML files It modifies this DOM tree instead.

## 🌳 DOM Tree Representation

After the browser parses HTML, it creates a DOM Tree — a tree-like structure that represents all HTML elements as nodes.

![Dom Tree](./assets/dom%20tree)


## 🔍 Accessing HTML Elements Using JavaScript

JavaScript uses the document object to access HTML.

Common methods:

- document.getElementById("title")
- document.querySelector("p")
- document.querySelectorAll(".item")


Example:
```
<h1 id="title">Hello</h1>
```

### const heading = document.getElementById("title");


Now JavaScript can control that h1 element.

## ✏️ Changing HTML Content

JavaScript can change text inside HTML elements.

### heading.textContent = "Hello JavaScript!";


Result on page:

- Hello JavaScript!

## 🎨 Changing HTML Styles

JavaScript can modify CSS styles dynamically.

- heading.style.color = "red";
- heading.style.fontSize = "32px";


### 📌 This changes the inline style of the element.

## 🖱 Responding to User Actions (Events)

JavaScript can listen for events like:

- Click

- Input

- Hover

- Key press

Example:
```
<button id="btn">Click me</button>


const btn = document.getElementById("btn");

btn.addEventListener("click", () => {
  alert("Button clicked!");
});
```


### 🧠 This is how webpages become interactive.

## 🔄 Updating the Page Without Reloading

JavaScript can:

- Add new elements

- Remove elements

- Update content dynamically

Example:
```
const p = document.createElement("p");
p.textContent = "New paragraph added!";
document.body.appendChild(p);
```

### ✨ No page reload required.

## ✅ Best Practices

- Place scripts at the bottom of <body> or use defer

- Keep HTML and JavaScript separate

- Use addEventListener instead of inline events

- Write clean and readable selectors

## 📝 Summary
- HTML → creates structure
- Browser → converts HTML to DOM
- JavaScript → reads & modifies the DOM
- DOM changes → update the webpage
<br><br>

# ➡️ JavaScript brings HTML to life