# Contents to be covered in this session.

## 1. JavaScript Sorting Arrays.

## 2. JavaScript Loop Methods (map, filter, reduce, forEach, some, every, find).

## 3. JavaScript Math Object.

## 4. JavaScript String.

## 5. JavaScript async and defer attributes.

# JavaScript Sorting Arrays.

In JavaScript, you can sort arrays using the `Array.prototype.sort()` method. By default, this method sorts the elements in the array as strings and in lexicographic (dictionary) order. This means that numbers will not be sorted correctly if you simply use the `sort()` method without any arguments. To perform custom sorting or sorting of numbers, you can pass a comparison function as an argument to `sort()`.

Here's how you can use `sort()` with a custom comparison function:

1. Sorting an array of strings in lexicographic order:

```javascript
const fruits = ["apple", "banana", "cherry", "date"];
fruits.sort(); // Sorts the array in-place
console.log(fruits); // Output: ['apple', 'banana', 'cherry', 'date']
```

2. Sorting an array of numbers in ascending order:

```javascript
const numbers = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5];
numbers.sort((a, b) => a - b); // Sorts the array in-place
console.log(numbers); // Output: [1, 1, 2, 3, 3, 4, 5, 5, 5, 6, 9]
```

3. Sorting an array of numbers in descending order:

```javascript
const numbers = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5];
numbers.sort((a, b) => b - a); // Sorts the array in-place
console.log(numbers); // Output: [9, 6, 5, 5, 5, 4, 3, 3, 2, 1, 1]
```

4. Sorting an array of objects based on a specific property:

```javascript
const persons = [
  { name: "Alice", age: 30 },
  { name: "Bob", age: 25 },
  { name: "Charlie", age: 35 },
];

persons.sort((a, b) => a.age - b.age); // Sorts by age in ascending order
console.log(persons);

/*
Output:
[
  { name: 'Bob', age: 25 },
  { name: 'Alice', age: 30 },
  { name: 'Charlie', age: 35 }
]
*/
```

Remember that the `sort()` method sorts the array in-place, meaning it modifies the original array. If you want to create a sorted copy of the array without modifying the original, you can create a copy of the array and then sort it. For example:

```javascript
const originalArray = [3, 1, 4, 1, 5];
const sortedArray = [...originalArray].sort();
console.log(originalArray); // Original array is unchanged
console.log(sortedArray); // Sorted array
```

# JavaScript Loop Methods (map, filter, reduce, forEach, some, every, find).

JavaScript loop methods such as `map`, `filter`, `reduce`, `forEach`, `some`, `every`, and `find` are powerful tools for manipulating arrays and working with their elements. These methods provide a more declarative and functional approach to working with arrays compared to traditional `for` loops. Here's an overview of each of these methods:

1. **`map`**: The `map` method applies a given function to each element in an array and returns a new array containing the results. It doesn't modify the original array.

   ```javascript
   const numbers = [1, 2, 3, 4, 5];
   const doubled = numbers.map((num) => num * 2);
   // doubled will be [2, 4, 6, 8, 10]
   ```

2. **`filter`**: The `filter` method creates a new array containing all elements from the original array that meet a certain condition specified by a callback function.

   ```javascript
   const numbers = [1, 2, 3, 4, 5];
   const evenNumbers = numbers.filter((num) => num % 2 === 0);
   // evenNumbers will be [2, 4]
   ```

3. **`reduce`**: The `reduce` method allows you to accumulate values from an array into a single value. It takes a callback function that defines how the accumulation is done and an initial value.

   ```javascript
   const numbers = [1, 2, 3, 4, 5];
   const sum = numbers.reduce(
     (accumulator, currentValue) => accumulator + currentValue,
     0
   );
   // sum will be 15
   ```

4. **`forEach`**: The `forEach` method iterates over each element in an array and applies a callback function to each element. It is used for side effects and doesn't return a new array.

   ```javascript
   const numbers = [1, 2, 3, 4, 5];
   numbers.forEach((num) => console.log(num));
   // This will print each number in the array.
   ```

