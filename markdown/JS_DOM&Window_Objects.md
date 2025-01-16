### Understanding the DOM and Window Object in JavaScript

#### DOM (Document Object Model)

The **DOM** (Document Object Model) is a programming interface for web documents. It represents the structure of a document as a tree of objects, where each node is an object that represents a part of the document. The DOM allows you to manipulate the content, structure, and style of web pages using JavaScript.

**Key Concepts:**
- **Nodes**: Individual components of the DOM, including elements, attributes, and text.
- **Elements**: Represent the tags in the document, such as `<div>`, `<p>`, `<a>`.
- **Attributes**: Provide additional information about elements, such as `id`, `class`, `href`.
- **Methods**: Functions available on DOM objects to interact with them, like `getElementById()`, `querySelector()`, and `createElement()`.

**MDN Resources:**
- [Introduction to the DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
- [Document Object Model (DOM)](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)

**Example:**

Consider the following HTML snippet:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Example</title>
</head>
<body>
    <h1 id="header">Hello, World!</h1>
    <p class="text">This is a paragraph.</p>
</body>
</html>
```

You can interact with this document using JavaScript:

```javascript
// Accessing the DOM
let header = document.getElementById('header'); // Gets the <h1> element
header.textContent = 'Hello, Universe!'; // Changes the text content

let paragraph = document.querySelector('.text'); // Gets the <p> element with class "text"
paragraph.style.color = 'blue'; // Changes the text color to blue
```

#### Window Object

The **window** object is the global object in a web browser environment. It represents the browser window and provides access to various properties and methods, such as those for interacting with the browser's history, screen, and other features. It also acts as the global context for JavaScript code running in the browser.

**Key Concepts:**
- **Global Scope**: All global JavaScript variables and functions are properties of the `window` object.
- **Methods**: Functions provided by the `window` object to interact with the browser, such as `alert()`, `confirm()`, `prompt()`, and `setTimeout()`.
- **Properties**: Attributes of the `window` object that provide information about the window, such as `window.innerWidth` (width of the viewport) and `window.location` (URL of the current document).

**MDN Resources:**
- [Window](https://developer.mozilla.org/en-US/docs/Web/API/Window)
- [Window Properties](https://developer.mozilla.org/en-US/docs/Web/API/Window#properties)

**Example:**

```javascript
// Accessing properties and methods of the window object
console.log(window.innerWidth); // Logs the width of the browser window
console.log(window.location.href); // Logs the current URL

// Using window methods
window.alert('Hello, World!'); // Displays an alert box with a message
window.setTimeout(function() {
    console.log('This message is displayed after 2 seconds');
}, 2000); // Executes code after 2 seconds
```
