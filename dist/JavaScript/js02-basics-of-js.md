# Fundamentals of JavaScript<a id='toc0_'></a>

Hello, friends! In this article, we will take a brief look at the fundamentals of JavaScript.

In this article, we'll cover:

- [JavaScript Statement Concept](#toc1_1_)
- [JavaScript White Space Usage](#toc1_2_)
- [JavaScript Code Blocks](#toc1_3_)
- [Usage of JavaScript Keywords](#toc1_4_)
- [JavaScript Syntax Concept](#toc1_5_)
- [JavaScript Immutable and Mutable Concepts](#toc1_6_)
- [Data Types in JavaScript](#toc1_7_)
- [JavaScript Variables](#toc1_8_)
  - [Variables in JavaScript are Dynamically Typed](#toc1_8_1_)
- [JavaScript Operators](#toc1_9_)
- [Concept of JavaScript Expressions](#toc1_10_)
- [Concept of JavaScript Identifiers](#toc1_11_)
- [JavaScript Case Sensitivity](#toc1_12_)
- [Summary](#toc1_13_)

I will briefly touch on them, and in the coming days, I will elaborate on the topics.

I hope you enjoy reading.

Yazının Türkçe versiyonu için [linke](tr-js02-basics-of-js.md) tıklayabilirsiniz.

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->

## <a id='toc1_1_'></a>[JavaScript Statement Concept](#toc0_)

A computer program creates expressions that will be executed by the computer. In programming languages, these are called **_statements_**. A JavaScript application consists of a list of statements.

In JavaScript, statements can consist of variables, values, operators, expressions, keywords, and comments.

**Example**

```javascript
/* The line below carries the statement feature. */
var x;
```

JavaScript statements are executed in the order they are written.

**Example**

```javascript
console.log("This will run first.");
console.log("Then this will run.");
console.log("Finally, this will run.");
```

    This will run first.
    Then this will run.
    Finally, this will run.

The `;` symbol is used to separate statements from each other. A single line can contain more than one statement.

**Example**

```javascript
/* The example below shows three statements created in a single line. */
console.log("1.Statement"); console.log("2.Statement"); console.log("3.Statement");
```

    1.Statement
    2.Statement
    3.Statement

## <a id='toc1_2_'></a>[JavaScript White Space Usage](#toc0_)

JavaScript ignores white space characters. This means that statements written on a single line have the same meaning as statements created on multiple lines.

**💡 To ensure code readability, it is recommended to write each statement on a separate line. Keeping each line to around 80 characters on average can enhance readability.**

**Example**

```javascript
let x = 3, let y = 4;

/* The above expression can also be written as follows. */
let x = 3;
let y = 4;
```

## <a id='toc1_3_'></a>[JavaScript Code Blocks](#toc0_)

In JavaScript, `{}` braces are used to group code. Grouped code blocks are referred to as **_methods_** or **_functions_**.

**Example**

```javascript
function drive() {
  console.log("Let's ride George");
}

// The expression "Let's ride George" is printed to the console.
drive();
```

    Let's ride George

## <a id='toc1_4_'></a>[Usage of JavaScript Keywords](#toc0_)

JavaScript expressions often begin with a keyword.

**❗ Keyword names cannot be used when defining variable or method names because these keywords are reserved in JavaScript.**

**Example**

```javascript
/* ❌ The variable declaration below is incorrect. */
let var = 5;

// The statement "SyntaxError: Unexpected token 'var'" will be printed to the console.
console.log(var);
```

The commonly used keywords are listed below.

| **Keyword** | **Description**                           |
| ----------- | ----------------------------------------- |
| `var`       | Creates a variable.                       |
| `let`       | Creates a block-scoped variable.          |
| `const`     | Creates a block-scoped constant variable. |

I will touch upon terms and usage types as we go along. I will explain the purposes of keywords like `var`, `const`, `let` and their differences in the process.

## <a id='toc1_5_'></a>[JavaScript Syntax Concept](#toc0_)

Syntax in JavaScript determines the arrangement of code. We can think of these rules as the writing guide or grammar of a language.

**⚠️ If there are incorrect syntaxes, the program or code blocks will not work.**

**Example**

```javascript
// We see the syntax used to create a variable in the example.
var x;
var y;

"Osman" = let z;

/**
 * ❌ The syntax of the z variable is incorrect. The statement "SyntaxError: Invalid
 * left-hand side in assignment" will be printed to the console.
 */
console.log (z);
```

## <a id='toc1_6_'></a>[JavaScript Immutable and Mutable Concepts](#toc0_)

**In JavaScript, variables are divided into two groups based on data types:**

- Immutable (Constant values)

- Mutable (Variable values)

Constant values are also called **_Literals_**. Each assigned value has a new address in memory (RAM), and the content of the assigned value cannot be changed in memory.

**💡 We generally use constant values in places where we want to preserve the original data. For example, the original data may be used in multiple places. Data that is not preserved can lead to undesired results in the program.**

**⚠️ When a new value is assigned to a constant-valued variable, a new space is allocated in memory to store the data. This can lead to memory-related issues. Therefore, if performance is a priority, we should use constants less frequently.**

Variable values are also referred to as **_variables_**. The assigned value has an address in memory, and the content of the assigned data can be changed. **Therefore, they have the property of being references. When a new data is assigned to a variable-valued variable, a new space is not used in memory. The relevant reference address where the data is stored is found, and the old data is overwritten, saving the new data to the reference address.**

**💡 Variable-valued values do not take up space in memory like constants, as they use reference addresses for data. Therefore, if performance is a priority, we can use this data type.**

**Example**

Below is an example of the immutable property.

```javascript
// The studentName variable has the immutable property.
let studentName = "Emin";

console.log(`The content of the studentName variable is: ${studentName}`);

// We store the content of the studentName variable in the personName variable.
let personName = studentName;

/**
 * We store a new value in the studentName variable. In this case, a new address will be allocated in RAM for
 * Hasan.
 */
studentName = "Hasan";

console.log(
  `Pay attention here. The value stored in the personName variable is: ${personName}`
);
console.log(`The content of the studentName variable is: ${studentName}`);
```

    The content of the studentName variable is: Emin
    Pay attention here. The value stored in the personName variable is: Emin
    The content of the studentName variable is: Hasan

Below is an example of the mutable property.

**Example**

```javascript
// Our variable 'vehicle' has mutable properties.
let vehicle = { type: "car", color: "orange" };

console.log(`The expression ${vehicle["type"]} is printed to the console.`);

// We create a variable named 'bus' and set its value to be referenced by the 'vehicle' variable.
let bus = vehicle;

// We access the 'type' key of the 'bus' variable and store a new value.
bus["type"] = "long bus";

console.log(`The expression ${bus["type"]} is printed to the console.`);

/**
 * ⚠️ Pay attention here. The value stored in 'vehicle[type]' will be overwritten with "long bus,"
 * and the console will print the expression "long bus."
 *
 * This is because when we change the content of the 'bus' variable, we simultaneously change the
 * content at the reference address in memory that holds the data.
 */
console.log(`The expression ${vehicle["type"]} is printed to the console.`);
```

    The expression car is printed to the console.
    The expression long bus is printed to the console.
    The expression long bus is printed to the console.

## <a id='toc1_7_'></a>[Data Types in JavaScript](#toc0_)

**In JavaScript, there are two main types of data:**

- Primitive Data Types

- Object Data Types

Primitive data types consist of **_number, string, boolean, undefined, null, symbol_**, and **_bigint_**. Except for the **_null_** data type, these are also characterized by their **immutable** nature.

Object data types consist of **_object, array, date_** and **_function_**. These data types, on the other hand, exhibit the **mutable** property.

It's important to understand that primitive data types are immutable, meaning their values cannot be changed once they are assigned. In contrast, object data types are mutable, allowing their values to be modified. This distinction plays a crucial role in understanding how data is handled and manipulated in JavaScript.

## <a id='toc1_8_'></a>[JavaScript Variables](#toc0_)

Variables in programming languages are used to store data. In JavaScript, variables can be declared using the `var`, `const` or `let` keywords.

**Example**

```javascript
// We stored the number 4 in the variable x.
var x = 4;

// We stored the expression "Hasan" in the variable y.
let y = "Hasan";

// We stored the number 3.14 in the constant variable pi.
const pi = 3.14;

console.log(`Value of x: ${x}`);
console.log(`Value of y: ${y}`);
console.log(`Value of pi: ${pi}`);
```

    Value of x: 4
    Value of y: Hasan
    Value of pi: 3.14

### <a id='toc1_8_1_'></a>[Variables in JavaScript are Dynamically Typed](#toc0_)

In JavaScript, variables have dynamic type, meaning a variable can be used to hold values of different data types.

**Example**

```javascript
// The data type of the variable x is undefined.
let x;

// The data type of the variable x is number.
x = 5;

// The data type of the variable x is string.
x = "Sebile";

console.log(`Value of x: ${x}`);
```

    Value of x: Sebile

## <a id='toc1_9_'></a>[JavaScript Operators](#toc0_)

Essentially, we can use mathematical expressions that we use in everyday life within JavaScript. These are expressions such as `( + - * / )` and are referred to as **_arithmetic operators_**.

**⚠️ In JavaScript, the `=` sign functions as an assignment operator, meaning it does not imply mathematical equality. For equality operation `==` or `===` operators are used. Data type of these operators will be boolean.**

**Example**

```javascript
// We assigned the value 4 to the variable x. The reference x is now storing the value 4.
let x = 4;

console.log(`Value of x:${x}`);
```

    Value of x:4

In JavaScript, there are many operators. I will touch upon them as needed.

## <a id='toc1_10_'></a>[Concept of JavaScript Expressions](#toc0_)

In JavaScript, the calculation of an operation in a single line is referred to as an **_expression_**. An expression consists of variables, values, and operators.

**Example**

```javascript
var x = 4;
var y = 3;

// Expression
var z = 4 * 3;
```

## <a id='toc1_11_'></a>[Concept of JavaScript Identifiers](#toc0_)

Identifiers are used to name variables or functions in programming.

**When naming variables in JavaScript, the following points should be noted:**

- In JavaScript, an identifier can start with an uppercase or lowercase letter, `$`, or `_`.

- JavaScript identifiers are **unique**, meaning the same name cannot be used for another variable or method.

- JavaScript is case-sensitive, so `x` and `X` represent different variables.

- Numeric values cannot be the initial character when defining an identifier, but they can be used in other parts of the identifier.

- Reserved keywords in JavaScript cannot be used as identifiers.

**Example**

```javascript
/**
 * ✔️ Proper naming conventions. ⚠️ Even though the variable names in the first two lines are the same,they
 * define different variables.
 */
var deneme;
var Deneme;
var DENEME01;
var $deneme;
var _deneme;

// ❌ Incorrect naming conventions
var 1deneme;

// The 'let' keyword cannot be used as a variable name.
var let;
```

## <a id='toc1_12_'></a>[JavaScript Case Sensitivity](#toc0_)

JavaScript is case-sensitive, meaning it distinguishes between uppercase and lowercase letters. `firstname` and `firstName` do not have the same meaning.

**⚠️ The `-` character cannot be used in JavaScript due to it being reserved.**

## <a id='toc1_13_'></a>[Summary](#toc0_)

In this section, we covered the fundamentals of JavaScript. We explored concepts such as JavaScript statements, white space usage, code blocks, keyword usage, syntax, immutable and mutable concepts, data types, and variables. Additionally, we touched on JavaScript operators, expressions, identifiers, and the distinction between uppercase and lowercase letters.

This foundational knowledge provides a basis for understanding JavaScript programming. In the upcoming sections, we will delve deeper into each topic, providing more detailed explanations and examples.