5. **`some`**: The `some` method checks if at least one element in the array satisfies a given condition. It returns `true` if any element matches the condition; otherwise, it returns `false`.

   ```javascript
   const numbers = [1, 2, 3, 4, 5];
   const hasEven = numbers.some((num) => num % 2 === 0);
   // hasEven will be true
   ```

6. **`every`**: The `every` method checks if all elements in the array satisfy a given condition. It returns `true` if all elements match the condition; otherwise, it returns `false`.

   ```javascript
   const numbers = [2, 4, 6, 8, 10];
   const allEven = numbers.every((num) => num % 2 === 0);
   // allEven will be true
   ```

7. **`find`**: The `find` method returns the first element in the array that satisfies a given condition. If no element matches, it returns `undefined`.

   ```javascript
   const numbers = [1, 2, 3, 4, 5];
   const firstEven = numbers.find((num) => num % 2 === 0);
   // firstEven will be 2
   ```

# JavaScript Math Object.

The JavaScript `Math` object provides a collection of built-in mathematical functions and constants that you can use in your JavaScript programs. Here are some commonly used methods and constants from the `Math` object, along with code examples:

1. **Math.PI**: This constant represents the mathematical constant π (pi), which is approximately equal to 3.14159.

```javascript
console.log(Math.PI); // Outputs: 3.141592653589793
```

2. **Math.abs()**: This method returns the absolute value of a number.

```javascript
console.log(Math.abs(-5)); // Outputs: 5
```

3. **Math.round()**: This method rounds a number to the nearest integer.

```javascript
console.log(Math.round(3.7)); // Outputs: 4
console.log(Math.round(3.2)); // Outputs: 3
```

4. **Math.floor()**: This method rounds a number down to the nearest integer.

```javascript
console.log(Math.floor(3.7)); // Outputs: 3
```

5. **Math.ceil()**: This method rounds a number up to the nearest integer.

```javascript
console.log(Math.ceil(3.2)); // Outputs: 4
```

6. **Math.sqrt()**: This method returns the square root of a number.

```javascript
console.log(Math.sqrt(25)); // Outputs: 5
```

7. **Math.pow()**: This method raises a number to a specified power.

```javascript
console.log(Math.pow(2, 3)); // Outputs: 8 (2^3 = 8)
```

8. **Math.random()**: This method returns a random floating-point number between 0 (inclusive) and 1 (exclusive).

```javascript
console.log(Math.random()); // Outputs a random number between 0 and 1
```

To generate random integers within a specific range, you can combine `Math.random()` with other methods like `Math.floor()`:

```javascript
const min = 1;
const max = 10;
const randomInt = Math.floor(Math.random() * (max - min + 1)) + min;
console.log(randomInt); // Outputs a random integer between 1 and 10
```

9. **Math.min()** and **Math.max()**: These methods return the minimum and maximum values from a set of numbers.

```javascript
console.log(Math.min(5, 3, 9, 1)); // Outputs: 1
console.log(Math.max(5, 3, 9, 1)); // Outputs: 9
```

# JavaScript String.

JavaScript provides a `String` data type and a set of built-in methods to work with strings. Strings in JavaScript are sequences of characters and are used to represent text.

Here are some basic operations and methods you can perform with JavaScript strings:

1. **Creating Strings:**
   You can create strings using single quotes, double quotes, or backticks (template literals).

   ```javascript
   let singleQuotedString = "Hello, world!";
   let doubleQuotedString = "Hello, world!";
   let templateLiteralString = `Hello, world!`;
   ```

2. **String Length:**
   You can find the length of a string using the `length` property of a string.

   ```javascript
   let str = "Hello, world!";
   console.log(str.length); // Outputs 13
   ```

