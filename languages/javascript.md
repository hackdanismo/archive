# JavaScript

+ [Scripts](#scripts)
    + [Internal](#internal)
    + [External](#external)
        + [Defer](#defer)
+ [Loading](#loading)
+ [Select Elements](#select-elements)
    + [Select Multiple Elements](#select-multiple-elements)
+ [Variables](#variables)

## Scripts
`JavaScript` can either be written as an `internal` script, where the `JavaScript` code is added directly to the `HTML` using `<script>` tags, or `external` where a `<script>` tag is used but a the code is added to an external file with a `.js` file extension.

### Internal
The `JavaScript` code is added internally into the `HTML` usually before the closing `</body>` element:

```html
    <script>
        console.log("This is JavaScript.");
    </script>
</body>
</html>
```

### External
The `JavaScript` code is added to the page using an external file with the extension of `.js`. The `<script>` tag uses a `src` attribute to connect the `HTML` to the `JavaScript`.

```html
    <script src="scripts/script.js"></script>
</body>
</html>
```
External is recommended as it allows the `JavaScript` code to be shared across multiple pages using a single file.

```text
project/
├── index.html
└── scripts/
    └── script.js
```

### Defer
The `defer` attribute can be added to `external` script files to allow the `JavaScript` to be downloaded whilst the `HTML` is being parsed but to not run the `JavaScript` until the `HTML` has been fully parsed. This allows the `JavaScript` to be placed in the `<head>` section of the page. Without `defer`, a normal script can run too early before elements in the `<body>` exist. With `defer`, the `HTML` is ready before the `JavaScript` code runs.

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <script src="scripts/script.js" defer></script>
```
Without `defer`, placing scripts before the closing `</body>` tag allows the HTML to parse before the `JavaScript` is downloaded to aid performance.

## Loading
Within the `JavaScript` code itself, we want to ensure the `DOM (Document Object Model)` is loaded, so the `HTML` elements are loaded, before the script loads. We can listen for `DOMContentLoaded` and add our `JavaScript` code within.

Usually this method is not needed when using `defer` as the attribute handles the loading.

```javascript
// scripts/script.js

document.addEventListener("DOMContentLoaded", () => {
    // Add the JavaScript code here.
});
```

A better option, when using `defer`, is to wrap the JavaScript code within an `IIFE (Immediately Invoked Function Expression)` to keep all variables local scoped within to avoid polluting the global scope. We only need to use `DOMContentLoaded` should `defer` not being used.

```javascript
// scripts/script.js

(() => {
    // Add the JavaScript code inside the IIFE if using defer on the <script>.
})();
```

We can also pass in `document` and `window` into the `IIFE` if they are being used:

```javascript
// scripts/script.js

// We can change the names here to something like: "w" or "d" to reference them inside the IIFE.
((window, document) => {
    // Add the JavaScript code inside the IIFE if using defer on the <script>.
})(window, document);
```

## Select Elements
We can use the `querySelector` method of the `document` object to select an `HTML` element on the page using `JavaScript`. As an example, we can select the `<h1>` element from the `HTML` using this line of code:

```javascript
const heading = document.querySelector("h1");
```

```javascript
// scripts/script.js

((document) => {
    const heading = document.querySelector("h1");
    // Log the element in the console (this is not needed, but useful to testing).
    console.log(heading);
})(document);
```

The HTML element may look like this:

```html
<h1>Welcome to the page</h1>
```

The text within the `<h1>` element can be changed using `textContent`.

```javascript
// Select the heading element in the HTML.
const heading = document.querySelector("h1");
// Update the heading text.
heading.textContent = "New heading text";
```

Elements can be selected like so:

```javascript
// Select a tag or element:
const heading = document.querySelector("h1");
// Select an element with a classname of element:
const class = document.querySelector(".element");
// Select an element with an ID of element:
const id = document.querySelector("#idExample");
```

The HTML:

```html
<!-- Tag or element -->
<h1>Welcome to the page</h1>
<!-- Element with a classname -->
<div class="element">Element with a classname</div>
<!-- Element with an ID -->
<div id="idExample">Element with an ID</div>
```

We can add a safety check to stop the code running should no element be found:

```javascript
// scripts/script.js

((document) => {
    // Select the heading element in the HTML.
    const heading = document.querySelector("h1");

    // If there's no heading, stop executing the code, check for null, prevents errors.
    if (!heading) return;

    // Update the heading text.
    heading.textContent = "New heading text";
})(document);
```

### Select Multiple Elements
To select multiple elements we use the `querySelectorAll` method.

```html
<p class="item">Paragraph number one</p>
<p class="item">Paragraph number two</p>
<p class="item">Paragraph number three</p>
```

The `querySelectorAll` method is used to get all items with the `class` of `item`:

```javascript
const items = document.querySelectorAll(".item");
```

We then use a `loop` to apply `JavaScript` code to all the items that have been selected:

```javascript
items.forEach(item => {
    // JavaScript code to apply to all items that have been selected.
});
```

The full code:

```javascript
// scripts/script.js

((document) => {
    // Select all elements that have the class of "item" in the HTML.
    const items = document.querySelectorAll(".item");

    // Loop over all the items that have been selected.
    items.forEach(item => {
        // JavaScript code to apply to all items that have been selected.
    });
})(document);
```

## Variables
A `variable` in `JavaScript` is a named container for storing a value. There are three ways to declare a variable: `var`, `const` and `let`.

Variables declared with `const` have been used in earlier code examples to store the elements that have been selected using `querySelector` or `querySelectorAll` methods.

```javascript
// This is the legacy method of declaring variables in JavaScript.
var name = "Dan";
// The const keyword is used to declare a variable value that does not change.
const name = "Dan";
const pi = 3.14;
// The let keyword is used for values that can change.
let score = 10;

// Select the element and store in a variable.
const heading = document.querySelector("h1");
// Select all the elements and store in a variable.
const items = document.querySelectorAll(".item");
```

A `variable` created outside of any `function` or `block` can be used almost anywhere. A `variable` created inside a `function` can only be used inside that function.

```javascript
// This is a variable declared outside of the function.
let name = "Dan";
// Log the value of the variable = "Dan"
console.log(name);

function sayName() {
    // Log the value of the variable - "Dan"
    console.log(name);
}

// This is a variable declared inside of a function.
function greet() {
    // Declare the variable inside of the function. It can only be used here
    let message = "Hello";
    // Log the value of the variable - "Hello"
    console.log(message);
}

// Call the function to run the code.
greet();

// Error: message is not defined.
console.log(message); 
```
