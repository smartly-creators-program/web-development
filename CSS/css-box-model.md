# CSS Box Model

## Introduction
The CSS Box Model explains how elements are sized and spaced on a webpage.  
Every HTML element is treated as a box by the browser.
We use the box model to understand how width, padding, border and margin work together.

## Why do we use the Box Model?
The box model helps us control the size and spacing of elements so layouts look clean and is easy to predict.
Without understanding it, elements may appear bigger than expected or spacing may look incorrect.

## Parts of the Box Model
The box model has four main parts:

- **Content**
  This is the actual content inside the element, like text or images.
-**Padding** 
  The space between the content and the border.
-**Border**
  A line that surrounds the padding and content.
-**Margin** 
  The space outside the border that separates elements from each other.

 ## Simple Example

```css
div {
  width: 200px;
  padding: 10px;
  border: 2px solid black;
  margin: 20px;
}
```

## Example Explanation
In this example, the width is set to 200px, but the element takes more space on the page and this happens because padding, border, and margin are added around the content.
So the final size of the element is larger than just the width value.
