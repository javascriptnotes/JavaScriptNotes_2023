# Contents to be covered in this session.

## 1. JavaScript Introduction

## 2. JavaScript Basics

## 3. JavaScript Variables

## 4. JavaScript Constants

## 5. JavaScript Primitive Types

## 6. JavaScript Type Coercion

## 7. More Examples on JavaScript Type Coercion

# JavaScript Introduction

JavaScript is a versatile and widely used programming language primarily used for front-end web development. It allows developers to create interactive and dynamic web pages by adding functionality and interactivity to websites. Here's a brief introduction to JavaScript:

## History

JavaScript was created by Brendan Eich in 1995 while he was working at Netscape Communications Corporation. It was initially called "Mocha" and later renamed to "LiveScript" before settling on "JavaScript" to capitalize on the popularity of Java. Despite the name similarity, JavaScript and Java are entirely different languages.

## Purpose

JavaScript is primarily used for front-end web development to enhance the user experience by making web pages interactive and responsive. However, it's also used on the server-side (Node.js) and for mobile app development (React Native, NativeScript).

## Key Features

- **Interactivity:** JavaScript allows you to add interactive features to web pages. For example, you can create forms that validate user input, add sliders, create games, and more.
- **DOM Manipulation:** JavaScript can manipulate the Document Object Model (DOM) of a web page, which represents the page's structure. This allows you to dynamically change HTML and CSS, update content, and respond to user actions.
- **Event Handling:** JavaScript enables you to respond to user actions like clicks, keyboard input, and mouse movements by defining event handlers.
- **Asynchronous Programming:** JavaScript supports asynchronous operations, allowing you to make network requests, load resources, and perform other tasks without blocking the main thread.
- **Cross-Browser Compatibility:** Modern JavaScript is designed to work consistently across different web browsers, making it a reliable choice for web development.

## Syntax

JavaScript has a C-style syntax and is an interpreted language. It's often embedded directly within HTML documents using `<script>` tags or included from external script files.

```javascript
// Example JavaScript code
function greet(name) {
  return "Hello, " + name + "!";
}
```

# JavaScript Basics

JavaScript is a versatile programming language commonly used for web development. It adds interactivity and dynamic behavior to web pages. Here are some fundamental concepts:

## Variables

Variables are used to store data. In JavaScript, you can use `let` and `const` to declare variables.

```javascript
// Declare a variable
let age = 25;

// Variables can change values
age = 30;

// Constants cannot be reassigned
const pi = 3.14;
```

## Data Types

JavaScript has several data types:

- **Numbers:** Representing numeric values.
- **Strings:** Representing text.
- **Booleans:** Representing true or false values.
- **Arrays:** Ordered collections of values.
- **Objects:** Unordered collections of key-value pairs.

```javascript
let name = "John";
let age = 30;
let isStudent = true;
let colors = ["red", "green", "blue"];
let person = { firstName: "John", lastName: "Doe" };
```

## Operators

Operators are used to perform operations on variables and values.

```javascript
let x = 5;
let y = 3;

// Arithmetic operators
let sum = x + y;
let product = x * y;

// Comparison operators
let isEqual = x === y;
let isGreater = x > y;

// Logical operators
let andResult = true && false;
let orResult = true || false;
```

## Conditional Statements

Conditional statements allow you to make decisions in your code based on conditions.

```javascript
let grade = 85;

if (grade >= 90) {
  console.log("A");
} else if (grade >= 80) {
  console.log("B");
} else {
  console.log("C");
}
```

## Loops

Loops are used to repeat actions in your code.

### For Loop

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

### While Loop

```javascript
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```

## Functions

Functions are reusable blocks of code that can be called with different arguments.

```javascript
function greet(name) {
  return "Hello, " + name + "!";
}

let message = greet("Alice");
console.log(message);
```

## Events and Event Handling

Events allow you to respond to user interactions with your web page.

```javascript
// HTML button: <button id="myButton">Click me</button>

let button = document.getElementById("myButton");

button.addEventListener("click", function () {
  alert("Button clicked!");
});
```

## DOM Manipulation

