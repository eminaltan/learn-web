# Loops in JavaScript<a id='toc0_'></a>

Hello friends, in this episode of the series, we will examine the concept of loops and their types in JavaScript.

In this article, we'll cover:

- [Concept of Loops and Types](#toc1_1_)
  - [`for` Loop](#toc1_1_1_)
    - [Usage of Scopes in the `for` Loop](#toc1_1_1_1_)
  - [`for...in` Loop](#toc1_1_2_)
  - [`for...of` Loop](#toc1_1_3_)
  - [`while` Loop](#toc1_1_4_)
  - [`do...while` Loop](#toc1_1_5_)
  - [Usage of `break` and `continue` Statements in a Loop](#toc1_1_6_)
- [Using Labels in JavaScript](#toc1_2_)
- [Summary](#toc1_3_)

I hope you enjoy reading.

Yazının Türkçe versiyonu için [linke](tr-js19-loops.md) tıklayabilirsiniz.

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->

## <a id='toc1_1_'></a>[Concept of Loops and Types](#toc0_)

Sometimes, we may want to process and store our data in a computer environment. Performing this task manually for a few pieces of data will be easy. However, if we consider having a list consisting of hundreds of data, this process will not only be difficult but also lead to labor and time loss.

In such situations, the concept of loops in programming comes to our rescue and makes our work easier by automating **repetitive** tasks.

Loops are especially common in array data types.

**Listing the commonly used loop types in JavaScript:**

- `for`

- `for...in`

- `for...of`

- `while`

- `do...while`

Now, let's delve into these loop types.

### <a id='toc1_1_1_'></a>[`for` Loop](#toc0_)

We may want to perform certain tasks automatically based on a condition we specify. In such cases, we can use the `for` loop.

**Prototype:**

```javascript
for (exp1; exp2; exp3) {
  // Code block for the for loop. The code to be executed is written here.
}
```

Above, we see the structure of the `for` loop. Three expressions are used in the `for` loop, and the expressions are separated by the `;` sign.

**Let's discuss the expressions:**

- `exp1`: Usually, variables and values to be used in the loop are defined in this part. This section is executed once before the code block of the `for` loop is executed.

- `exp2`: The loop condition is created in this part. The code block of the `for` loop is executed as long as the result of the loop condition is `true`. The loop terminates when the condition is `false`.

- `exp3`: This part is used to iterate the loop. This part will be executed if the loop condition is `true`.

**Example**

```javascript
for (let i = 0; i < 5; i++) {
  console.log(`Value of i: ${i}`);
}
```

    Value of i: 0
    Value of i: 1
    Value of i: 2
    Value of i: 3
    Value of i: 4

**If we explain the above `for` loop:**

1. In the loop, the `exp1` expression corresponds to the `i = 0` part. We assigned the value 0 to the variable `i`. This expression will run once when the loop starts.

2. In the loop, the `exp2` expression corresponds to the `i < 5` part. Here, we set the loop condition. The loop will continue to run as long as the variable `i` is less than 5, returning a `true` result. It will keep running as long as it is `true`, and it will terminate when it becomes `false`.

3. In the loop, the `exp3` expression corresponds to the `i++` part. As long as the loop condition returns `true`, the value of the variable `i` will be incremented by +1, ensuring the repetition of the loop.

**Example**

```javascript
const cars = ["Lada", "Tata", "BMW", "Audi", "Mercedes"];

// We can define multiple variables simultaneously in the exp1 part.
for (let i = 0, len = cars.length, text = ""; i < len; i++) {
  text += cars[i] + " ";

  console.log(`Car brand: ${text}`);
}
```

    Car brand: Lada
    Car brand: Lada Tata
    Car brand: Lada Tata BMW
    Car brand: Lada Tata BMW Audi
    Car brand: Lada Tata BMW Audi Mercedes

As seen in the example above, we defined multiple variables for the `exp1` part. We separated the variables using the `,` sign.

Using the `exp1` part inside the `for` loop is optional. You can define the `exp1` part outside the loop, eliminating the need for the `exp1` part within the for loop.

**Example**

```javascript
// We defined the i variable corresponding to the exp1 part outside the for statement.
let i = 0;

for (; /* We skipped the exp1 part. */ i < 5; i++) {
  console.log(`Value of i: ${i}`);
}
```

    Value of i: 0
    Value of i: 1
    Value of i: 2
    Value of i: 3
    Value of i: 4

The use of the `exp2` part (loop condition) within the for loop is optional.

**⚠️ If the loop condition is not determined, the break statement should be included in the loop. Otherwise, the program will crash because the loop will not terminate.**

**Example**

```javascript
for (let i = 0 /* We skipped the exp2 part. */; ; i++) {
  console.log(`Value of i: ${i}`);

  // The loop will terminate when the value of i is 5.
  if (i == 5) {
    break;
  }
}
```

    Value of i: 0
    Value of i: 1
    Value of i: 2
    Value of i: 3
    Value of i: 4
    Value of i: 5

The usage of the `break` statement is visible above. If we had not used the `break` statement, the code would have entered an infinite loop and causing the program to crash.

**💡 In situations where we have not yet determined the termination condition `for` loop but expect it to emerge during the coding process, we can benefit from the `break` statement.**

The use of the `exp3` part (iterate value) within the for loop is optional. In this case, the `exp3` part is defined within the for loop.

**Example**

```javascript
for (let i = 0; i < 5 /* We skipped the exp3 part */; ) {
  console.log(`Value of i: ${i}`);

  // We defined the exp3 part inside the loop.
  i++;
}
```

    Value of i: 0
    Value of i: 1
    Value of i: 2
    Value of i: 3
    Value of i: 4

As seen in the example above, we did not use the `exp3` part among the components that make up the for loop. Instead, we used the iterate value within the code block.

#### <a id='toc1_1_1_1_'></a>[Usage of Scopes in the `for` Loop](#toc0_)

Unless a variable is declared using the `var` keyword, if the value of a variable is changed within a `for` loop, the new value of the variable will only be valid within the scope where it is found. The value of the variable in the higher scope remains unchanged.

**Example**

```javascript
let i = 5;

for (let i = 0; i < 10; i++) {
  console.log(`Value of i within the for scope: ${i}`);
}

console.log(
  `Value of i outside the loop: ${i}. The value of the i variable remains the same.`
);
```

    Value of i within the for scope: 0
    Value of i within the for scope: 1
    Value of i within the for scope: 2
    Value of i within the for scope: 3
    Value of i within the for scope: 4
    Value of i within the for scope: 5
    Value of i within the for scope: 6
    Value of i within the for scope: 7
    Value of i within the for scope: 8
    Value of i within the for scope: 9
    Value of i outside the loop: 5. The value of the i variable remains the same.

The reason for this is that the `let` keyword has block scope characteristics. If we had used the `var` keyword in the same example, the value stored in the variable `i` would have been updated. This is because the `var` keyword has a global scope feature. <!-- To better understand the topic, you can refer to the [Block Scope Concept](js03-variables.ipynb#block-scope-kavramı) section. -->

**Example**

```javascript
// The value of the i variable will be 10 after the loop.
var i = 5;

for (var i = 0; i < 10; i++) {
  console.log(`Value of i within the for scope: ${i}`);
}

console.log(
  `Value of i outside the loop: ${i}. The value of the i variable has been updated.`
);
```

    Value of i within the for scope: 0
    Value of i within the for scope: 1
    Value of i within the for scope: 2
    Value of i within the for scope: 3
    Value of i within the for scope: 4
    Value of i within the for scope: 5
    Value of i within the for scope: 6
    Value of i within the for scope: 7
    Value of i within the for scope: 8
    Value of i within the for scope: 9
    Value of i outside the loop: 10. The value of the i variable has been updated.

### <a id='toc1_1_2_'></a>[`for...in` Loop](#toc0_)

It is generally used to access the property values of an object-variable.

**Prototype:**

```javascript
for (let keys in object) {
  // Code block for the for...in loop. The code to be executed is written here.
}
```

In the above code, we see the structure of the `for...in` loop. The `for...in` loop consists of two variables: `keys` and `object`.

**Regarding these variables:**

- `object`: Represents the object to be used in the `for...in` loop.

- `keys`: Represents the `key` part of the property in the object.

**Example**

```javascript
const cars = { carName: "Lada", carModel: 1200, carColor: "white" };

var stringHolder;

// Copy the keys of properties in the cars variable to the keys variable.
for (let keys in cars) {
  /**
   * Using a switch condition, we determine the value of the stringHolder variable
   * based on the current key value.
   */
  switch (keys) {
    case "carName":
      stringHolder = "Car Brand";
      break;
    case "carModel":
      stringHolder = "Car Model";
      break;
    default:
      stringHolder = "Car Color";
  }

  console.log(`${stringHolder}: ${cars[keys]}`);
}
```

    Car Brand: Lada
    Car Model: 1200
    Car Color: white

**Explanation of the above `for...in` loop:**

1. The `for...in` loop will iterate over each property in the cars object. (Example: `carName: Lada`)

2. In each iteration, the keys part of the property is copied to the `keys` variable within the loop.

3. Based on the current value of the `keys` variable, the `switch` statement determines the value of the `stringHolder` variable. Later, we will use this variable when printing the property values.

4. Using the current value of the `keys` variable in the loop, we access the values in the `cars` property (i.e., `Lada`, `1200`, and `white`). Access is achieved using the syntax `cars[key]`. The values inside the properties are printed to the console along with the `stringHolder` variable.

The `for...in` loop can also be used to access elements in an array variable.

**Example**

```javascript
const cars = ["Lada", "Audi", "BMW", "Tata"];

for (let car of cars) {
  console.log(`Car brand: ${car}`);
}
```

    Car brand: Lada
    Car brand: Audi
    Car brand: BMW
    Car brand: Tata

**❗ Using the `for...in` loop is not recommended for arrays data type. This is because it can cause issues related to index when we want to use array methods within the loop. Instead of `for...in`, you can use `for`, `for...of` loops, or `Array.forEach()` method.**

**Example**

```javascript
const cars = ["Lada", "Audi", "BMW", "Tata"];

// We used an arrow function as the callback method.
cars.forEach((car) => console.log(`Car brand: ${car}`));
```

    Car brand: Lada
    Car brand: Audi
    Car brand: BMW
    Car brand: Tata

In the example above, we utilized the `Array.forEach()` method. The `Array.forEach()` method will iterate over each element in the `cars` array variable, and for each element, the `forEach()` method will execute. The value of the element will be transferred to the variable `i`, and the console will print the value of the current element.

### <a id='toc1_1_3_'></a>[`for...of` Loop](#toc0_)

It is used for variables whose values are iterable. The data types of such variables can be any of Array, String, Maps, NodeList, etc.

**Prototype:**

```javascript
for (iterator of object) {
  // Code block for the for...of loop. The code to be executed is written here.
}
```

Above, we see the structure of the `for...of` loop. The `for...of` loop consists of two variables: `iterator` and `object`.

**Regarding these variables:**

- `iterator`: In each iteration of the loop, the value or content of the `object` variable is copied to the `iterator` variable.

- `object`: Represents a value with iterable properties. The data type of this value can be one of array, string, maps, NodeList, etc.

**Example**

```javascript
const cars = ["Lada", "Audi", "BMW", "Tata"];

/**
 * The elements of the cars variable will be copied to the iterator variable, and the loop
 * will iterate for each element.
 */
for (const iterator of cars) {
  console.log(`Car brand: ${iterator}`);
}
```

    Car brand: Lada
    Car brand: Audi
    Car brand: BMW
    Car brand: Tata

The working logic of the `for...of loop` is similar to the `for...in` loop.

In the case of the `cars` variable, each element is copied to the `iterator` variable, and as long as the loop condition is `true`, the value of the `iterator` variable will be printed to the console.

Let's create a `for...of` loop for a variable with the string data type.

**Example**

```javascript
const message = "Hello";

/**
 * Each character of the message variable will be copied to the iterator variable,
 * and this value will be printed to the console.
 */
for (const iterator of message) {
  console.log(iterator + " ");
}
```

    H
    e
    l
    l
    o

In the example above, each character of the `message` variable will be copied to the `iterator` variable in each iteration, and the current value of the `iterator` variable will be printed to the console.

### <a id='toc1_1_4_'></a>[`while` Loop](#toc0_)

It is similar to the `for` loop. The `while` loop will execute the code block associated with it as long as the specified condition is `true`. The loop will terminate when the condition evaluates to `false`.

**Prototype:**

```javascript
while (condition) {
  /**
   * Code block for the while loop. The code here will be executed as long as
   * the condition is true.
   */
}
```

**Example**

```javascript
let i = 0;

while (i < 5) {
  /**
   * The loop will run as long as the value of the i variable is less than 5, and
   * the current value of the i variable will be printed to the console.
   */
  console.log(`Current value of the i variable: ${i}`);

  /**
   * In each iteration, we increment the value of the i variable by +1 so that we
   * can repeat the loop and test the condition inside the while loop.
   */
  i++;
}
```

    Current value of the i variable: 0
    Current value of the i variable: 1
    Current value of the i variable: 2
    Current value of the i variable: 3
    Current value of the i variable: 4

**⚠️ To retest the condition within the `while` loop and to enter the loop (this is called iteration), we are incrementing the value of the `i` variable by +1 using the `i++` syntax. This way, the condition checks the value stored in the `i` variable each time. If we didn't increment the value of the `i` variable, the `while` loop would become an infinite loop, causing our JavaScript program to crash.**

If we had done the above example with a `for` loop

**Example**

```javascript
for (let i = 0; i < 5; i++) {
  console.log(`Current value of the i variable: ${i}`);
}
```

    Current value of the i variable: 0
    Current value of the i variable: 1
    Current value of the i variable: 2
    Current value of the i variable: 3
    Current value of the i variable: 4

### <a id='toc1_1_5_'></a>[`do...while` Loop](#toc0_)

It works similarly to the `while loop`. The difference is that the `while` loop checks the condition first and then executes the code, while the `do...while` loop executes the code first and then checks the condition. Therefore, the `do...while` loop will be executed at least once, even if the condition evaluates to `false`.

**Prototype:**

```javascript
do {
  /**
   * Code block for the do...while loop. This code will be executed at least once
   * even if the condition is false.
   */
  /**
   * Later, the condition is checked. If the condition evaluates to true, the loop
   * starts running again. Otherwise, the loop terminates.
   */
} while (condition);
```

**Example**

```javascript
let i = 0;

// The loop will be executed at least once.
do {
  console.log(`Current value of the i variable: ${i}`);
  i++;
} while (
  // Then the loop condition will be checked.
  i < 5
);
```

    Current value of the i variable: 0
    Current value of the i variable: 1
    Current value of the i variable: 2
    Current value of the i variable: 3
    Current value of the i variable: 4

**⚠️ To retest the condition within the `do...while` loop and to enter the loop (this is called iteration), we are incrementing the value of the `i` variable by +1 using the `i++` syntax. This way, the condition checks the value stored in the `i` variable each time. If we didn't increment the value of the `i` variable, the `do...while` loop would become an infinite loop, causing our JavaScript program to crash.**

### <a id='toc1_1_6_'></a>[Usage of `break` and `continue` Statements in a Loop](#toc0_)

Sometimes, we may want a loop to terminate when a specific condition is met or for a loop to skip its execution just once. In such situations, we use the `break` and `continue` statements.

If we use the `break` statement, the loop will terminate when the specified condition is met.

If we use the `continue` statement, the loop will not execute once when the specified condition is met, and it will not produce a result.

**Example**

```javascript
const studentNames = ["Emin", "Murat", "Ömer", "Hasan"];

for (const iterator of studentNames) {
  // If the content of the iterator variable is "Ömer," the loop will terminate.
  if (iterator === "Ömer") {
    break;
  }

  console.log(`Student's name: ${iterator}`);
}
```

    Student's name: Emin
    Student's name: Murat

**Let's explain:**

1. In the example above, the elements of the variable named `studentNames`, which is of type array, are copied to the `iterator` variable.

2. In each iteration of the loop, the condition specified in the `if` statement is tested. If the condition is met, the `break` statement in the `if` block will be executed, and the loop will be terminated.

3. The copied value is printed to the console.

If the example above had been done using the `continue` statement, when the condition is met, the loop would be paused temporarily, and then it would continue to run. In other words, the value "Ömer" would not be printed to the console.

**Example**

```javascript
const studentNames = ["Emin", "Murat", "Ömer", "Hasan"];

for (const iterator of studentNames) {
  // If the content of the iterator variable is "Ömer," the current iteration is skipped.
  if (iterator === "Ömer") {
    continue;
  }

  console.log(`Student's name: ${iterator}`);
}
```

    Student's name: Emin
    Student's name: Murat
    Student's name: Hasan

**⚠️ `break` and `continue` statements are the only types of statements in JavaScript that can exit a block.**

## <a id='toc1_2_'></a>[Using Labels in JavaScript](#toc0_)

Sometimes, in a loop, we may want the program to exit the loop and continue execution from a specific point when a certain condition (e.g., an `if` statement) is met. To achieve this, we use labels in conjunction with the `break` and `continue` statements. This way, when the specified condition is met, we can exit the code block of the loop and continue the program flow from a designated point.

Labels are particularly useful in nested loops.

**Example**

```javascript
// We define a variable named scores with an array data type.
let scores = [];

// We assign values to the elements of the scores variable.
scores[0] = 5;
scores[1] = 10;
scores[2] = 15;
scores[3] = 20;
/** scores[4] = 25;
 *
 * Let's comment out the 3rd element of the array. This way, an empty element with an undefined data type will be
 * created.
 */
scores[5] = 30;

/**
 * The total variable will hold the total sum of array elements. We will use the result variable
 * to indicate if the loop is continuing.
 */
let total = 0,
  result = false;

// We have a label named example. This label corresponds to the if block.
example: if (scores.length > 0) {
  // We use a for loop to access all elements in the scores variable.
  for (let i = 0; i < scores.length; i++) {
    /**
     * The isNaN() method checks whether each element in the scores variable has a numeric value or not.
     *
     * If the value is not numeric, the loop/condition will end, and we will continue the program from the
     * location corresponding to the example label.
     */
    if (isNaN(scores[i])) {
      break example;
    } else {
      total = total + scores[i];
    }
  }

  // If the loop ends successfully, we set the value of the result variable to true.
  result = true;
}

result
  ? console.log(`The result of the summation: ${total}`)
  : console.log(
      "Summation operation could not be completed. There are array elements not included in the sum."
    );
```

    Summation operation could not be completed. There are array elements not included in the sum.

In the example above, we used the `example` label in conjunction with the `break` statement. If the result of the condition `if (isNaN(scores[i]))` is `true`, the loop will terminate, and the program will return to the starting point labeled as `example`, continuing execution from the next line.

Let's create an example for the `continue` statement.

**Example**

```javascript
const studentNames = ["Emin", "Murat", "Ömer", "Hasan"];

example: for (let i = 0; i < studentNames.length; i++) {
  // If the current element is "Ömer," the loop will be skipped for this iteration.
  if (studentNames[i] == "Ömer") {
    continue example;
  } else {
    console.log(`Current value of the element: ${studentNames[i]}`);
  }
}
```

    Current value of the element: Emin
    Current value of the element: Murat
    Current value of the element: Hasan

## <a id='toc1_3_'></a>[Summary](#toc0_)

Loop structures in JavaScript are used to repeat specific tasks and iterate over data. These loops provide a variety of options to address different needs and scenarios.

- **`for` Loop:** Used to iterate over numerical values based on a specific condition. It is commonly employed to traverse numbers within a certain range.

- **`for...in` Loop:** Used to access object properties. It is useful for iterating over the keys of an object.

- **`for...of` Loop:** Used to iterate over iterable objects. It can be applied to data types such as arrays and strings.

- **`while` Loop:** Used to repeat a code block as long as a specific condition is true. If the condition is not initially met, the block may not execute at all.

- **`do...while` Loop:** The condition check occurs at the end of the loop block. Therefore, the block executes at least once.

Loops are a crucial tool in programming, enabling us to perform repetitive tasks more efficiently and systematically. However, it's important to be cautious while using loops to prevent infinite loops or unintended situations. Always ensure proper condition checks when working with loops.
