# Introduction to JavaScript<a id='toc0_'></a>

This guide is prepared for those who want to learn JavaScript. I am skipping information about when or for what purpose JavaScript emerged. You've probably researched these details. In my opinion, it's beneficial to learn the philosophy of the job; I won't include similar information in the guide.

The guide requires basic HTML knowledge.

In this article, we'll cover:

- [The `<script>` Element](#toc1_1_)
- [JavaScript Usage Cases](#toc1_2_)
- [JavaScript Outputs](#toc1_3_)
  - [`innerHTML` Property](#toc1_3_1_)
  - [Usage of the `document.write()` Method](#toc1_3_2_)
  - [`window.alert()` Method](#toc1_3_3_)
  - [`console.log()` Method](#toc1_3_4_)
  - [Print Feature in JavaScript](#toc1_3_5_)
- [Summary](#toc1_4_)

I will touch upon.

I hope you enjoy reading.

Yazının Türkçe versiyonu için [linke](tr-js01-introduction.md) tıklayabilirsiniz.

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->

## <a id='toc1_1_'></a>[The `<script>` Element](#toc0_)

JavaScript code is placed between `<script></script>` elements.

**💡 For older browsers to interpret JavaScript code, the type attribute must be defined. In this context, when you encounter an expression like `<script type="text/javascript">`, you can understand that the web page is prepared for older browsers. In modern browsers, the type attribute doesn't need to be defined.**

JavaScript code can be placed between the `<head></head>` or `<body></body>` elements.

**Example**

```html
<!DOCTYPE html>
<html>
  <head>
    <script>
      /* In this example, JavaScript code is placed between the <head></head> elements */
      console.log("test");
    </script>
  </head>
  <body>
    <h2>JavaScript Example</h2>
  </body>
</html>

<!DOCTYPE html>
<html>
  <head>
    <body>
      <script>
        /* In this example, JavaScript code is placed between the <body></body> elements */
        console.log("test");
      </script>
      <h2>JavaScript Example</h2>
    </body>
  </head>
</html>
```

**💡 Placing JavaScript code near the `</body>` tag ensures faster interpretation and execution of the code.**

**Example**

```html
<!DOCTYPE html>
<html>
  <head>
    <body>
      <h2>JavaScript Example</h2>
      <script>
        /* Placing JavaScript code near the </body> tag will make it run faster. */
        console.log("test");
      </script>
    </body>
  </head>
</html>
```

## <a id='toc1_2_'></a>[JavaScript Usage Cases](#toc0_)

We can use JavaScript code between `<script></script>` elements or include JavaScript code from an external file.

**Using external JavaScript code provides us with several advantages:**

- Separation of HTML and JavaScript code makes the document easier to read, understand, and manage.

- The same code can be reused on other pages, avoiding the need to rewrite it, following the **_DRY1_[^1]** principle.

- JavaScript code can be cached, leading to faster page loading.

In the example below, the import of external JavaScript files onto a web page is demonstrated.

**Example**

```javascript
<script src="script1.js"></script>
<script src="script2.js"></script>
```

## <a id='toc1_3_'></a>[JavaScript Outputs](#toc0_)

**There are four methods commonly used to obtain output in JavaScript:**

- To output content into an HTML element, you can use the `innerHTML` property.

- To output content within an HTML document, you can use the `document.write()` method.

- For displaying alert messages, you can use the `window.alert()` method.

- For logging messages to the console, you can use the `console.log()` method.

Let's briefly overview these methods; I will delve into details throughout the process.

### <a id='toc1_3_1_'></a>[`innerHTML` Property](#toc0_)

Sometimes, we may want to use the result of an operation as output within an HTML element. In such cases, we generally use the `innerHTML` property.

**Example**

```html
<!DOCTYPE html>
<html>
  <body>
    <p id="content"></p>
    <script>
      /* In the example, the HTML element with the #content id will be located, and the text "test" will be inserted into it. */
      document.getElementById("content").innerHTML = "test";
    </script>
  </body>
</html>
```

### <a id='toc1_3_2_'></a>[Usage of the `document.write()` Method](#toc0_)

The `document.write()` method is generally used for testing purposes.

**❗ If the `document.write()` method is called after the HTML page has loaded, the content of the page will be overwritten.**

In the example below, the content of the HTML page **gets cleared, and the string "Test" is used** within the document when the button is clicked.

**Example**

```html
<!DOCTYPE html>
<html>
  <body>
    <p>document.write() method is called with onClick HTML event handler.</p>

    <!-- When the button is clicked, the document.write() method will execute. -->
    <button
      type="button"
      onclick="document.write(`Test`)"
    >
      Click
    </button>
  </body>
</html>
```

In the example below, the content of the HTML page will not be cleared.

**Example**

```html
<!DOCTYPE html>
<html>
  <body>
    <p>
      The document content will not be cleared because the document.write()
      method is not called.
    </p>
    <script>
      document.write("Test");
    </script>
  </body>
</html>
```

### <a id='toc1_3_3_'></a>[`window.alert()` Method](#toc0_)

Sometimes, we may want to create message boxes, similar to those in Windows. In such cases, the `window.alert()` method is used.

**⚠️ In JavaScript, the `window` keyword represents the _global_ scope object. This means that all variables, properties, and methods defined in JavaScript are, by default, part of the `window` object. The use of the `window` keyword is optional; it can be omitted.**

**Example**

```javascript
/* Both statements have the same meaning. */
window.alert("Test");

alert("Test");
```

### <a id='toc1_3_4_'></a>[`console.log()` Method](#toc0_)

The `console.log()` method is commonly used in debugging processes. It is used to output information to the JavaScript console. To access the console, we can use the browser's inspector. Typically, you can open it by right-clicking and selecting 'Inspect' or by pressing the F12 key. Then, navigate to the 'Console' tab, where you can use `console.log()` to output various information for debugging purposes."

![Console](https://wd.imgix.net/image/admin/ET1JJFtUIXvaoPCGQ94C.png?auto=format, "The console of the browser is visible in the figure.")

**Example**

```javascript
/* The code will print the string "Test" to the console. */
console.log("Test");
```

    Test

### <a id='toc1_3_5_'></a>[Print Feature in JavaScript](#toc0_)

In JavaScript, there is only the `window.print()` method. This allows obtaining a hard copy or soft copy of the content on the browser screen.

**Example**

```html
<!DOCTYPE html>
<html>
  <body>
    <!-- Helps us to print the content from the browser. -->
    <button onclick="window.print()">Print Screen</button>
  </body>
</html>
```

## <a id='toc1_4_'></a>[Summary](#toc0_)

In this section, we briefly introduced JavaScript. We discussed the use of JavaScript code, factors affecting performance, and some JavaScript methods commonly used in debugging processes.

[^1]: DRY an acronym for "Don't Repeat Yourself," is an approach that aims to avoid repeating the same code.
