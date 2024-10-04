# Variables in JavaScript<a id='toc0_'></a>    

Hello friends, in this part of the series, we will cover variables in JavaScript.

In this article, we'll cover:

- [JavaScript Variable Concept and Variable Declaration Methods](#toc1_1_)    
  - [Usage Order of `var`, `let`, and `const` Keywords](#toc1_1_1_)    
- [JavaScript Data Types](#toc1_2_)    
- [Variable Declaration in JavaScript](#toc1_3_)    
- [Re-Declaration of the Same Variable in JavaScript](#toc1_4_)    
- [Using the `$` Symbol in JavaScript](#toc1_5_)    
- [Using the `_` Symbol in JavaScript](#toc1_6_)    
- [Block Scope Concept](#toc1_7_)    
- [JavaScript Hoisting](#toc1_8_)    
- [Summary](#toc1_9_)    

I will touch upon.

I hope you enjoy reading.

Yazının Türkçe versiyonu için [linke](tr-js03-variables.ipynb) tıklayabilirsiniz.

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->

## <a id='toc1_1_'></a>[JavaScript Variable Concept and Variable Declaration Methods](#toc0_)

If we explain variables through a metaphor, we can liken them to a container filled with liquid. Just as we can change the liquids we put into the container, we can also change the data stored within variables.

**In JavaScript, a variable can be defined using one of the four methods:**

- Automatically

- Using the `var` keyword

- Using the `let` keyword

- Using the `const` keyword

Automatically declared variables **do not have a keyword at the beginning.** Therefore, we understand that a variable is automatically declared in this way. Automatically declared variables can also be used in mathematical operations.

**Example**



```python
%%script node
    
x = 4;
y = 5;
result = x + y;

// This code prints the number 9 to the console in JavaScript.
console.log(`Result: ${result}`);
```

    Result: 9


**💡 Always defining variables at the beginning of the JavaScript document or the _scope_[^1] it belongs to will prevent potential issues. I will address this under the title [JavaScript Hoisting](#javascript-hoisting).**

**💡 Between 1995 and 2015, the `var` keyword was used to declare variables. In 2015, the `let` and `const` keywords were introduced to JavaScript for variable declaration. This allows us to determine whether a document is prepared for modern or old browsers by looking at its content.**


### <a id='toc1_1_1_'></a>[Usage Order of `var`, `let`, and `const` Keywords](#toc0_)

**Variables should be declared at the beginning of the document or scope they belong to. Generally, the following order is recommended when creating variables:**

1. It is advisable not to use automatic variables.

2. If the content of a variable is constant, i.e., it will not change, it is recommended to always declare it using the `const` keyword.

3. If the content of variables of type array or object is constant, i.e., it will not change, it is recommended to always declare them using the `const` keyword.

4. In cases where the `const` keyword cannot be used, it is recommended to declare the variable using the `let` keyword.

5. If you are writing a script for older browsers, it is advisable to use the `var` keyword.


## <a id='toc1_2_'></a>[JavaScript Data Types](#toc0_)

Just like in other programming languages, JavaScript has various data types. Examples of data types include strings and numeric values, which are among the most commonly used data types in JavaScript. For now, I'll cover what we need.

**⚠️ String data types are used between `""` or `''` signs. If a numerical expression is used between `""` or `''` signs, it is referred to as a _numeric string_.**

**Example**

```javascript
// str1 is a variable of string type.
var str1 = "Test";

// str2 is a variable of numeric string type.
var str2 = "4";

// str3 is a variable of numeric string type.
var str3 = '3';

// str4 is a variable of numeric type.
var str4 = 4;

// str5 is a variable of string type.
var str5 = 'Text';
```


**Additionally, we can use backticks or template literals ` `` ` to create string content in JavaScript. Typically, within backticks, we combine both a variable and a string expression, allowing us to create dynamic content.**

**Example**


```python
%%script node

var str5 = 8;

// Utilizing backticks (template literals) to create a string that includes a variable
console.log(`Content of the str5 variable: ${str5}`);
```

    Content of the str5 variable: 8


**⚠️ Other string values except for numeric-like string values do not contribute to the result in mathematical operations. If a string is used in a mathematical expression, the result will be of string data type. This affects the result based on where the string is used. The situation is somewhat different for numeric-like string values. For more detailed information, you can refer to the section on [JavaScript Numeric-like String Values](js07-numeric-data-type.ipynb#javascript-numeric-string-values).**

<!-- [#1](https://github.com/eminaltan/learn-web/issues/1) -->

**In JavaScript, expressions are evaluated from left to right. That is, JavaScript determines where the expression will be a string based on this pattern.**

**Example**



```python
%%script node

var x = 4 + 3 + "1";

// "71" will be printed to the console.
console.log(`The console will print ${x}.`);

var y = "1" + 4 + 3;

// "143" will be printed to the console.
console.log(`The console will print ${y}.`);

// "8" will be printed to the console.
y = "9" - 4 + 3;
console.log(`The console will print ${y}.`);

```

    The console will print 71.
    The console will print 143.
    The console will print 8.


The `+` operator from mathematical operators can be used with string data types. In this case, strings are concatenated. The `+` operator for string data types is named the **_concatenation operator_**.

**Example**



```python
%%script node

let x = "Emin" + " " + "Altan";

/** 
 * "Emin" and " Altan" will be concatenated, and "Emin Altan" will be printed to the 
 * console.
 */
console.log(`The console will print ${x}.`);

```

    The console will print Emin Altan.


## <a id='toc1_3_'></a>[Variable Declaration in JavaScript](#toc0_)

The process of creating a variable in JavaScript is called **_declaration_**. When declaring a variable, the `const` and `let` keywords are commonly used.

A variable can be declared without assigning a value to it. In this case, the content of the variable is determined as `undefined`. **This does not apply to variables declared with `const`. For a variable declared with the `const` keyword, it is mandatory to assign a value on the same line as the declaration.**

**💡 `undefined` is also a keyword and can be useful, especially when creating _conditional statements_[^2].**

**Example**

```javascript
/**
 * ✔️ We created the variable x without assigning a value. In this case, the content of the variable is 
 * determined as undefined.
 */
var x;

// ❌ It is not appropriate to use the const keyword in this way for a variable declaration.
const firstName;
firstName = "Murat";

// ✔️ Declaration with the const keyword should be done in a single line.
const firstName2 = "Sinan";
```


**💡 We can declare variables of the same type in a single line, saving us time. In this case, `,` are placed between variables.**

**Example**



```python
%%script node

let firstName = "Emin", surname = "Altan", id = 500;

// "Emin" will be printed to the console.
console.log (firstName);

```

    Emin


**❗ In JavaScript, variable names actually serve as references. That is, they are used as references to represent a value. When we look at the `const` keyword from this perspective, it is used not to declare a constant variable but to create a reference for a constant value. Understanding this distinction is important when using the `const` keyword with data types like objects and arrays. I will delve into arrays and objects in the later parts of this writing.**

**Example**

```javascript
// We store our values of array type in a variable named cities declared with const.
const cities = ["Bursa", "İzmir", "Ankara"];

// We print the first element of the cities array type data (i.e., Bursa) to the console.
console.log(cities[0]);

// We replace the first element of the cities array type data (i.e., Bursa) with a new value.
cities[0] = "İstanbul";

/**
 * We print the first value of the cities reference to the console. In this case, the first value will be 
 * İstanbul, not Bursa.
 */
console.log(cities[0]);

// ❌ We cannot assign a new value to the cities reference.
cities = ["Tekirdağ", "Samsun", "Sinop"];
```


## <a id='toc1_4_'></a>[Re-Declaration of the Same Variable in JavaScript](#toc0_)

In JavaScript, a variable can be re-declared using the `var` keyword. This process is called **_re-declaring_**. In this case, the variable retains its stored data unless new data is assigned to it.

**Example**



```python
%%script node

var firstName = "Emin";

/**
 * The declaration of the firstName variable is repeated. It will retain the stored information unless a new 
 * value is assigned to the firstName variable.
 */
var firstName;

// "Emin" expression will be printed to the console.
console.log(`The console will print the expression ${firstName}.`);

firstName = "Murat";

/** 
 * The new value of the firstName variable will be Murat, and the expression "Murat" will be printed to the 
 * console.
 */
console.log(`The new value of the firstName variable will be Murat, and the console will print the expression ${firstName}.`);

```

    The console will print the expression Emin.
    The new value of the firstName variable will be Murat, and the console will print the expression Murat.


**⚠️ A variable declared with `let` and `const` cannot be re-declared. The ability to re-declare a variable is only applicable to the `var` keyword.**

**Example**

```javascript
let i = 5;
let i = 3;

// ❌ SyntaxError: Identifier 'i' has already been declared error message will return.
console.log(i);
```


## <a id='toc1_5_'></a>[Using the `$` Symbol in JavaScript](#toc0_)

**💡 Generally, the `$` symbol is not used to declare variables. It is used to give an _alias_[^3] to a method within a JavaScript library. For example, the `$` sign can be used to select all `<a>` elements in the jQuery library, like `$("a")`.**


## <a id='toc1_6_'></a>[Using the `_` Symbol in JavaScript](#toc0_)

**💡 Generally, the `_` (underscore) symbol is used in JavaScript to indicate that a variable is private.**


## <a id='toc1_7_'></a>[Block Scope Concept](#toc0_)

Before 2015 (ES6), there were two types of scope concepts in JavaScript these are **_ global scope_**[^4] and **_function scope_**[^5]. With ES6, the `let` and `const` keywords have been integrated into JavaScript. **A variable created using these keywords cannot be accessed or used outside of its scope.** This concept forms the **_block scope._**

**Example**

```javascript
{
  let x = 5;

  /** 
   * ⚠️ Variables created with the `var` keyword can be accessed and used outside of their scope (except function 
   * scope).
   */
  var y = 10;
}

/**
 * ❌ x variable cannot be accessed or used. The console will print the expression "ReferenceError: x is not 
 * defined."
 */
console.log(x);

// y variable can be accessed and used. The console will print the number 10.
console.log(y);
```

**💡 For more information about concept of scope please visit [JavaScript Scope](js23-scope-concept.ipynb) headline.**


## <a id='toc1_8_'></a>[JavaScript Hoisting](#toc0_)

Sometimes we assign a value to a variable and then declare it. In this case, JavaScript will move the variable to the top of its scope and execute the code. This is called hoisting. You can keep in mind what the word hoist means from its literal meaning.

**⚠️ The hoisting concept works fully for variables declared with the `var` keyword. A variable declared with `let` or `const` is hoisted but cannot be initialized. This means a variable declared with `let` or `const` is moved to the top of its scope, but it cannot be used before its declaration. If we try to use a variable in the _temporal dead zone_[^6], we encounter a `ReferenceError`. Such variables can be used after their declaration and data storage.**

**❗ I recommend defining a variable at the top of the scope where it will be used. Otherwise, at times, it may be difficult to understand where a particular piece of data originated from.**

**Example**

```javascript
// In the example, we first use the variable and then declare it in the second line. This is called hoisting.
carName = "Lada";
var carName;

// "Lada" is logged to the console.
console.log(carName);

// ❌ When using the hoisting feature with variables declared with let or const, we encounter a ReferenceError.
model = "Niva";
let model;
```

## <a id='toc1_9_'></a>[Summary](#toc0_)

In this section, we covered fundamental topics related to variables in JavaScript. Variables are used for storing data, and there are different ways to declare them. Variables can be declared using the `var`, `let`, and `const` keywords. In modern JavaScript applications, `let` and `const` are generally preferred, but `var` can still be used for older browsers.

Among the data types, strings and numeric values play a significant role. String expressions are defined within `""` or `''` and numeric-string values can be used in mathematical operations.

Sometimes, we may want to use a string expression along with a value. In such cases, we can use backticks ` `` ` known as template literals in JavaScript.

The concept of block scope emerged with ES6 and the introduction of `let` and `const` keywords. This concept ensures that variables are only accessible within the block where they are defined. Particularly, variables declared with `const` cannot be reassigned.

In JavaScript, hoisting refers to the movement of `var` declarations to the top of the code. However, for `let` and `const`, hoisting only moves the declaration to the top without initialization.

Understanding these fundamental concepts is crucial for developing more complex applications in JavaScript. Knowledge of data types, variable declaration methods, and scope concepts contributes to writing more effective and comprehensible code.


[^1]: The term "scope" is used to denote the area where a variable is accessible and useable.
[^2]: In JavaScript, a conditional statement allows us to change the flow of a program based on certain conditions or criteria. In such cases, we make use of expressions like `if`, `else`, or `else if`. These are referred to as conditional statements.
[^3]: In JavaScript, the content of a variable can be copied to another variable. Generally, this concept forms the basis for the term "alias." Aliases enable us to write understandable and semantic code. For example, in an expression like `let x = 5`; `var aliasVariable = x`;, `x` and `aliasVariable` share the same value. While `x` is referred to as a reference, `aliasVariable` is expressed as an alias.
[^4]: I will explain this through a metaphor. In mathematics, we are familiar with the concept of a universal set. Similar to how the universal set encompasses other sets, in JavaScript, the global scope encompasses variables or methods (functions) defined within it and makes them accessible from anywhere in the script. Thus, the global scope can be likened to the universal set in this context. In this sense, they are universal.
[^5]: It refers to the variables or other methods (functions) defined within a method (function). Variables inside the function scope cannot be accessed or used from outside; they can only be used within the scope in which they are defined. In this sense, they are considered private or local to that specific scope.
[^6]: The concept used for Hoisting is used to express that a variable is unreachable and unusable until it is defined. It remains so until the variable is declared for use.

