# Contents to be covered in this session.

## 1. JavaScript for in.

## 2. JavaScript for of.

## 3. JavaScript Lexical Environment.

## 4. JavaScript Array Fundamentals.

## 5. JavaScript Properties of Array.

## 6. JavaScript Array Length.

## 7. JavaScript Array Concatenation.

## 8. JavaScript Array Push and Pop.

## 9. JavaScript Array Reverse.

## 10. JavaScript Array Shift and Unshift.

## 11. JavaScript Array toString.

## 12. JavaScript Array Slice and Splice.

## 13. JavaScript Array Join.

## 14. JavaScript Array includes, indexOf, and lastIndexOf.

# JavaScript for in.

In JavaScript, the `for...in` loop is used to iterate over the properties of an object. It allows you to loop through all the enumerable properties of an object, including those inherited from its prototype chain. Here's the basic syntax for the `for...in` loop:

```javascript
for (variable in object) {
  // code to be executed for each property
}
```

- `variable`: A variable that represents the current property name on each iteration.
- `object`: The object whose properties you want to iterate over.

Here's an example of how you can use the `for...in` loop to iterate over the properties of an object:

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
};

for (let key in person) {
  console.log(key + ": " + person[key]);
}
```

In this example, the `for...in` loop iterates over the properties of the `person` object, and on each iteration, it assigns the property name (e.g., `"firstName"`, `"lastName"`, `"age"`) to the `key` variable, which you can then use to access the corresponding property value using `person[key]`.

It's important to note that the `for...in` loop should be used with caution, especially with objects that you didn't create yourself, as it iterates over all enumerable properties, including those inherited from the prototype chain. To avoid unexpected behavior, you can use the `hasOwnProperty` method to check if a property belongs to the object itself or if it's inherited. Here's an example:

```javascript
for (let key in person) {
  if (person.hasOwnProperty(key)) {
    console.log(key + ": " + person[key]);
  }
}
```

# JavaScript for of.

In JavaScript, the `for...of` loop is used to iterate over the values of iterable objects, such as arrays, strings, maps, sets, and more. It provides a simple and concise way to iterate through the elements of an iterable without needing to keep track of indices or keys. Here's the basic syntax of the `for...of` loop:

```javascript
for (const element of iterable) {
  // code to be executed for each element
}
```

Here's how you can use the `for...of` loop with different types of iterables:

1. **Arrays**:

```javascript
const fruits = ["apple", "banana", "cherry"];

for (const fruit of fruits) {
  console.log(fruit);
}
```

2. **Strings** (iterating over characters):

```javascript
const text = "Hello, World!";

for (const char of text) {
  console.log(char);
}
```

3. **Maps** (iterating over key-value pairs):

```javascript
const person = new Map();
person.set("name", "John");
person.set("age", 30);

for (const [key, value] of person) {
  console.log(`${key}: ${value}`);
}
```

4. **Sets**:

```javascript
const colors = new Set(["red", "green", "blue"]);

for (const color of colors) {
  console.log(color);
}
```

5. **Custom Iterables** (you can create your own iterable objects by defining an iterator):

```javascript
const myIterable = {
  [Symbol.iterator]: function* () {
    yield 1;
    yield 2;
    yield 3;
  },
};

for (const value of myIterable) {
  console.log(value);
}
```

# JavaScript Lexical Environment.

A lexical environment is a concept in JavaScript that determines how variables are scoped and accessed within a program. It consists of two main components: the environment record and the outer lexical environment. The environment record is a data structure that stores variable and function declarations, while the outer lexical environment is a reference to the lexical environment in which the current code is defined. Lexical environments are an integral part of JavaScript's scoping and variable lookup rules.

Here's an example to illustrate the concept of a lexical environment:

```javascript
function outer() {
  let outerVar = "I am in the outer function";

  function inner() {
    let innerVar = "I am in the inner function";
    console.log(outerVar); // Accessing outerVar from the outer lexical environment
    console.log(innerVar); // Accessing innerVar from the current lexical environment
  }

  inner();
}

