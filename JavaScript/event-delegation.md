# Event Delegation in JavaScript
## Introduction
Event Delegation is a JavaScript technique where a single event listener is added to a parent element to handle events triggered by its child elements.  
It improves performance and makes event handling easier, especially when working with dynamic content.


## What is Event Delegation?
Instead of attaching event listeners to multiple child elements, Event Delegation allows us to attach one listener to their parent and determine which child triggered the event using JavaScript.

This works because of **event bubbling**.

## Event Bubbling
When an event occurs on an element, it bubbles up through its parent elements in the DOM tree.  
Example flow:  
**Child → Parent → Body → Document**  
Event Delegation relies on this bubbling behavior.


## Without Event Delegation

### HTML


```html
<ul>
  <li>Apple</li>
  <li>Banana</li>
  <li>Orange</li>
</ul>

```
 ### JavaScript
 
 ```javascript
 document.querySelectorAll("li").forEach(item => {
  item.addEventListener("click", () => {
    console.log(item.innerText);
  });
});

```
##  Problems
- Multiple event listeners are created
- Poor performance for large lists
- Dynamically added elements won’t work automatically

## With Event Delegation

### HTML
```html
<ul id="fruitList">
  <li>Apple</li>
  <li>Banana</li>
  <li>Orange</li>
</ul>

```
### JavaScript
```javascript
document.getElementById("fruitList").addEventListener("click", (event) => {
  if (event.target.tagName === "LI") {
    console.log(event.target.innerText);
  }
});

```
## Advantages
- Only one event listener
- Better performance
- Works for dynamically added elements
- Cleaner and maintainable code

## Dynamic Elements Example
Even if a new <li> is added later, Event Delegation will still work without adding a new event listener.
```javascript
const list = document.getElementById("fruitList");

const newItem = document.createElement("li");
newItem.textContent = "Mango";
list.appendChild(newItem);

```

## When to Use Event Delegation
- Handling lists or tables
- Dynamic UI elements
- Large number of similar elements
- Improving performance
## Interview Questions: Event Delegation

### Q1. What is Event Delegation in JavaScript?

**Answer:**  
Event Delegation is a technique where a single event listener is attached to a parent element to handle events triggered by its child elements. It works by using event bubbling and identifying the target element with `event.target`.



### Q2. Why is Event Delegation preferred over multiple event listeners?

**Answer:**  
Event Delegation improves performance by reducing the number of event listeners, simplifies code, and automatically supports dynamically added elements.

## Conclusion
Event Delegation is an important JavaScript concept that helps manage events efficiently by using event bubbling. It results in cleaner code and better performance.