The Document Object Model (DOM) represents the structure of a web page and can be manipulated with JavaScript.

```javascript
// HTML: <p id="myPara">This is a paragraph.</p>

let paragraph = document.getElementById("myPara");
paragraph.textContent = "Updated text"; // Change text content
paragraph.style.color = "blue"; // Change CSS styles
```

## JavaScript in HTML

You can include JavaScript directly in your HTML documents.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>JavaScript Example</title>
  </head>
  <body>
    <h1>JavaScript Example</h1>
    <button id="myButton">Click me</button>

    <script>
      let button = document.getElementById("myButton");

      button.addEventListener("click", function () {
        alert("Button clicked!");
      });
    </script>
  </body>
</html>
```

# JavaScript Variables

In JavaScript, variables are used to store and manage data. You can think of them as containers that hold values or references to values. Here are some key points to understand about JavaScript variables:

1. **Declaring Variables**: You declare variables using the `var`, `let`, or `const` keyword.

   - `var`: Variables declared with `var` have function-level scope, meaning they are only scoped to the function in which they are declared or, if declared outside any function, they have global scope. However, `var` declarations are not block-scoped.

   - `let`: Variables declared with `let` have block-level scope, meaning they are scoped to the nearest enclosing curly braces (`{}`), whether that's a function, loop, or any block. `let` is a preferred choice for variable declaration in modern JavaScript.

   - `const`: Variables declared with `const` are also block-scoped, like `let`. However, `const` variables must be assigned a value when declared and cannot be reassigned after that. This makes `const` suitable for defining constants or values that should not change.

   Example:

   ```javascript
   var name = "John";
   let age = 30;
   const pi = 3.14;
   ```

2. **Variable Naming**: Variable names (identifiers) must follow certain rules:

   - They can contain letters, digits, underscores, or dollar signs.
   - The first character must be a letter, underscore (\_), or dollar sign ($).
   - Variable names are case-sensitive (`age` is different from `Age`).

   Valid variable names: `myVar`, `_privateVar`, `myVar2`, `$price`.
   Invalid variable names: `2myVar`, `my-Var`, `my Var`.

3. **Assigning Values**: You can assign values to variables using the `=` operator.

   ```javascript
   let x = 10;
   let message = "Hello, World!";
   ```

4. **Data Types**: JavaScript is a dynamically-typed language, which means variables can change their data type during runtime. Common data types include numbers, strings, booleans, objects, arrays, and more.

   ```javascript
   let num = 42; // Number
   let name = "Alice"; // String
   let isTrue = true; // Boolean
   let fruits = ["apple", "banana"]; // Array
   let person = {
     // Object
     name: "John",
     age: 30,
   };
   ```

5. **Reassigning Variables**: Variables declared with `var` and `let` can be reassigned.

   ```javascript
   let score = 50;
   score = 75; // Reassignment is allowed
   ```

6. **Constants**: Variables declared with `const` cannot be reassigned once they have been assigned a value.

   ```javascript
   const pi = 3.14;
   pi = 3.14159; // This will result in an error
   ```

7. **Hoisting**: In JavaScript, variable declarations using `var` are hoisted to the top of their containing function or global scope. This means you can use a variable before it's declared, but it will have an initial value of `undefined`. Variables declared with `let` and `const` are also hoisted but are not initialized until the actual declaration in the code.

   ```javascript
   console.log(x); // Outputs: undefined
   var x = 10;
   ```

8. **Scope**: Variables declared with `var` have function scope, whereas variables declared with `let` and `const` have block scope.

   ```javascript
   function example() {
     var localVar = "I am a local variable";
     if (true) {
       let blockVar = "I am a block-scoped variable";
     }
     // localVar is accessible here
     // blockVar is not accessible here
   }
   ```

# JavaScript Constants

In JavaScript, constants are declared using the `const` keyword. Constants are variables that cannot be reassigned after they are initially assigned a value. This makes them useful for defining values that should remain constant throughout your code, such as mathematical constants, configuration settings, or any value that should not change during the execution of your program.

Here's how you declare and use constants in JavaScript:

```javascript
const PI = 3.14159;
const MAX_WIDTH = 800;

