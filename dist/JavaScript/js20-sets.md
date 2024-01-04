# Sets in JavaScript<a id='toc0_'></a>

Hello, friends! In this section of the series, we will explore the concept of **_Set_** in JavaScript.

In this article, we'll cover:

- [Concept of Set in JavaScript](#toc1_1_)
- [Commonly Used Methods in the Set Data Type](#toc1_2_)
  - [`add()` Method](#toc1_2_1_)
  - [`delete()` Method](#toc1_2_2_)
  - [`has()` Method](#toc1_2_3_)
  - [`forEach()` Method](#toc1_2_4_)
  - [`values()` Method](#toc1_2_5_)
- [Usage of the `size` Property](#toc1_3_)
- [Summary](#toc1_4_)

I hope you enjoy reading.

Yazının Türkçe versiyonu için [linke](tr-js20-sets.md) tıklayabilirsiniz.

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->

## <a id='toc1_1_'></a>[Concept of Set in JavaScript](#toc0_)

**In JavaScript, we can liken the concept of **_Set_** to the array data type. Unlike arrays:**

- Sets have the property of containing **unique** elements. This means the same element cannot be repeated within a set. Therefore, Sets are used to store unique values.

- Methods are used to access elements in Sets. As you may recall, in arrays, we used index to access elements.

To create a Set, the `new Set()` constructor method is used.

**Example**

```javascript
const arry = [2, 2, 4, 5, 6, 6];

const set1 = new Set([2, 2, 4, 5, 6, 6]);

console.log(`Elements of the arry variable: ${arry}`);
console.log(`Elements of the set1 variable: ${[...set1]}`);

console.log(`Size of the arry variable: ${arry.length}`);
console.log(`Size of the set1 variable: ${set1.size}`);
```

    Elements of the arry variable: 2,2,4,5,6,6
    Elements of the set1 variable: 2,4,5,6
    Size of the arry variable: 6
    Size of the set1 variable: 4

In the example above, we created a new Set using the `new Set()` method.

As seen, both the `arry` and `set1` variables contain two occurrences of the elements `2` and `6`. When we print the contents of both variables to the console, we observe that the elements `2` and `6` within `set1` are only printed once.

**⚠️ When attempting to store multiple identical variables or values in a Set, the operation is based on the reference to the variable or value at the beginning of the data list.**

Looking at the size of the `arry` and `set1` variables, even though they are numerically the same, we notice that the size of the `set1` variable is actually 4. This is because a Set only keeps unique elements, and therefore, the size of the Set is equal to the number of unique elements it contains.

In addition to storing data, Sets can also be used to create a unique list by combining, intersecting, or taking the difference of the contents of two variables.

**Example**

```javascript
let set1 = new Set([1, 2, 3]);
let set2 = new Set([2, 3, 4]);

/**
 * The content of the union variable will be the result of the combination of two sets.
 * Duplicate values will be used only once when creating the content.
 */
let union = new Set([...set1, ...set2]);

// Finding common elements in set1 and set2 variables.
let intersection = new Set([...set1].filter((x) => set2.has(x)));

// Finding non-common! elements in set1 and set2 variables.
let difference = new Set([...set1].filter((x) => !set2.has(x)));

console.log(`Result of the union operation: ${[...union]}`);

console.log(`Result of the intersection operation: ${[...intersection]}`);

console.log(`Result of the difference operation: ${[...difference]}`);
```

    Result of the union operation: 1,2,3,4
    Result of the intersection operation: 2,3
    Result of the difference operation: 1

In the example above, union, intersection, and difference operations are performed for two sets.

Note that the operations are performed within a new Set.

**💡 Sometimes, we may want a variable with array-like properties to consist of a unique data list. In this case, we can place the array-like variable inside the `new Set()` method to turn it into a Set containing unique elements.**

**Example**

```javascript
const arry = [2, 2, 2, 2, 2, 3, 4, 5, 6, 7, 7];

// Removes repeated values in array.
const set1 = new Set(arry);

console.log(`Elements of the set1 variable: ${[...set1]}`);
```

    Elements of the set1 variable: 2,3,4,5,6,7

## <a id='toc1_2_'></a>[Commonly Used Methods in the Set Data Type](#toc0_)

So far, we have seen the concept of Set and its features; now let's delve into commonly used Set methods.

### <a id='toc1_2_1_'></a>[`add()` Method](#toc0_)

Use to add a new element to a Set.

**Example**

```javascript
// Creating an empty Set.
const set1 = new Set();

// Usage of add() method
set1.add("Emin");
set1.add("Hasan");
set1.add("Murat");

console.log(`Elements of the set1 variable: ${[...set1]}`);
```

    Elements of the set1 variable: Emin,Hasan,Murat

In the example above, the `add()` method is used with the desired value as an argument to add elements to the Set.

### <a id='toc1_2_2_'></a>[`delete()` Method](#toc0_)

Use to delete a specified element from a Set.

**Example**

```javascript
const names = ["Emin", "Hasan", "Murat"];

const set1 = new Set(names);

// Value of "Hasan" will be remove in set1 variable
set1.delete("Hasan");

console.log(`Elements of the set1 variable: ${[...set1]}`);

// The content of the original variable has been preserved.
console.log(`Elements of the names variable: ${[...names]}`);
```

    Elements of the set1 variable: Emin,Murat
    Elements of the names variable: Emin,Hasan,Murat

In the example above, the `delete()` method is used with the desired value as an argument to remove the specified element from the Set.

If you notice, despite the content being equal between the variables `set1` and `names`, the deleted value from `set1` did not disrupt the content of the `names` variable.

Additionally we can use index values for remove any element in a Set.

**Example**

```javascript
const names = ["Emin", "Hasan", "Murat"];

const set1 = new Set(names);

// Access the 2nd element in set1 and remove this value.
set1.delete(names[1]);

console.log(`Elements of set1 variable: ${[...set1]}`);
```

    Elements of set1 variable: Emin,Murat

In the example above, we access and delete the element at index 2 within the Set. The expression `delete(names[1])` allows us to access the element at index 2 in the `set1` variable and delete this element.

### <a id='toc1_2_3_'></a>[`has()` Method](#toc0_)

We may want to check whether a value or variable exists in a Set or not. In such cases, we can use the `has()` method.

The `has()` method returns a boolean result. If the element is present in the Set, the result is `true`; otherwise, it is `false`.

**Example**

```javascript
const names = ["Emin", "Hasan", "Murat"];

const set1 = new Set(names);

// Value of "Hasan" will be check in Set
console.log(
  `Result: ${
    set1.has("Hasan")
      ? "The searched element is present in the Set."
      : "The searched element is not present in the Set."
  }`
);

// Value of "Derya" will be check in Set
console.log(
  `Result: ${
    set1.has("Derya")
      ? "The searched element is present in the Set."
      : "The searched element is not present in the Set."
  }`
);
```

    Result: The searched element is present in the Set.
    Result: The searched element is not present in the Set.

In the example above, we specified the element we want to check in the Set as an argument. If the result is `true`, it indicates that the element is present in the Set, and if the result is `false`, it indicates that the element is not present in the Set.

### <a id='toc1_2_4_'></a>[`forEach()` Method](#toc0_)

Sometimes, we may want to perform a specific operation for each element in a Set. In such cases, we can use the `forEach()` method.

**Example**

```javascript
const set1 = new Set([1, 2, 3, 4, 5, 6]);

let arry = [];

// Each element's value will be increased by +1
set1.forEach((val) => arry.push(val + 1));

console.log(`Elements of the arry variable: ${arry}`);
```

    Elements of the arry variable: 2,3,4,5,6,7

In the example above, using the `forEach()` method, we increment each element value in the `set1` variable by +1 The result is then stored in the `arry` variable.

### <a id='toc1_2_5_'></a>[`values()` Method](#toc0_)

We may want to use the elements in a Set similar to properties of an object. In such cases, we can use the `values()` method. The `values()` method creates an iterable variable for the elements in the Set, allowing access to the elements and facilitating navigation through them.

**Example**

```javascript
let set1 = new Set([1, 2, 3, 4, 5, 6]);

// An iterable is created with the values() method.
let setValues = set1.values();

// Accessing Set elements using forEach on the iterable.
setValues.forEach((element) => console.log(element));
```

## <a id='toc1_3_'></a>[Usage of the `size` Property](#toc0_)

Sets normally haven't properties. In fact, `size` is not a property but a method attribute. The `size` property provides the number of unique elements in the Set.

Let's revisit the initial example and examine the `size` property.

**Example**

```javascript
const set1 = new Set([2, 2, 4, 5, 6, 6]);

console.log(`Size of the set1 variable: ${set1.size}`);
```

    Size of the set1 variable: 4

As seen above, the `size` property provides the size or number of unique elements in the `set1` variable.

## <a id='toc1_4_'></a>[Summary](#toc0_)

The concept of Set in JavaScript is a data type used for storing unique values. Unlike arrays, Sets allow each element to appear only once. To create a Set, we use the `new Set()` constructor.

Sets are useful for creating unique data lists and performing operations such as adding, deleting, and checking elements. Sets are particularly suitable when working with unique values.