outer();
```

In this example, we have two functions: `outer` and `inner`. Each function creates its own lexical environment:

1. The `outer` function's lexical environment contains a variable `outerVar`.

2. The `inner` function's lexical environment contains a variable `innerVar`.

When we call `inner()` from within the `outer` function, it can access variables from both its own lexical environment and the lexical environment of the containing `outer` function. This is known as lexical scoping or closure.

The `console.log(outerVar)` statement in the `inner` function accesses the `outerVar` variable from the outer lexical environment, and the `console.log(innerVar)` statement accesses the `innerVar` variable from the current lexical environment.

# JavaScript Array Fundamentals.

JavaScript arrays are a fundamental data structure used to store and manipulate collections of values. They are versatile and widely used in web development and other programming tasks. Here are some fundamental concepts and operations related to JavaScript arrays:

1. **Creating Arrays:**
   You can create an array in several ways:

   ```javascript
   // Using square brackets
   const fruits = ["apple", "banana", "cherry"];

   // Using the Array constructor
   const numbers = new Array(1, 2, 3);

   // Creating an empty array
   const emptyArray = [];
   ```

2. **Array Indexing:**
   Arrays are zero-indexed, which means the first element is at index 0, the second at 1, and so on.

   ```javascript
   console.log(fruits[0]); // Output: 'apple'
   console.log(fruits[1]); // Output: 'banana'
   ```

3. **Array Length:**
   You can get the length of an array using the `length` property.

   ```javascript
   console.log(fruits.length); // Output: 3
   ```

4. **Adding and Removing Elements:**
   You can add and remove elements from arrays using methods like `push()`, `pop()`, `unshift()`, and `shift()`.

   - `push()`: Adds elements to the end of an array.
   - `pop()`: Removes the last element from an array.
   - `unshift()`: Adds elements to the beginning of an array.
   - `shift()`: Removes the first element from an array.

   ```javascript
   fruits.push("grape"); // Adds 'grape' to the end
   fruits.pop(); // Removes 'grape'
   fruits.unshift("lemon"); // Adds 'lemon' to the beginning
   fruits.shift(); // Removes 'lemon'
   ```

5. **Iterating Over Arrays:**
   You can loop through array elements using `for` loops, `forEach()`, `for...of` loops, or other methods.

   ```javascript
   for (let i = 0; i < fruits.length; i++) {
     console.log(fruits[i]);
   }

   fruits.forEach((fruit) => {
     console.log(fruit);
   });

   for (const fruit of fruits) {
     console.log(fruit);
   }
   ```

6. **Array Methods:**
   JavaScript provides various methods for manipulating arrays, such as `map()`, `filter()`, `reduce()`, and `slice()`. These methods allow you to perform common operations on arrays efficiently.

   ```javascript
   const numbers = [1, 2, 3, 4, 5];

   const doubled = numbers.map((num) => num * 2); // [2, 4, 6, 8, 10]
   const evenNumbers = numbers.filter((num) => num % 2 === 0); // [2, 4]
   const sum = numbers.reduce((acc, num) => acc + num, 0); // 15
   const sliced = numbers.slice(1, 4); // [2, 3, 4]
   ```

7. **Multidimensional Arrays:**
   Arrays can also be nested to create multidimensional arrays or matrices.

   ```javascript
   const matrix = [
     [1, 2, 3],
     [4, 5, 6],
     [7, 8, 9],
   ];

   console.log(matrix[1][2]); // Accessing element 6
   ```

8. **Common Array Properties and Methods:**
   - `length`: Property to get the number of elements in an array.
   - `concat()`: Combines two or more arrays.
   - `join()`: Joins array elements into a string.
   - `indexOf()` and `lastIndexOf()`: Find the index of an element.
   - `includes()`: Checks if an element exists in an array.
   - `sort()`: Sorts array elements in-place.
   - `reverse()`: Reverses the order of elements in an array.
   - `splice()`: Adds or removes elements from an array at a specified index.
   - `isArray()`: Checks if a value is an array.
   - `every()` and `some()`: Check if all/some elements meet a condition.

# JavaScript Properties of Array.

In JavaScript, arrays are a versatile and commonly used data structure for storing collections of values.

1. **`length`**: This property returns the number of elements in an array, and it can also be used to change the size of an array.

   ```javascript
   const fruits = ["apple", "banana", "cherry"];
   console.log(fruits.length); // Outputs: 3

   fruits.length = 2; // Truncates the array to two elements
   console.log(fruits); // Outputs: ['apple', 'banana']
   ```

2. **`constructor`**: Returns a reference to the constructor function that created the array object.

   ```javascript
   const arr = [1, 2, 3];
   console.log(arr.constructor === Array); // Outputs: true
   ```

3. **`prototype`**: Allows you to add properties and methods to all arrays.

   ```javascript
   Array.prototype.myMethod = function () {
     // Custom array method
   };

   const myArray = [1, 2, 3];
   myArray.myMethod(); // You can now call myMethod on all arrays
   ```

4. **`isArray()`**: A static method that checks whether an object is an array.

   ```javascript
   const arr = [1, 2, 3];
   console.log(Array.isArray(arr)); // Outputs: true
   ```

# JavaScript Array Length.

In JavaScript, the `length` property of an array is used to determine the number of elements in the array. Here's how you can use it:

```javascript
const fruits = ["apple", "banana", "cherry"];

