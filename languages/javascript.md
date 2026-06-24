# JavaScript

+ [Scripts](#scripts)
    + [Internal](#internal)
    + [External](#external)
        + [Defer](#defer)

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