3. **String Concatenation:**
   You can concatenate strings using the `+` operator or the `concat` method.

   ```javascript
   let str1 = "Hello";
   let str2 = " world!";
   let result = str1 + str2; // Concatenation using the + operator
   // OR
   let result2 = str1.concat(str2); // Concatenation using the concat method
   ```

4. **Accessing Characters:**
   You can access individual characters in a string using square brackets and zero-based indexing.

   ```javascript
   let str = "Hello, world!";
   console.log(str[0]); // Outputs 'H'
   console.log(str.charAt(7)); // Outputs 'w'
   ```

5. **Substring:**
   You can extract a substring from a string using the `substring`, `slice`, or `substr` methods.

   ```javascript
   let str = "Hello, world!";
   console.log(str.substring(0, 5)); // Outputs 'Hello'
   console.log(str.slice(7, 12)); // Outputs 'world'
   console.log(str.substr(7, 5)); // Outputs 'world'
   ```

6. **Searching and Replacing:**
   You can search for substrings within a string using `indexOf`, `lastIndexOf`, or regular expressions. You can also replace substrings using the `replace` method.

   ```javascript
   let str = "Hello, world!";
   console.log(str.indexOf("world")); // Outputs 7
   console.log(str.replace("world", "there")); // Replaces 'world' with 'there'
   ```

7. **Changing Case:**
   You can change the case of a string using the `toUpperCase` and `toLowerCase` methods.

   ```javascript
   let str = "Hello, world!";
   console.log(str.toUpperCase()); // Outputs 'HELLO, WORLD!'
   console.log(str.toLowerCase()); // Outputs 'hello, world!'
   ```

8. **String Comparison:**
   You can compare strings using comparison operators like `==`, `===`, `<`, `>`, etc. String comparisons are case-sensitive.

   ```javascript
   let str1 = "apple";
   let str2 = "Apple";
   console.log(str1 === str2); // Outputs false
   ```

9. **Template Literals:**
   Template literals (using backticks) allow you to interpolate variables and expressions into strings.

   ```javascript
   let name = "Alice";
   let greeting = `Hello, ${name}!`; // Interpolation
   ```

# JavaScript async and defer attributes.

The `async` and `defer` attributes are used with the `<script>` element in HTML to control how external JavaScript files are loaded and executed in a web page. They help improve the performance and behavior of web pages by influencing the order of script execution and whether it blocks the rendering of the page.

Here's an explanation of each attribute:

1. **`async` Attribute:**

   - When you include the `async` attribute in a `<script>` tag, it tells the browser to load the script asynchronously while not blocking the HTML parsing and rendering process.
   - Asynchronous scripts are downloaded in the background and executed as soon as they are ready, regardless of the order in which they appear in the HTML.
   - This can lead to scripts loading and executing out of order if they depend on each other, potentially causing issues if one script relies on another.
   - Useful for scripts that are not dependent on the page's structure or other scripts and can run independently.

   Example:

   ```html
   <script src="script.js" async></script>
   ```

2. **`defer` Attribute:**

   - The `defer` attribute, like `async`, also allows for asynchronous loading of scripts. However, it differs in behavior:
   - Deferred scripts are downloaded in the background but are executed in the order they appear in the HTML, just before the `DOMContentLoaded` event is fired.
   - This ensures that scripts are executed in the correct order and do not block the rendering of the page.
   - Useful for scripts that need to be executed in a specific order or depend on the page's structure.

   Example:

   ```html
   <script src="script.js" defer></script>
   ```

Usage guidelines:

- If a script does not depend on other scripts or the DOM structure, you can use `async` to load it for potentially faster rendering.

- If you have multiple scripts that rely on each other or need to interact with the DOM, use `defer` to ensure they are executed in order and don't block rendering.

- Scripts without the `async` or `defer` attributes are blocking, meaning they halt the HTML parsing and rendering process until they are downloaded and executed. This can slow down the page load, so it's generally recommended to use `async` or `defer` when appropriate to improve page performance.