console.log(fruits.length); // Outputs: 3
```

In the example above, `fruits.length` returns `3` because there are three elements in the `fruits` array.
You can also use the `length` property to modify the size of an array. If you set `length` to a value smaller than the current number of elements, it will truncate the array. If you set it to a value larger than the current number of elements, it will increase the size of the array and fill the new slots with `undefined`.
Here's an example:

```javascript
const numbers = [1, 2, 3, 4, 5];

console.log(numbers.length); // Outputs: 5

numbers.length = 3; // Truncate the array to 3 elements
console.log(numbers); // Outputs: [1, 2, 3]

numbers.length = 7; // Increase the array size to 7 elements
console.log(numbers); // Outputs: [1, 2, 3, undefined, undefined, undefined, undefined]
```

# JavaScript Array Concatenation.

Concatenation means combining two or more arrays to create a new array that contains all the elements of the original arrays. Here are some common ways to concatenate arrays in JavaScript:

1. Using the `concat()` method:
   The `concat()` method is a built-in array method that allows you to concatenate one or more arrays with the original array and returns a new array containing the combined elements.

   ```javascript
   const array1 = [1, 2, 3];
   const array2 = [4, 5, 6];
   const concatenatedArray = array1.concat(array2);
   console.log(concatenatedArray); // Output: [1, 2, 3, 4, 5, 6]
   ```

2. Using the spread operator (`...`):
   You can use the spread operator to merge arrays into a new one.

   ```javascript
   const array1 = [1, 2, 3];
   const array2 = [4, 5, 6];
   const concatenatedArray = [...array1, ...array2];
   console.log(concatenatedArray); // Output: [1, 2, 3, 4, 5, 6]
   ```

3. Using the `push()` method:
   You can also use the `push()` method to append the elements of one array to another.

   ```javascript
   const array1 = [1, 2, 3];
   const array2 = [4, 5, 6];
   array1.push(...array2);
   console.log(array1); // Output: [1, 2, 3, 4, 5, 6]
   ```

4. Using the `Array.from()` method:
   You can use the `Array.from()` method to create a new array from an iterable, such as another array, and combine their elements.

   ```javascript
   const array1 = [1, 2, 3];
   const array2 = [4, 5, 6];
   const concatenatedArray = Array.from(array1).concat(array2);
   console.log(concatenatedArray); // Output: [1, 2, 3, 4, 5, 6]
   ```

# JavaScript Array Push and Pop.

In JavaScript, `push` and `pop` are two methods used to manipulate arrays. They allow you to add and remove elements from the end of an array, respectively. Here's an explanation of each:

1. `push()` Method:

   - The `push()` method is used to add one or more elements to the end of an array.
   - It modifies the original array and returns the new length of the array.
   - You can push one or more elements by passing them as arguments to the `push` method.

   Example:

   ```javascript
   let fruits = ["apple", "banana"];
   let newLength = fruits.push("orange", "grape");
   console.log(fruits); // ["apple", "banana", "orange", "grape"]
   console.log(newLength); // 4 (length of the updated array)
   ```

2. `pop()` Method:

   - The `pop()` method is used to remove and return the last element from an array.
   - It modifies the original array by removing the last element and returns the removed element.
   - If the array is empty, `pop()` returns `undefined`.

   Example:

   ```javascript
   let fruits = ["apple", "banana", "orange", "grape"];
   let removedFruit = fruits.pop();
   console.log(fruits); // ["apple", "banana", "orange"]
   console.log(removedFruit); // "grape"
   ```

Here's a summary of how `push` and `pop` work:

- `push()` adds one or more elements to the end of an array and returns the new length of the array.
- `pop()` removes and returns the last element from an array and modifies the array in the process.

# JavaScript Array Reverse.

In JavaScript, you can reverse the elements of an array using the `reverse()` method. The `reverse()` method modifies the original array by reversing the order of its elements in place. Here's how you can use it:

```javascript
const originalArray = [1, 2, 3, 4, 5];
originalArray.reverse();

