# JavaScript Error Handling<a id='toc0_'></a>

In this part of the series, we will explore the **Error Handling** concept in JavaScript, focusing on the `try`, `catch`, `throw`, and `finally` keywords.

In this article, we'll cover:

- [Concept of JavaScript Error Handling](#toc1_1_)
- [`try` and `catch` Keywords](#toc1_2_)
  - [JavaScript `Error` Object and Properties](#toc1_2_1_)
    - [`RangeError`](#toc1_2_1_1_)
    - [`ReferenceError`](#toc1_2_1_2_)
    - [`SyntaxError`](#toc1_2_1_3_)
    - [`TypeError`](#toc1_2_1_4_)
    - [`URIError`](#toc1_2_1_5_)
- [`throw` Keyword](#toc1_3_)
- [`finally` Keyword](#toc1_4_)
- [Summary](#toc1_5_)

I hope you enjoy reading.

Yazının Türkçe versiyonu için [linke](tr-js22-try-catch.md) tıklayabilirsiniz.

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->

## <a id='toc1_1_'></a>[Concept of JavaScript Error Handling](#toc0_)

The term "error handling" in JavaScript refers to the process of identifying, handling, and managing errors that occur during the execution of a program. Errors arise when an application encounters unexpected situations, including user input errors, network connection issues, or file not found scenarios.

Error handling enables meaningful error messages to be displayed to users, aiding them in better understanding the encountered issues.

In JavaScript, error handling is typically implemented using the `try`, `catch`, `finally`, and `throw` keywords.

Now, let's delve into these keywords.

## <a id='toc1_2_'></a>[`try` and `catch` Keywords](#toc0_)

The `try` and `catch` keywords are used together friends. If we want to execute or control to code we write the code in `try` block. As long as the program doesn't encounter any issues, the code within the `try` block will run.

The `catch` block, on the other hand, contains the code to be executed in case of an error. Typically, the content of this block provides information to the user about the error message.

**Example**

```javascript
try {
  let num = 0;
  num = num + 1;
  console.log(`Result: ${num}`);
} catch (error) {
  console.log(error);
}
```

    Result: 1

Above, we see an example of a `try-catch` block. If there is no error, the code inside the `try` block will be executed.

If an error occurs within the code in the `try` block, the execution of the `try` block will be halted, and the code inside the `catch` block will be initiated. At the end of the process, an error message will be presented to the user.

**Örnek**

```javascript
try {
  let num = 0;

  // Since we didn't define the x variable, we will receive the "ReferenceError: x is not defined" error message.
  num = num + x;
  console.log(`Result: ${num}`);
} catch (error) {
  console.log(error);
}
```

As seen above, the variable `x` was **not defined** in the program, yet we still used the `x` variable within the `num = num + x` expression. In this case, JavaScript will terminate the execution of the code inside the `try` block, initiate the code inside the `catch` block, and log the "ReferenceError: x is not defined" message to the console.

### <a id='toc1_2_1_'></a>[JavaScript `Error` Object and Properties](#toc0_)

In JavaScript, predefined error messages are defined within the `Error` object. In the previous example, the predefined error message `ReferenceError` was used to create an error. Alongside `ReferenceError`, JavaScript has 6 more predefined error values.

Let's list them:

| **Error Name**   | **Description**                                                 |
| ---------------- | --------------------------------------------------------------- |
| `EvalError`      | Represents an error regarding a function.                       |
| `RangeError`     | Indicates that a numeric value is outside the valid range.      |
| `ReferenceError` | Represents an error when a non-existent variable is referenced. |
| `SyntaxError`    | Indicates a syntax error in the code.                           |
| `TypeError`      | Represents an error when a value is not of the expected type.   |
| `URIError`       | Used to indicate that a URI is malformed.                       |

**❗ `EvalError` is deprecated and not commonly used in modern JavaScript. Therefore, I'm skipping the explanation of `EvalError`.**

#### <a id='toc1_2_1_1_'></a>[`RangeError`](#toc0_)

`RangeError` indicates that a numeric value is outside the valid range.

**Example**

```javascript
let num = 1;

try {
  // Attempting to format the num variable with a precision of 500 digits will result in a RangeError.
  num.toPrecision(500);
} catch (error) {
  console.log(error.name);
}
```

    RangeError

#### <a id='toc1_2_1_2_'></a>[`ReferenceError`](#toc0_)

`ReferenceError` indicates situations where a variable reference is not valid.

**Example**

```javascript
try {
  let num = 0;

  // Since we didn't define the x variable, we will receive the ReferenceError message.
  num = num + x;
  console.log(`Result: ${num}`);
} catch (error) {
  console.log(error.name);
}
```

    ReferenceError

#### <a id='toc1_2_1_3_'></a>[`SyntaxError`](#toc0_)

`SyntaxError` occurs when there is a syntax error in the code.

**Example**

```javascript
try {
  // Using an invalid argument inside the eval method will result in a SyntaxError.
  let invalidCode = eval("2 +");
} catch (error) {
  console.log(error.name);
}
```

    SyntaxError

#### <a id='toc1_2_1_4_'></a>[`TypeError`](#toc0_)

`TypeError` occurs when an expression used for a variable is not of the expected type.

**Example**

```javascript
let num = 1;

try {
  // Using the toUpperCase() method on the num variable will result in a TypeError.
  num.toUpperCase();
} catch (error) {
  console.log(error.name);
}
```

    TypeError

#### <a id='toc1_2_1_5_'></a>[`URIError`](#toc0_)

`URIError` occurs when there are illegal characters in a URL.

**Example**

```javascript
try {
  // Using invalid characters in the URL will result in a URIError.
  decodeURI("%%%");
} catch (error) {
  console.log(error.name);
}
```

    URIError

Above the `Error` object, there are some properties determined by Mozilla and Microsoft.

**These are:**

- `fileName` (Mozilla)

- `lineNumber` (Mozilla)

- `columnNumber` (Mozilla)

- `stack` (Mozilla)

- `description` (Microsoft)

- `number` (Microsoft)

**❗ It is not recommended to use these properties because they lack cross-browser support and may not work in every browser.**

## <a id='toc1_3_'></a>[`throw` Keyword](#toc0_)

So far, we have examined the properties of the predefined `Error` object in JavaScript. To make error messages more meaningful, developers may want to create custom error messages using the `throw` keyword.

**Example**

```javascript
let x;

try {
  // Using the throw keyword to create a developer-defined error message.
  if (x === undefined) throw "The value of x is not defined.";
} catch (error) {
  console.log(error);
}
```

    The value of x is not defined.

In the above example, we defined a variable `x` with the data type `undefined` using the `let x` statement. In the `try` block, we used an `if` statement to check the data type of the `x` variable. If the data type of the `x` variable is `undefined`, we used the `throw` keyword to create a developer-defined error message. We passed the created error message to the `catch` block's `error` parameter and printed the result to the console.

Technically, this process is called **throwing an error** or **throwing an exception**.

## <a id='toc1_4_'></a>[`finally` Keyword](#toc0_)

The `finally` keyword allows our program to return an additional result independent of the `try-catch` block. Typically, operations like releasing or cleaning up resources are performed in this block.

For example, using the `try-catch` block, we can provide the user with an error message if a form is incorrectly filled out. The `finally` keyword can then be used to clean up and make the content of the relevant form element ready for reuse.

**Example**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1.0"
    />
    <link
      rel="stylesheet"
      href="test.css"
    />
    <title>try-catch-finally keywords of JavaScript Kitchen</title>

    <style>
      body {
        font-family: Arial, sans-serif;
      }

      form {
        width: 300px;
        margin: 20px;
      }

      label {
        display: block;
        margin-bottom: 5px;
      }

      input {
        width: 100%;
        padding: 5px;
        margin-bottom: 10px;
      }

      button {
        padding: 8px;
        background-color: #4caf50;
        color: #fff;
        border: none;
        cursor: pointer;
      }
    </style>
  </head>
  <body>
    <label for="inputField">Enter Your Text:</label>
    <input
      type="text"
      id="js-inputField"
      name="js-inputField"
      required
    />

    <button id="js-button">Send</button>

    <p id="js-message"></p>
    <script>
      const jsInputField = document.getElementById("js-inputField");
      const jsButton = document.getElementById("js-button");
      const jsMessage = document.getElementById("js-message");

      jsButton.addEventListener("click", () => {
        try {
          if (jsInputField.value.includes("pen")) {
            jsMessage.innerHTML = "'pen' string found in entered text.";
          } else {
            throw "Can't find a 'pen' string in the entered text.";
          }
        } catch (error) {
          jsMessage.innerHTML = error;
        } finally {
          // Delete the finally block and observe the state of the text field in the form.
          jsInputField.value = "";
        }
      });
    </script>
  </body>
</html>
```

Copy the above code into an empty HTML page. Fill out the form separately for text containing and not containing the "pen" expression, then click the "Send" button to observe the form content.

Perform the same action by removing the `finally` block and observe the difference.

**🖱️ You can access the working example by clicking [here](https://codepen.io/eminaltan/pen/vYPKWjQ).**

## <a id='toc1_5_'></a>[Summary](#toc0_)

In JavaScript, **error handling** is an important concept for controlling and providing meaningful feedback to users about possible errors that may occur during the program's execution. The process involves using the `try`, `catch`, `finally`, and `throw` keywords.

- Code within the `try` block runs normally regardless of whether an error occurs.

- The `catch` block executes when an error occurs within the `try` block, handling the error. Operations are performed here to display a meaningful error message to the user.

- The `finally` block runs independently of the `try-catch` block in all situations. Typically, operations like releasing or cleaning up resources occur in this block.

Developers also have the ability to create their custom error messages using the `throw` keyword. This is useful, especially for controlling the flow of the program and customizing error messages under specific conditions.

Commonly encountered error types in JavaScript include `RangeError`, `ReferenceError`, `SyntaxError`, `TypeError`, and `URIError`. Each represents different situations and provides developers with the ability to perform specific actions based on the type of error.

**In conclusion**, error handling is a crucial practice to enhance the reliability of a JavaScript application and improve the user experience. A robust error handling strategy minimizes the impact of errors and provides users with meaningful feedback.
