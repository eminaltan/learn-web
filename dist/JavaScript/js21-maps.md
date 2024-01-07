# Maps in JavaScript<a id='toc0_'></a>

Hello friends, in this part of the series, we will explore the concept of **_Map_** in JavaScript.

In this article, we'll cover:

- [Map Concept in JavaScript](#toc1_1_)
  - [Map Elements Iterated Directly](#toc1_1_1_)
  - [Has the `size` Property](#toc1_1_2_)
  - [Part of Key Can Be of Any Data Type](#toc1_1_3_)
  - [Map Elements Sorted According to Insertion Order](#toc1_1_4_)
  - [Map Objects Based on Value Equality](#toc1_1_5_)
- [Commonly Used Methods in the Map Data Type](#toc1_2_)
  - [`set()` Method](#toc1_2_1_)
  - [`get()` Method](#toc1_2_2_)
  - [`delete()` Method](#toc1_2_3_)
  - [`has()` Method](#toc1_2_4_)
  - [`forEach()` Method](#toc1_2_5_)
  - [`entries()` Method](#toc1_2_6_)
- [Summary](#toc1_3_)

I hope you enjoy reading.

Yazının Türkçe versiyonu için [linke](tr-js21-maps.md) tıklayabilirsiniz.

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->

## <a id='toc1_1_'></a>[Map Concept in JavaScript](#toc0_)

In JavaScript, we can liken the **_Map_** concept to the object data type. A Map consists of **_key-value_** pairs, similar to elements in objects.

To create a Map, we use the `new Map()` constructor method.

**Example**

```javascript
const maps = new Map([
  [625, "Murat"],
  [276, "Emin"],
  [198, "Hasan"],
]);

// Logging the contents of the 'maps' variable
console.log(`Content of the 'maps' variable: ${[...maps]}`);

// Retrieving the name associated with the key '276'
console.log(`Name of the student with the number 276: ${maps.get(276)}`);
```

    Content of the 'maps' variable: 625,Murat,276,Emin,198,Hasan
    Name of the student with the number 276: Emin

In the example above, we created a variable named `maps` in JavaScript and used the `new Map()` constructor method to store the values we wanted in the form of an array within the `maps` variable. We then used the `get()` method to print the name of a student whose number we knew to the console.

**Differences Between Maps and Objects:**

- While object properties cannot be iterated directly, Map elements can be iterated directly.

- Unlike objects, Maps have a `size` property.

- In an object, the key part of a property is either a string or a symbol, whereas there is no such restriction for the key part of Map elements. The key part can be of any data type.

- The order of object properties may vary, whereas in Map objects, elements are sorted based on the order of insertion, and this order is preserved.

- Objects rely on reference equality, whereas Maps rely on value equality.

Now, let's take a closer look at each difference.

### <a id='toc1_1_1_'></a>[Map Elements Iterated Directly](#toc0_)

Unlike objects, we can access the elements of a Map variable directly using iterable functions such as `for...of` loop or `forEach`.

**Example**

```javascript
const student = {
  studentName: "Sibel",
  studentLastName: "Özel",
  studentNumber: 219,
};

// The "for...of" loop does not work on objects; it will throw an error.
try {
  for (const [key, value] of student) {
    console.log(`${key}: ${value}`);
  }
} catch (error) {
  console.error(`Error message: ${error.message}`);
}
```

    Error message: student is not iterable

In the example above if we directly use the `for...of` loop for the `student` object, we will receive an error message. This is because object properties do not inherently have iterable characteristics.

Let's demonstrate the same example by creating a variable with Map feature.

**Example**

```javascript
const student = new Map([
  ["studentName", "Sibel"],
  ["studentLastName", "Özel"],
  ["studentNumber", 219],
]);

// Accessing elements of student Map with for...of loop
for (const [key, value] of student) {
  console.log(
    `key part of student variable: ${key} | value part of student variable: ${value}`
  );
}
```

    key part of student variable: studentName | value part of student variable: Sibel
    key part of student variable: studentLastName | value part of student variable: Özel
    key part of student variable: studentNumber | value part of student variable: 219

As can be seen, we accessed the keys and values within the `student` directly using a `for...of` loop.

### <a id='toc1_1_2_'></a>[Has the `size` Property](#toc0_)

Unlike objects, to determine the size of a Map, we use the `size` property.

**Example**

```javascript
const student = new Map([
  ["studentName", "Sibel"],
  ["studentLastName", "Özel"],
  ["studentNumber", 219],
]);

const student2 = {
  studentName: "Batuhan",
  studentLastName: "Akar",
  studentNumber: 50,
};

const student2Size = Object.entries(student2).length;

console.log(`Size of the 'student' variable: ${student.size}`);
console.log(`Size of the 'student2' variable: ${student2Size}`);
```

    Size of the 'student' variable: 3
    Size of the 'student2' variable: 3

Above, we determine the size of the `student` variable using the `size` property.

**To determine the size of the variable `student2`, which is an object:**

1. As shown in the example, we use the `entries()` method of the `Object` object to create an array-type content from the key-value pairs in `student2`.

2. We determine the size of the created content using the `length` property.

3. We store the result of the size in a variable named `student2Size`.

As seen, it is easier to determine the size of the Map-like variable `student` compared to the object-like variable `student2`.

### <a id='toc1_1_3_'></a>[Part of Key Can Be of Any Data Type](#toc0_)

Recall that the key part of an object had to be of type string or symbol. In the case of a Map-like variable, there is no such limitation; the key part can be of any data type.

For example, suppose we want to create a list of personnel IDs and names based on the ID from a database. In such a case, we can benefit from the Map data type.

**Example**

```javascript
const personal = new Map([
  [1, "Emin"],
  [2, "Murat"],
  [3, "Hasan"],
  [4, "Barçın"],
]);

for (const [key, value] of personal) {
  console.log(`Personel ID's: ${key} | Name of Personel: ${value}`);
}
```

    Personel ID's: 1 | Name of Personel: Emin
    Personel ID's: 2 | Name of Personel: Murat
    Personel ID's: 3 | Name of Personel: Hasan
    Personel ID's: 4 | Name of Personel: Barçın

In the example above, as can be seen, the key part of the `personal` variable consists of the number data type. Using a `for...of` loop, we printed the ID and name information of the personnel to the console.

### <a id='toc1_1_4_'></a>[Map Elements Sorted According to Insertion Order](#toc0_)

In JavaScript objects, properties generally do not have a specific order. Object properties are not sorted based on the order in which they are added. In JavaScript, object properties are in the form of key-value pairs, and the order of these pairs does not follow a specific sequence.

However, this is not the case with Maps. In Maps, an element added to the Map is stored at the end.

**💡 In situations where order matters, we can benefit from Map or array data types.**

**Example**

```javascript
const personal = new Map([
  [1, "Emin"],
  [2, "Murat"],
  [3, "Hasan"],
  [4, "Barçın"],
]);

// We're add "Burak" value in personal variable.
personal.set(5, "Burak");

for (const [key, value] of personal) {
  console.log(`Personel ID's: ${key} | Name of Personel: ${value}`);
}
```

    Personel ID's: 1 | Name of Personel: Emin
    Personel ID's: 2 | Name of Personel: Murat
    Personel ID's: 3 | Name of Personel: Hasan
    Personel ID's: 4 | Name of Personel: Barçın
    Personel ID's: 5 | Name of Personel: Burak

As seen in the example above, we added a new employee named "Burak" to the `personal` variable using the `set()` method. When we iterate over the list, "Burak" is placed at the end of the list.

### <a id='toc1_1_5_'></a>[Map Objects Based on Value Equality](#toc0_)

In objects, two different variables with object properties are considered different if they do not have the same reference, even if their contents are the same.

This is not the case with Maps. If two Maps have the same key-value pairs, these Maps are considered equal.

**Example**

```javascript
const obj1 = { firstName: "Hasan" };
const obj2 = { firstName: "Hasan" };

const map1 = new Map([
  ["Emin", "Altan"],
  ["Hasan", "Taş"],
]);

const map2 = new Map([
  ["Emin", "Altan"],
  ["Hasan", "Taş"],
]);

console.log(`Are obj1 and obj2 equal?: ${obj1 === obj2}`);
console.log(
  `Are map1 and map2 equal?: ${[...map1.keys()][0] === [...map2.keys()][0]}`
);
```

    Are obj1 and obj2 equal?: false
    Are map1 and map2 equal?: true

In the example above, even though the key-value pairs of `obj1` and `obj2` are the same, they are considered different variables. This is because object data types are reference-based. **Unless there is reference equality, separate memory addresses are used for both variables. Therefore, the comparison of `obj1` and `obj2` is based on the memory address, not on the data type or the stored data. If these variables shared the same memory address, i.e., if a reference-based variable was used for comparison, the result would be `true`.**

For Map-like variables, comparing them involves checking if the key-value pairs and their corresponding values match, and this is sufficient for the result to be `true`.

## <a id='toc1_2_'></a>[Commonly Used Methods in the Map Data Type](#toc0_)

So far, we've covered the concept and features of the Map. Now, let's delve into some of the commonly used methods in Map.

### <a id='toc1_2_1_'></a>[`set()` Method](#toc0_)

Used to add a new element to a Map.

**Example**

```javascript
const student = new Map();

// Using the set() method to store key-value pairs in the 'student' variable.
student.set(1, "Emin");
student.set(2, "Murat");
student.set(3, "Can");

for ([key, value] of student) {
  console.log(`Elements of the 'student' variable: ${key} ${value}`);
}
```

    Elements of the 'student' variable: 1 Emin
    Elements of the 'student' variable: 2 Murat
    Elements of the 'student' variable: 3 Can

Above, we create an empty Map named `student` using the `new Map()` constructor method and use the `set()` method to store elements in the variable.

We use a `for...of` loop to print the stored elements to the console.

### <a id='toc1_2_2_'></a>[`get()` Method](#toc0_)

Returns the value associated with a key in the Map.

**Example**

```javascript
const student = new Map();

student.set(1, "Emin");
student.set(2, "Murat");
student.set(3, "Can");

// Accessing the value associated with the key '1' in the Map.
console.log(student.get(1));
```

    Emin

In the example above, the `get()` method will retrieve the value associated with the key specified as the argument.

Let's go back to the previous example and use the `get()` method to access the values of the Map element with a key value of `1`.

**Example**

```javascript
const student = new Map();

student.set(1, "Emin");
student.set(2, "Murat");
student.set(3, "Can");

for ([key, value] of student) {
  // Passing the key variable as an argument to the get() method to access the key parts in the Map.
  console.log(`Elements of the 'student' variable: ${key} ${student.get(key)}`);
}
```

    Elements of the 'student' variable: 1 Emin
    Elements of the 'student' variable: 2 Murat
    Elements of the 'student' variable: 3 Can

### <a id='toc1_2_3_'></a>[`delete()` Method](#toc0_)

Used to delete an element from a Map.

**Örnek**

```javascript
const student = new Map();

student.set(1, "Emin");
student.set(2, "Murat");
student.set(3, "Can");

// Deleting the element with the key value '2' from the Map.
student.delete(2);

for ([key, value] of student) {
  console.log(`Elements of the 'student' variable: ${key} ${student.get(key)}`);
}
```

    Elements of the 'student' variable: 1 Emin
    Elements of the 'student' variable: 3 Can

As seen above, the `delete()` method will find the key corresponding to the argument provided and delete it from the Map.

### <a id='toc1_2_4_'></a>[`has()` Method](#toc0_)

We might want to check whether an element exists in a Map or not. In such cases, we use the `has()` method.

The `has()` method returns a boolean result. If the element is present in the Map, the result is `true`; otherwise, it is `false.

**Example**

```javascript
const student = new Map();

student.set(1, "Emin");
student.set(2, "Murat");
student.set(3, "Can");

// Checking the presence of the element with id '2' in the 'student' variable.
console.log(
  `Result: ${
    student.has(2)
      ? `The element with id '2' is present in the Map. Student's name: ${student.get(
          2
        )}`
      : `The element with id '2' is not present in the Map.`
  }`
);

// Checking the presence of the element with id '4' in the 'student' variable.
console.log(
  `Result: ${
    student.has(4)
      ? `The element with id '4' is present in the Map. Student's name: ${student.get(
          4
        )}`
      : `The element with id '4' is not present in the Map.`
  }`
);
```

    Result: The element with id '2' is present in the Map. Student's name: Murat
    Result: The element with id '4' is not present in the Map.

### <a id='toc1_2_5_'></a>[`forEach()` Method](#toc0_)

With the `forEach()` method, we can automatically perform a specified operation for each element in a Map. This way, we avoid manually processing each element one by one, saving time.

In the `forEach()` method, a method is created, and this method is called and used repeatedly for each Map element. This is referred to as a **callback function**.

**Example**

```javascript
const personal = new Map([
  [1, { name: "Emin", lastName: "Altan", salary: 5000 }],
  [2, { name: "Murat", lastName: "Taş", salary: 6000 }],
  [3, { name: "Sinan", lastName: "Can", salary: 7000 }],
  [4, { name: "Barçın", lastName: "Aktaş", salary: 8000 }],
]);

personal.forEach((value, key) => {
  console.log(
    `Personnel ID: ${key} | Personnel Name: ${
      value.name
    } | Personnel's New Salary: ${value.salary + 1000}$`
  );
});
```

    Personnel ID: 1 | Personnel Name: Emin | Personnel's New Salary: 6000$
    Personnel ID: 2 | Personnel Name: Murat | Personnel's New Salary: 7000$
    Personnel ID: 3 | Personnel Name: Sinan | Personnel's New Salary: 8000$
    Personnel ID: 4 | Personnel Name: Barçın | Personnel's New Salary: 9000$

In the example above, we created a Map named `personal`. We created the values of the Map elements in the form of objects. Using the `forEach()` method, we access the `salary` key of each employee and print the new salary, increased by 1000, along with the personnel details to the console.

### <a id='toc1_2_6_'></a>[`entries()` Method](#toc0_)

Creates an iterable variable for the elements in a Map. Typically used to iterate through elements with constructs like `for...of`.

**Example**

```javascript
const personal = new Map([
  [1, "Emin"],
  [2, "Murat"],
  [3, "Hasan"],
  [4, "Barçın"],
]);

for (const iterator of personal.entries()) {
  console.log(`Personel ID's: ${iterator[0]}`);
  console.log(`Name of Personel: ${iterator[1]}`);
}
```

    Personel ID's: 1
    Name of Personel: Emin
    Personel ID's: 2
    Name of Personel: Murat
    Personel ID's: 3
    Name of Personel: Hasan
    Personel ID's: 4
    Name of Personel: Barçın

In the example above, using the `entries()` method, we copied the elements in the `personal` variable to the `iterator` variable.

1. With the expression `iterator[0]`, we accessed the key part in the key-value pair stored in the `iterator` variable and printed the current stored value to the console.

2. With the expression `iterator[1]`, we accessed the value part in the key-value pair stored in the `iterator` variable and printed the current stored value to the console.

## <a id='toc1_3_'></a>[Summary](#toc0_)

The concept of Map in JavaScript is a powerful data structure that allows us to store key-value pairs. This feature provides a more flexible way of storing and processing data, offering advantages distinct from objects.

Maps differ from objects with features such as the ordering of elements, iterability, and being based on value equality. These characteristics contribute to more effective and reliable data management in specific situations.

Map methods include functionality like adding and deleting elements, checking for their presence, and automatically applying a specific operation for each element. These methods contribute to cleaner, more readable, and performance-oriented code.

The usage of Map in JavaScript is particularly beneficial when dealing with scenarios where multiple values need to be stored, and easy access to these values is necessary. Using Maps for data structures such as student lists or employee information can make our code more organized and efficient.

In conclusion, the Map concept in JavaScript provides a powerful and flexible data structure, simplifying data management in more complex applications and offering advantages to developers.