console.log(originalArray); // Output: [5, 4, 3, 2, 1]
```

As shown in the example above, calling `reverse()` on the `originalArray` reversed its elements.

Keep in mind that the `reverse()` method modifies the original array and does not create a new reversed array. If you want to create a reversed copy of an array without modifying the original, you can use the `slice()` method to first create a shallow copy and then call `reverse()` on the copied array:

```javascript
const originalArray = [1, 2, 3, 4, 5];
const reversedArray = originalArray.slice().reverse();

console.log(originalArray); // Original array is unchanged: [1, 2, 3, 4, 5]
console.log(reversedArray); // Reversed copy: [5, 4, 3, 2, 1]
```

# JavaScript Array Shift and Unshift.

In JavaScript, the `shift()` and `unshift()` methods are used to add and remove elements from the beginning of an array. Here's how they work:

1. `shift()` Method:

   - The `shift()` method removes the first element from an array and returns that removed element.
   - It also updates the array by shifting all the remaining elements one position to the left (i.e., the second element becomes the first, the third becomes the second, and so on).
   - If the array is empty, `shift()` returns `undefined`.

   ```javascript
   const fruits = ["apple", "banana", "cherry"];

   const removedFruit = fruits.shift();

   console.log(removedFruit); // Output: 'apple'
   console.log(fruits); // Output: ['banana', 'cherry']
   ```

2. `unshift()` Method:

   - The `unshift()` method adds one or more elements to the beginning of an array and returns the new length of the array.
   - It modifies the original array by inserting elements at the beginning and shifting the existing elements to accommodate the new ones.

   ```javascript
   const fruits = ["banana", "cherry"];

   const newLength = fruits.unshift("apple", "grape");

   console.log(newLength); // Output: 4
   console.log(fruits); // Output: ['apple', 'grape', 'banana', 'cherry']
   ```

# JavaScript Array toString.

In JavaScript, the `toString()` method is used to convert an array into a string. It returns a string representation of the array's elements separated by commas. Here's the basic syntax for using the `toString()` method:

```javascript
array.toString();
```

Here's an example:

```javascript
var fruits = ["apple", "banana", "cherry"];
var fruitsString = fruits.toString();

console.log(fruitsString); // Output: "apple,banana,cherry"
```

As you can see in the example above, the `toString()` method takes no arguments, and it simply converts the elements of the array into a string with each element separated by a comma.

It's worth noting that `toString()` does not modify the original array; it returns a new string representation of the array's elements. If you want to join the elements of an array with a custom separator, you can use the `join()` method instead.

```javascript
var fruits = ["apple", "banana", "cherry"];
var fruitsString = fruits.join(" and ");

