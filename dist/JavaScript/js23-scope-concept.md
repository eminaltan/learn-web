# JavaScript Scope<a id='toc0_'></a>

Hello friends, in this part of the series, we will explore the concept of **_scope_** in JavaScript.

In this article, we'll cover:

- [JavaScript Scope Concept](#toc1_1_)
  - [Block Scope](#toc1_1_1_)
  - [Function Scope](#toc1_1_2_)
  - [Global Scope](#toc1_1_3_)
- [Local Scope](#toc1_2_)
- [Summary](#toc1_3_)

I hope you enjoy reading.

Yazının Türkçe versiyonu için [linke](tr-js23-scope-concept.md) tıklayabilirsiniz.

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->

## <a id='toc1_1_'></a>[JavaScript Scope Concept](#toc0_)

In JavaScript, the **_scope_** concept refers to the area where a variable is defined and can be accessed. This area can consist of a loop, condition, or method.

A scope is created within `{}` curly braces.

**Example**

```javascript
const x = 5;

if (x == 5) {
  // This area represents the scope in the if condition.
}

for (let i = 0; i < x; i++) {
  // This area represents the scope in the for loop.
}

function myFunction() {
  // This area represents the scope in the myFunction() function.
  console.log(x);
}
```

**In JavaScript, there are 3 types of scopes:**

- Block scope

- Function scope

- Global Scope

Now, let's examine these scope types.

### <a id='toc1_1_1_'></a>[Block Scope](#toc0_)

Before 2015 (ES6), JavaScript had two types of scope concepts: **_global scope_** and **_function scope_**. With ES6, the `let` and `const` keywords were integrated into JavaScript. **A variable created using these keywords cannot be accessed or used outside of its scope.** This statement creates the concept of **_block scope_**.

**❗Block scopes are also characterized as local scopes. This means that when JavaScript starts executing code within a block scope, variables within that block scope are defined in memory, and when JavaScript concludes the execution within the block scope, the variables within that block scope are removed from memory.**

**Example**

```javascript
{
  /**
   * Enclosed within curly braces {}, this represents a block scope in JavaScript. Any variable declared with
   * const or let within this scope will have block scope characteristics.
   */
  const studentName = "Betül";

  console.log(`The value of the studentName variable: ${studentName}`);
}
```

    The value of the studentName variable: Betül

In the example above, `studentName` possesses block scope characteristics. This variable can be accessed and used within its scope. In the example, we print the value stored in the `studentName` variable within the local scope.

If we attempt to access the variable from outside its scope, we encounter an error.

**Example**

```javascript
{
  const studentName = "Betül";
}

try {
  /**
   * We are trying to access and use the studentName variable from outside block scope. Since we cannot access
   * it, the catch mechanism will be triggered, and an error message will be printed to the console.
   */
  console.log(`The value of the studentName variable: ${studentName}`);
} catch (error) {
  console.log(error.name + ": " + error.message);
}
```

    ReferenceError: studentName is not defined

In the example above, we attempted to access and use the `studentName` variable from outside its scope. In this case, JavaScript will assume that the `studentName` variable is not defined and will return the "ReferenceError: studentName is not defined" error message.

**💡 Block scopes allow us to store different types of data under the same variable name within different scopes.**

**Example**

```javascript
{
  // 1st.scope
  const x = "Şenay";
  console.log(`Value of x variable: ${x}`);
}

{
  // 2nd.scope
  const x = "279";
  console.log(`Value of x variable: ${x}`);
}
```

    Value of x variable: Şenay
    Value of x variable: 279

As seen above, the content of the `x` variable in 1st is different from the content of the `x` variable in 2nd. scope.

### <a id='toc1_1_2_'></a>[Function Scope](#toc0_)

In JavaScript, we can define a variable within a function. In this case, the variable is only valid within the function where it is defined, meaning we cannot access it from outside the function.

**❗ Function scopes are also characterized as local scopes. This means that when JavaScript starts executing code within a function scope, variables within that function scope are defined in memory, and when JavaScript concludes the execution within the function scope, the variables within that function scope are removed from memory.**

**⚠️ Normally, a variable declared using the `var` keyword has global scope characteristics. However, if a variable is declared within a function using the `var` keyword, it will have function scope characteristics, and it cannot be accessed from outside the function.**

**Example**

```javascript
function myFunction() {
  var studentName = "Şenay";

  console.log(`The value of the studentName variable: ${studentName}`);
}

myFunction();
```

    The value of the studentName variable: Şenay

In the example above, despite being declared using the `var` keyword, `studentName` possesses function scope characteristics. This means that attempting to access the `studentName` variable from outside the `myFunction()` will result in an error.

**Example**

```javascript
function myFunction() {
  var studentName = "Şenay";
}

try {
  // Trying to access the 'studentName' variable outside the function will result in an error.
  console.log(`The value of the studentName variable: ${studentName}`);
} catch (error) {
  console.log(error.name + ": " + error.message);
}
```

    ReferenceError: studentName is not defined

As seen above, when attempting to access the `studentName` variable from outside the `myFunction()`, we received the error message "ReferenceError: studentName is not defined."

The distinction between function scope and block scope is related to the usage of the `var` keyword. In function scope, a variable declared with the `var` keyword cannot be accessed from outside its scope, while in block scope, a variable declared with the `var` keyword can be accessed from outside its scope.

**Example**

```javascript
{
  // Block scope
  var carName = "Volvo";
}

function myFunction() {
  // Function scope
  var carModel = "S70";
}

// ✔️ Since carName has block scope characteristics, it can be accessed from outside its scope.
console.log(`Car brand: ${carName}`);

// ❌ Since carModel has function scope characteristics, it cannot be accessed from outside its scope.
console.log(`Car model: ${carModel}`);
```

In the example above, variables are declared using the `var` keyword. `carName` can be accessed from outside its scope, while `carModel` cannot.

**⚠️ If a variable is declared within a function scope using the `var`, `let`, or `const` keywords, it becomes inaccessible from outside its scope.**

**Example**

```javascript
function myFunction() {
  var carName = "Volvo"; // Function Scope
}

function myFunction() {
  let carName = "Volvo"; // Function Scope
}

function myFunction() {
  const carName = "Volvo"; // Function Scope
}
```

**⚠️ The parameters of a function have function scope.**

**Example**

```javascript
// The variables param1 and param2 defined within myFunction() have function scope.
function myFunction(param1, param2) {
  console.log(`Value of param1 = ${param1}`);
  console.log(`Value of param2 = ${param2}`);
}
```

### <a id='toc1_1_3_'></a>[Global Scope](#toc0_)

When a variable is defined outside of a function, it gains the property of being a global variable. The scope where the variable is located is referred to as the global scope. We can access a variable of this type from anywhere within the program.

**A variable, when defined using the `var` keyword outside of a function scope**, gains the property of being a global variable.

**Example**

```javascript
{
  var studentName = "Şenay";
}

console.log(`The value of the studentName variable: ${studentName}`);
```

    The value of the studentName variable: Şenay

In the example above, `studentName` possesses global variable characteristics due to being declared using the `var` keyword. The scope where this variable is located is considered the global scope. **If we had declared the same variable within a function, it would have demonstrated function scope characteristics, making it a local scope variable.**

When a variable is defined using `let` or `const` keywords with the encapsulation method, it exhibits global variable characteristics within its scope.

**Example**

```javascript
{
  // Main scope
  const studentName = "Şenay";

  {
    // Sub-scope
    console.log(`The value of the studentName variable: ${studentName}`);
  }
}

/**
 * We cannot access the studentName variable from here. We would encounter a ReferenceError: studentName is not
 * defined. Uncomment the console.log part and observe the result.
 */
// console.log(`The value of the studentName variable: ${studentName}`);
```

    The value of the studentName variable: Şenay

As observed above, the `studentName` variable is declared in the main scope. In this case, the `studentName` variable will gain global variable characteristics for the nested scope(s), making it accessible from within those scopes. However, when attempting to access the same variable from an outer scope, an error message will be encountered.

**💡 A variable created using the `var` keyword will be associated with the window object in HTML. Nevertheless, a globally-scoped variable created using the encapsulation method with `let` or `const` keywords will not be associated with the window object. This is because the use of `let` and `const` keywords is not defined in the window object.**

**Example**

```javascript
var carName = "Volvo";

// To access the carName variable, the syntax window.carName can be used.
document.getElementById("demo").innerHTML = "I can display " + window.carName;
```

If the `carName` variable had been defined using either the `let` or `const` keywords, attempting to access it would result in an `undefined` error.

**Example**

```javascript
let carName = "Volvo";

/**
 * We cannot use the window.carName syntax to access the carName variable. This is because the let keyword is not
 * defined in the window object.
 */
document.getElementById("demo").innerHTML =
  "I can not display " + window.carName;
```

In addition, if a variable is assigned a value without being declared using the `var`, `let`, or `const` keywords (i.e., creating an undefined variable), that variable also gains global variable characteristics.

**Example**

```javascript
function myFunction() {
  carName = "Volvo";
}

myFunction();

console.log(`The content of the carName variable: ${carName}`);
```

    The content of the carName variable: Volvo

In the example above, the variable `carName` is assigned a value without being explicitly declared. In this case, the `carName` variable gains the characteristics of an undeclared variable, and to access its content, the relevant function is called, followed by accessing the `carName` variable.

**⚠️ As an exception, in JavaScript strict mode, undeclared variables do not automatically become global variables.**

It is not recommended to use a variable by assigning a value to it without prior declaration because the scope of the variable may be uncertain, leading to unexpected errors. Whenever possible, it is better to define variables appropriately using `var`, `let`, or `const` to specify their scopes.

## <a id='toc1_2_'></a>[Local Scope](#toc0_)

The term **_local scope_** refers to the condition where a variable cannot be used outside of its scope. In this context, both block scope and function scope exhibit the characteristics of local scope. This is because it is not possible to access a variable defined within these scope types from the outside.

**Reasons for using local scope:**

- Sometimes, variables or data need to be protected for security reasons and should not be accessed from other places. In other words, the variable or value must be private. In such cases, we use local scopes.

- We ensure the isolation of variables in this way, contributing to the error-free operation of our program.

- Local scopes allow the use of the same variable names, reducing the likelihood of conflicts between variables with the same name.

- In error situations, local scopes help isolate errors within the scope, making debugging and correction processes easier.

- For a variable defined within a local scope, a memory address is created, and the variable can be used throughout the lifespan of that scope. When the JavaScript program exits the local scope, the variable's runtime is completed, and its memory address is cleared. This ensures that variables whose function has ended do not unnecessarily occupy memory space, contributing to the faster execution of our JavaScript program.

## <a id='toc1_3_'></a>[Summary](#toc0_)

In this section, we explored the concept of **_scope_** in JavaScript. In JavaScript, **_scope_** specifies the area where a variable is defined and accessible. There are three main types of scope: Block Scope, Function Scope, and Global Scope.

- **Block Scope:** Variables declared with `let` and `const` are only valid within the block they are defined. This provides a local and isolated scope.

- **Function Scope:** When a variable is declared within a function, it is only valid within that function and cannot be accessed from the outside. Function scope provides a local scope.

- **Global Scope:** When a variable is defined outside a function, it becomes a global variable and can be accessed from anywhere in the program. However, if an undefined variable is created without using the `var` keyword and has not been previously declared, in this case, the variable is automatically treated as a global variable. That is, when an undefined variable is created without using `var`, JavaScript adds this variable to the global scope.

These scope types ensure the organized use of variables for security, isolation, and error management. Scopes enhance code readability and prevent unexpected errors.