console.log(PI); // Outputs: 3.14159
console.log(MAX_WIDTH); // Outputs: 800
```

Key points to note about JavaScript constants:

1. **Immutability**: Once a value is assigned to a constant, you cannot change that value by reassigning it. Attempting to do so will result in an error.

   ```javascript
   const age = 30;
   age = 31; // This will result in an error
   ```

2. **Block Scope**: Like variables declared with `let`, constants declared with `const` are block-scoped. They are only accessible within the block where they are defined.

   ```javascript
   if (true) {
     const blockScopedConstant = "I am block-scoped";
   }
   // blockScopedConstant is not accessible here
   ```

3. **Initialization**: Constants must be initialized when they are declared. Unlike variables declared with `var`, they cannot be declared without an initial value.

   ```javascript
   const name; // This will result in an error
   ```

4. **Naming Convention**: It is common practice to use uppercase letters and underscores to name constants in JavaScript. This helps differentiate them from regular variables and makes it clear that their value should not change.

   ```javascript
   const TAX_RATE = 0.08;
   const API_KEY = "your-api-key-here";
   ```

5. **Use Cases**: Constants are often used for:
   - Mathematical constants like `PI` or `E`.
   - Configuration settings that should not change during program execution.
   - Values that are shared across multiple parts of your code and should remain consistent.
   - Enumerations or predefined lists of values.

```javascript
const COLORS = {
  RED: "red",
  GREEN: "green",
  BLUE: "blue",
};
```

# JavaScript Primitive Types

JavaScript has several primitive data types, which are the most basic data types in the language. These primitive types represent single values and are immutable, meaning they cannot be changed once they are created. Here are the primary JavaScript primitive data types:

1. **Number**: The `number` type represents both integer and floating-point numbers. JavaScript does not distinguish between them, and all numbers are represented as 64-bit floating-point numbers (similar to the `double` type in some other programming languages).

   ```javascript
   let integerNumber = 42;
   let floatingPointNumber = 3.14159;
   ```

2. **String**: The `string` type represents text data enclosed in single (' '), double (" "), or backticks (\` \`) quotes. Strings are used to store and manipulate sequences of characters.

   ```javascript
   let firstName = "John";
   let lastName = "Doe";
   let fullName = `John ${lastName}`;
   ```

3. **Boolean**: The `boolean` type represents true or false values, which are often used in conditional statements and logical operations.

   ```javascript
   let isStudent = true;
   let isWorking = false;
   ```

4. **Undefined**: The `undefined` type has only one value, which is `undefined`. It represents a variable that has been declared but has not been assigned a value.

   ```javascript
   let uninitializedVariable;
   console.log(uninitializedVariable); // Outputs: undefined
   ```

5. **Null**: The `null` type has only one value, which is `null`. It represents the intentional absence of any object value or no value at all.

   ```javascript
   let emptyValue = null;
   ```

6. **Symbol** (ES6 and later): Symbols are unique and immutable values, often used as property keys in objects to ensure that they are unique.

   ```javascript
   const uniqueSymbol = Symbol("description");
   ```

7. **BigInt** (ES11 and later): BigInt is used for representing large integers that exceed the maximum safe integer value supported by the `number` type.

   ```javascript
   const bigIntValue = 1234567890123456789012345678901234567890n;
   ```

# JavaScript Type Coercion

JavaScript uses type coercion to automatically convert values from one data type to another in certain situations. Type coercion can be a powerful feature, but it can also lead to unexpected behavior if you're not aware of how it works. Here are some key points about JavaScript-type coercion:

1. **Implicit Type Coercion**: This occurs when JavaScript automatically converts values from one type to another without explicit instructions from the developer. It typically happens in the following situations:

   - **Concatenation of Strings and Other Types**: When you use the `+` operator with strings and non-string values, JavaScript converts non-string values to strings and concatenates them.

     ```javascript
     let num = 42;
     let str = "The answer is: " + num; // Implicit coercion to string
     ```

   - **Comparison Operators**: JavaScript will attempt to convert values to a common type when using comparison operators (`==` and `===`). This can lead to unexpected results.

     ```javascript
     5 == "5"; // true (implicit conversion to compare)
     5 === "5"; // false (strict comparison, no conversion)
     ```

2. **Explicit Type Conversion**: Developers can also perform explicit type conversions using functions or operators to ensure that values are of the desired type.

   - **`parseInt` and `parseFloat`**: These functions are used to parse strings and convert them to numbers.

     ```javascript
     let numStr = "42";
     let num = parseInt(numStr);
     ```

   - **`Number`, `String`, and `Boolean` Functions**: These functions can be used to explicitly convert values to numbers, strings, or booleans.

     ```javascript
     let str = String(123); // Explicitly convert to string
     let bool = Boolean(0); // Explicitly convert to boolean
     ```

   - **Using the `+` Operator for Type Conversion**: You can use the unary `+` operator to explicitly convert a value to a number.

     ```javascript
     let strNum = "42";
     let num = +strNum;
     ```

3. **Falsy and Truthy Values**: JavaScript has a concept of falsy and truthy values, which are values that are treated as either false or true in a boolean context. This can affect type coercion.

   - Falsy values: `false`, `0`, `""` (empty string), `null`, `undefined`, and `NaN`.
   - Truthy values: All other values, including non-empty strings, non-zero numbers, and objects.

   ```javascript
   if ("hello") {
     // This block will execute because "hello" is truthy
   }
   ```

4. **Prefer Explicit Over Implicit Coercion**: To avoid unexpected behavior and make your code more readable, it's generally recommended to use explicit type conversion when necessary rather than relying on implicit coercion. This can make your intentions clear and reduce the chances of bugs.

# More Examples on JavaScript Type Coercion

JavaScript coercion can sometimes lead to unexpected behavior if you're not aware of how it works. Here are some examples that demonstrate different scenarios of type coercion in JavaScript:

1. **Coercion in Arithmetic Operations**:

   ```javascript
   let num = 5;
   let str = "10";

   let result = num + str; // Implicit coercion to string
   console.log(result); // Outputs "510" (string concatenation)
   ```

2. **Comparison with Loose Equality (`==`)**:

   ```javascript
   let num = 5;
   let str = "5";

   console.log(num == str); // true (implicit conversion)
   ```

   In this example, JavaScript converts the string `"5"` to a number for comparison, and they are considered equal.

3. **Comparison with Strict Equality (`===`)**:

   ```javascript
   let num = 5;
   let str = "5";

   console.log(num === str); // false (no type coercion)
   ```

   With strict equality, JavaScript does not perform type coercion, so the comparison returns `false`.

4. **Falsy and Truthy Values in Conditional Statements**:

   ```javascript
   let value = 0;
   if (value) {
     console.log("Truthy");
   } else {
     console.log("Falsy");
   }
   ```

   In this case, `0` is a falsy value, so the "Falsy" message is printed. JavaScript implicitly coerces `0` to `false` in a boolean context.

5. **Explicit Type Conversion**:

   ```javascript
   let numStr = "42";
   let num = parseInt(numStr); // Explicitly converting to a number
   console.log(num); // Outputs 42
   ```

   Here, we use `parseInt` to explicitly convert the string `"42"` to a number.

6. **Using the `+` Operator for Type Conversion**:

   ```javascript
   let strNum = "42";
   let num = +strNum; // Explicitly converting to a number
   console.log(num); // Outputs 42
   ```

   The unary `+` operator is used for explicit type conversion from a string to a number.

7. **Concatenation with Non-Strings**:

   ```javascript
   let greeting = "Hello, ";
   let number = 42;

   let message = greeting + number; // Implicit coercion to string
   console.log(message); // Outputs "Hello, 42"
   ```

   JavaScript implicitly coerces the number `42` to a string and concatenates it with the greeting.

It's important to be aware of these scenarios to write JavaScript code that behaves as expected. While type coercion can be useful in some cases, it can also lead to bugs if not used carefully. To avoid unexpected behavior, consider using strict equality (`===`) for comparisons and explicit type conversion when necessary to make your code more predictable and readable.