console.log(fruitsString); // Output: "apple and banana and cherry"
```

The `join()` method allows you to specify a custom separator between the elements of the array.

# JavaScript Array Slice and Splice.

JavaScript provides two array methods, `slice()` and `splice()`, which are used for different purposes when working with arrays.

1. `slice()`: This method is used to create a new array by extracting a portion of an existing array. It doesn't modify the original array but returns a new array containing the selected elements.

   Syntax:

   ```javascript
   array.slice(start, end);
   ```

   - `start`: The index at which to begin extraction (inclusive).
   - `end`: The index at which to stop extraction (exclusive).

   Example:

   ```javascript
   const fruits = ["apple", "banana", "cherry", "date", "fig"];
   const slicedFruits = fruits.slice(1, 4); // Returns ["banana", "cherry", "date"]
   ```

2. `splice()`: This method is used to change the contents of an array by removing, replacing, or adding elements to it. It modifies the original array.

   Syntax:

   ```javascript
   array.splice(start, deleteCount, item1, item2, ...);
   ```

   - `start`: The index at which to start changing the array.
   - `deleteCount`: An integer indicating the number of elements in the array to remove from `start`.
   - `item1`, `item2`, ...: Optional items to add to the array at `start`.

   Example:

   ```javascript
   const fruits = ["apple", "banana", "cherry", "date", "fig"];
   fruits.splice(2, 2, "orange", "grape"); // Removes "cherry" and "date", adds "orange" and "grape"
   // fruits is now ["apple", "banana", "orange", "grape", "fig"]
   ```

   You can also use `splice()` to just remove elements from the array without adding any new elements:

   ```javascript
   const fruits = ["apple", "banana", "cherry", "date", "fig"];
   fruits.splice(2, 2); // Removes "cherry" and "date"
   // fruits is now ["apple", "banana", "fig"]
   ```

# JavaScript Array Join.

In JavaScript, the `join()` method is used to join all the elements of an array into a single string and return that string. You can specify a separator string to be used between the elements in the resulting string. If you don't provide a separator, the default separator is a comma (`,`).

Here's the basic syntax of the `join()` method:

```javascript
array.join(separator);
```

- `array`: The array whose elements you want to join into a string.
- `separator` (optional): The string that will be used as a separator between the array elements. If omitted, a comma (`,`) will be used as the default separator.

Here are some examples of how to use the `join()` method:

```javascript
var fruits = ["apple", "banana", "cherry"];

// Using the default separator (comma)
var result1 = fruits.join();
console.log(result1); // Output: "apple,banana,cherry"

// Using a custom separator (hyphen)
var result2 = fruits.join("-");
console.log(result2); // Output: "apple-banana-cherry"

// Using no separator (all elements concatenated)
var result3 = fruits.join("");
console.log(result3); // Output: "applebananacherry"
```

# JavaScript Array includes, indexOf, and lastIndexOf.

In JavaScript, the `Array` object provides several methods for searching for elements within an array, including `includes`, `indexOf`, and `lastIndexOf`. These methods help you determine whether an element exists in an array and find its index if it does. Here's how each of them works:

1. **`includes` Method**:

   - The `includes` method checks if an array includes a specific element and returns a boolean (`true` or `false`) to indicate whether the element is present.
   - It takes one argument, which is the element you want to search for in the array.
   - If the element is found in the array, `includes` returns `true`; otherwise, it returns `false`.
   - It does not provide information about the index of the first occurrence of the element or its last occurrence.

   Example:

   ```javascript
   const array = [1, 2, 3, 4, 5];
   const elementToFind = 3;
   const isElementPresent = array.includes(elementToFind);
   console.log(isElementPresent); // true
   ```

2. **`indexOf` Method**:

   - The `indexOf` method searches for a specific element in an array and returns the index of the first occurrence of that element.
   - It takes one argument, which is the element you want to search for.
   - If the element is found, `indexOf` returns its index (a non-negative integer); otherwise, it returns -1 to indicate that the element is not present in the array.
   - It does not provide information about the last occurrence of the element.

   Example:

   ```javascript
   const array = [1, 2, 3, 4, 5, 3];
   const elementToFind = 3;
   const firstIndex = array.indexOf(elementToFind);
   console.log(firstIndex); // 2 (index of the first occurrence)
   ```

3. **`lastIndexOf` Method**:

   - The `lastIndexOf` method is similar to `indexOf`, but it returns the index of the last occurrence of a specific element in an array.
   - It also takes one argument, which is the element to search for.
   - If the element is found, `lastIndexOf` returns its index (a non-negative integer); otherwise, it returns -1 to indicate that the element is not present in the array.
   - It searches the array from the end to the beginning to find the last occurrence.

   Example:

   ```javascript
   const array = [1, 2, 3, 4, 5, 3];
   const elementToFind = 3;
   const lastIndex = array.lastIndexOf(elementToFind);
   console.log(lastIndex); // 5 (index of the last occurrence)
   ```
