# JavaScript

+ [Scripts](#scripts)
    + [Internal](#internal)
    + [External](#external)
        + [Defer](#defer)
+ [Loading](#loading)
+ [Select Elements](#select-elements)

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
