# Embedded JavaScript (EJS)
 EJS is a **Templating Engine** for Express.js that lets you **render dynamic HTML pages** using JavaScript variables.

## EJS =  HTML + JavaScript

# Real Life Analogy

- EJS = chocolate mold
- Template HTML = shape
- Data = filling that changes for each page

# One of Best & Simple Use of EJS:
 
- HTML alone can't do calculation or show dynamic data:

`<h2> 2+2 </h2>`   
output: 2+2 (plain text)

- EJS allows JavaScript Logic directly in HTML:

`<h2><%= 2+2 %></h2>`         
output: 4

# Simple Structure Program:

<img width="1542" height="452" alt="Image" src="https://github.com/user-attachments/assets/e6ee68ee-c000-4fcb-a85b-3b293f1e5131" />

`app.set('view engine', 'ejs');`  // this line tell express to use EJS for rendering pages with dynamic content


