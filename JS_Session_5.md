# Contents to be covered in this session.

## 1. JS Operators Revision

## 2. Operators Precedence

## 3. JS Bitwise Operators

## 4. JS Debugging tools

## 5. JS Logging tools

## 6. JS Debugging using console

## 7. JavaScript Infinite Loops

## 8. JavaScript Error Handling - Try and Catch

# JavaScript Operators Revision

JavaScript operators are symbols or keywords that perform operations on values and variables. There are various types of operators in JavaScript, including arithmetic, assignment, comparison, logical, bitwise, and more. Let's go through these operator types with code examples for each:

1. **Arithmetic Operators:**
   - Addition (+)
   - Subtraction (-)
   - Multiplication (\*)
   - Division (/)
   - Modulus (%)
   - Increment (++)
   - Decrement (--)

```javascript
let a = 10;
let b = 5;

console.log(a + b); // Addition: 15
console.log(a - b); // Subtraction: 5
console.log(a * b); // Multiplication: 50
console.log(a / b); // Division: 2
console.log(a % b); // Modulus: 0

let x = 7;
console.log(x++); // Increment: 7 (then x becomes 8)
console.log(++x); // Increment: 9

let y = 4;
console.log(y--); // Decrement: 4 (then y becomes 3)
console.log(--y); // Decrement: 2
```

2. **Assignment Operators:**
   - Assignment (=)
   - Addition assignment (+=)
   - Subtraction assignment (-=)
   - Multiplication assignment (\*=)
   - Division assignment (/=)
   - Modulus assignment (%=)

```javascript
let num = 10;
num += 5; // num = num + 5
num -= 3; // num = num - 3
num *= 2; // num = num * 2
num /= 4; // num = num / 4
num %= 6; // num = num % 6

console.log(num); // 4
```

3. **Comparison Operators:**
   - Equal to (==)
   - Not equal to (!=)
   - Strict equal to (===)
   - Strict not equal to (!==)
   - Greater than (>)
   - Less than (<)
   - Greater than or equal to (>=)
   - Less than or equal to (<=)

```javascript
let p = 5;
let q = "5";

console.log(p == q); // Equal to: true (loose equality)
console.log(p != q); // Not equal to: false
console.log(p === q); // Strict equal to: false (strict equality)
console.log(p !== q); // Strict not equal to: true
console.log(p > q); // Greater than: false
console.log(p < q); // Less than: false
console.log(p >= q); // Greater than or equal to: true
console.log(p <= q); // Less than or equal to: true
```

4. **Logical Operators:**
   - Logical AND (&&)
   - Logical OR (||)
   - Logical NOT (!)

```javascript
let isLoggedIn = true;
let isAdmin = false;

console.log(isLoggedIn && isAdmin); // Logical AND: false
console.log(isLoggedIn || isAdmin); // Logical OR: true
console.log(!isLoggedIn); // Logical NOT: false
```

5. **Bitwise Operators:**
   - Bitwise AND (&)
   - Bitwise OR (|)
   - Bitwise XOR (^)
   - Bitwise NOT (~)
   - Left shift (<<)
   - Right shift (>>)
   - Zero-fill right shift (>>>)

```javascript
let x = 5; // Binary representation: 0101
let y = 3; // Binary representation: 0011

console.log(x & y); // Bitwise AND: 1 (binary 0001)
console.log(x | y); // Bitwise OR: 7 (binary 0111)
console.log(x ^ y); // Bitwise XOR: 6 (binary 0110)
console.log(~x); // Bitwise NOT: -6 (binary 11111010 in 2's complement)
console.log(x << 1); // Left shift by 1: 10 (binary 1010)
console.log(x >> 1); // Right shift by 1: 2 (binary 0010)
console.log(x >>> 1); // Zero-fill right shift by 1: 2 (binary 0010)
```

# JavaScript Operators Precedence

JavaScript, like many programming languages, has operator precedence rules that determine the order in which operators are evaluated in expressions. Here's a detailed explanation of operator precedence in JavaScript with code examples:

1. **Grouping `()`**: Parentheses have the highest precedence and are used to force a particular evaluation order.

   ```javascript
   let result = (2 + 3) * 4; // result will be 20
   ```

2. **Exponentiation `**`\*\*: The exponentiation operator raises the left operand to the power of the right operand.

   ```javascript
   let result = 2 ** 3; // result will be 8
   ```

3. **Multiplication `*`, Division `/`, Remainder `%`**: These arithmetic operators have the same precedence and are evaluated from left to right.

   ```javascript
   let result = (10 / 2) * 3; // result will be 15
   ```

4. **Addition `+` and Subtraction `-`**: Similarly, addition and subtraction operators have the same precedence and are evaluated from left to right.

   ```javascript
   let result = 5 + 3 - 2; // result will be 6
   ```

5. **Comparison Operators**: These operators compare two values and return a Boolean result. They have lower precedence than arithmetic operators.

   ```javascript
   let x = 10;
   let y = 5;
   let result = x > y; // result will be true
   ```

6. **Logical Operators**: Logical operators include `&&` (logical AND), `||` (logical OR), and `!` (logical NOT). They have lower precedence than comparison operators.

   ```javascript
   let a = true;
   let b = false;
   let result = a && b; // result will be false
   ```

7. **Conditional (Ternary) Operator `? :`**: The ternary operator allows for conditional expressions.

   ```javascript
   let x = 5;
   let result = x > 0 ? "Positive" : "Negative"; // result will be "Positive"
   ```

8. **Assignment Operators**: Assignment operators, such as `=`, `+=`, `-=` have lower precedence. They are used to assign values to variables.

   ```javascript
   let x = 5;
   x += 2; // x is now 7
   ```

9. **Comma `,` Operator**: The comma operator evaluates two expressions from left to right and returns the result of the second expression.

   ```javascript
   let a = (1, 2, 3); // a is assigned 3 (the result of the last expression)
   ```

10. **Bitwise Operators**: JavaScript also includes bitwise operators (`&`, `|`, `^`, `<<`, `>>`, `>>>`), but they are used less frequently and have lower precedence than most other operators.

```javascript
let x = 5 & 3; // Bitwise AND: x is 1
```

# JavaScript Bitwise Operators

JavaScript provides several bitwise operators that manipulate the individual bits of integer values. These operators are rarely used in everyday programming but can be helpful in certain low-level operations. Here are JavaScript's bitwise operators with code examples:

1. **Bitwise AND (`&`)**: Performs a bitwise AND operation on each pair of corresponding bits.

   ```javascript
   let a = 5; // Binary: 0101
   let b = 3; // Binary: 0011
   let result = a & b; // Binary result: 0001 (Decimal: 1)
   ```

2. **Bitwise OR (`|`)**: Performs a bitwise OR operation on each pair of corresponding bits.

   ```javascript
   let a = 5; // Binary: 0101
   let b = 3; // Binary: 0011
   let result = a | b; // Binary result: 0111 (Decimal: 7)
   ```

3. **Bitwise XOR (`^`)**: Performs a bitwise XOR (exclusive OR) operation on each pair of corresponding bits.

   ```javascript
   let a = 5; // Binary: 0101
   let b = 3; // Binary: 0011
   let result = a ^ b; // Binary result: 0110 (Decimal: 6)
   ```

4. **Bitwise NOT (`~`)**: Inverts all the bits of the operand, changing 0s to 1s and 1s to 0s. It operates on a single operand.

   ```javascript
   let a = 5; // Binary: 0101
   let result = ~a; // Binary result: 1010 (Decimal: -6)
   ```

   Note: The result is a signed 2's complement representation in JavaScript, which may appear as a negative number.

5. **Left Shift (`<<`)**: Shifts the bits of the left operand to the left by a specified number of positions, filling in with zeros.

   ```javascript
   let a = 5; // Binary: 0101
   let result = a << 2; // Binary result: 010100 (Decimal: 20)
   ```

6. **Sign-propagating Right Shift (`>>`)**: Shifts the bits of the left operand to the right by a specified number of positions, filling in with the sign bit (the leftmost bit).

   ```javascript
   let a = -5; // Binary: 11111111111111111111111111111011 (32-bit representation)
   let result = a >> 2; // Binary result: 11111111111111111111111111111110 (Decimal: -2)
   ```

7. **Zero-fill Right Shift (`>>>`)**: Shifts the bits of the left operand to the right by a specified number of positions, filling in with zeros.

   ```javascript
   let a = -5; // Binary: 11111111111111111111111111111011 (32-bit representation)
   let result = a >>> 2; // Binary result: 00111111111111111111111111111110 (Decimal: 1073741822)
   ```

# JavaScript Debugging Tools

JavaScript debugging is a crucial part of the development process to find and fix issues in your code. There are various tools and techniques available for debugging JavaScript. In this response, I'll detail some of the commonly used JavaScript debugging tools and provide short examples of how to use them.

1. **Console.log()**

   The simplest and most basic way to debug JavaScript is by using `console.log()` to print values, variables, or messages to the browser console.

   ```javascript
   let num1 = 5;
   let num2 = 10;
   console.log(num1 + num2); // Prints 15 to the console
   ```

2. **Browser Developer Tools**

   Most modern web browsers come with built-in developer tools that include a JavaScript debugger. You can set breakpoints, inspect variables, and step through your code line by line.

   - **Chrome DevTools Example:**

     1. Open Chrome DevTools (F12 or right-click and select "Inspect").
     2. Go to the "Sources" tab.
     3. Find your JavaScript file, set breakpoints by clicking on line numbers, and then refresh your page to trigger the debugger.

3. **Debugger Statement**

   You can use the `debugger` statement to pause the execution of your code and open the browser's developer tools.

   ```javascript
   function someFunction() {
     debugger;
     // Your code here
   }
   ```

4. **JavaScript Linters**

   Tools like ESLint or JSHint can help catch common coding mistakes and potential issues before you even run your code.

5. **Visual Studio Code Debugger**

   If you're using Visual Studio Code as your code editor, you can use its built-in debugger by setting breakpoints and launching your application in debug mode.

6. **Online Editors with Debugging Support**

   Some online code editors like CodePen and JSFiddle have built-in debugging capabilities that allow you to see console output and errors easily.

Here's a short example of using breakpoints in Chrome DevTools:

```javascript
function calculateTotal(price, quantity) {
  let total = price * quantity;
  debugger; // Set a breakpoint here
  return total;
}

let itemPrice = 20;
let itemQuantity = 3;

let result = calculateTotal(itemPrice, itemQuantity);

console.log(`Total cost: $${result}`);
```

# JavaScript Logging Tools

JavaScript logging tools are essential for debugging and monitoring applications. They allow developers to track the flow of their code, identify errors, and gain insights into how their applications behave. Here are some popular JavaScript logging tools in detail, along with short examples for each:

1. **console.log()**

   - The most basic logging tool in JavaScript, available in all browsers.
   - Outputs messages to the console.

   ```javascript
   console.log("Hello, world!");
   ```

2. **console.debug()**

   - Similar to `console.log()`, but intended for debugging purposes.

   ```javascript
   console.debug("Debugging message");
   ```

3. **console.info()**

   - Used for informational messages.

   ```javascript
   console.info("Informational message");
   ```

4. **console.warn()**

   - Logs warnings, often displayed in yellow in the console.

   ```javascript
   console.warn("This is a warning!");
   ```

5. **console.error()**

   - Logs errors, often displayed in red in the console.

   ```javascript
   console.error("This is an error!");
   ```

6. **Custom Logging Function**

   - You can create your own custom logging function for more advanced logging and to centralize your logging logic.

   ```javascript
   function customLogger(level, message) {
     const logEntry = `[${level}] ${message}`;
     console.log(logEntry);
   }

   customLogger("INFO", "Custom info message");
   ```

7. **Log Levels with loglevel Library**

   - The `loglevel` library allows you to define log levels and control the verbosity of your logs.

   ```javascript
   import log from "loglevel";

   log.setLevel(log.levels.DEBUG);

   log.debug("Debug message");
   log.info("Info message");
   log.warn("Warning message");
   log.error("Error message");
   ```

8. **Winston Logger (Node.js)**

   - Winston is a popular logging library for Node.js applications.

   ```javascript
   const winston = require("winston");

   const logger = winston.createLogger({
     level: "info",
     format: winston.format.json(),
     transports: [
       new winston.transports.Console(),
       new winston.transports.File({ filename: "error.log", level: "error" }),
     ],
   });

   logger.info("Info message");
   logger.warn("Warning message");
   logger.error("Error message");
   ```

9. **Bunyan Logger (Node.js)**

   - Bunyan is another logging library for Node.js known for its structured logging.

   ```javascript
   const bunyan = require("bunyan");

   const logger = bunyan.createLogger({ name: "myapp" });

   logger.info("Info message");
   logger.warn("Warning message");
   logger.error("Error message");
   ```

10. **Pino Logger (Node.js)**
    - Pino is a lightweight and extremely fast Node.js logger.

```javascript
const pino = require("pino")();

pino.info("Info message");
pino.warn("Warning message");
pino.error("Error message");
```

# JavaScript Debugging using console

Debugging JavaScript using the console is a fundamental skill for web developers. The console allows you to output information, inspect variables, and catch errors. Here are some common debugging techniques using the console, along with code examples:

1. **Printing Debug Information**:

   Use `console.log()` to print variables, values, or messages to the console.

   ```javascript
   let name = "John";
   console.log("Hello, " + name); // Output: Hello, John
   ```

2. **Inspecting Variables**:

   You can use `console.log()` to inspect the values of variables and objects at specific points in your code.

   ```javascript
   let user = { name: "Alice", age: 30 };
   console.log(user); // Output: { name: "Alice", age: 30 }
   ```

3. **Console Grouping**:

   Group related log statements together using `console.group()` and `console.groupEnd()` to create a more organized log.

   ```javascript
   console.group("User Details");
   console.log("Name: Alice");
   console.log("Age: 30");
   console.groupEnd();
   ```

4. **Conditional Logging**:

   Use `console.assert()` to log a message if a given condition is false.

   ```javascript
   let isLoggedIn = false;
   console.assert(isLoggedIn, "User is not logged in");
   ```

5. **Counting**:

   Count occurrences of a specific log message using `console.count()`.

   ```javascript
   for (let i = 0; i < 5; i++) {
     console.count("Loop Iteration");
   }
   ```

6. **Timing**:

   Measure the time taken by a block of code using `console.time()` and `console.timeEnd()`.

   ```javascript
   console.time("MyTimer");
   // Code to measure
   console.timeEnd("MyTimer"); // Outputs the time taken
   ```

7. **Error Handling**:

   Use `console.error()` to log errors along with a message.

   ```javascript
   try {
     // Some code that may throw an error
   } catch (error) {
     console.error("An error occurred:", error);
   }
   ```

8. **Stack Tracing**:

   Print a stack trace of the current location in your code using `console.trace()`.

   ```javascript
   function foo() {
     console.trace("Trace this");
   }
   foo();
   ```

9. **Clearing the Console**:

   Use `console.clear()` to clear the console.

   ```javascript
   console.clear();
   ```

# JavaScript Infinite Loops

An infinite loop is a loop that continues to execute indefinitely because the loop condition is always true. Infinite loops are generally considered errors in programming because they can cause your program to hang or crash. However, in some cases, you might intentionally create an infinite loop for specific purposes, such as running a server or a game loop.

Here are some examples of infinite loops in JavaScript, both unintentional and intentional:

1. Unintentional Infinite Loop:

   This code creates an unintentional infinite loop because the loop condition (`while (true)`) is always true, and there is no way to exit the loop. It will run indefinitely and may freeze your browser or application.

   ```javascript
   while (true) {
     // This code will run forever
   }
   ```

2. Infinite Loop with Break Statement:

   In this example, we create an infinite loop intentionally, but we provide a way to exit the loop using the `break` statement when a certain condition is met.

   ```javascript
   let count = 0;
   while (true) {
     console.log("Loop iteration: " + count);
     count++;
     if (count >= 10) {
       break; // Exit the loop when count reaches 10
     }
   }
   ```

3. Infinite Loop Using a For Loop:

   You can create an infinite loop using a `for` loop with a condition that is always true.

   ```javascript
   for (;;) {
     // This is an infinite loop
   }
   ```

4. Infinite Loop with setInterval():

   You can also create an infinite loop using the `setInterval()` function, which repeatedly executes a function at a specified interval.

   ```javascript
   setInterval(function () {
     console.log("This will run repeatedly.");
   }, 1000); // Executes the function every 1000 milliseconds (1 second)
   ```

5. Recursive Infinite Loop:

   Recursive functions can also lead to infinite loops if there is no base case to stop the recursion.

   ```javascript
   function infiniteRecursiveLoop() {
     console.log("This will run indefinitely.");
     infiniteRecursiveLoop(); // Recursive call without a base case
   }
   infiniteRecursiveLoop();
   ```

# JavaScript Error Handling - Try and Catch

In JavaScript, error handling is typically done using the `try...catch` statement. This allows you to write code that attempts to execute some potentially problematic code within the `try` block and then gracefully handle any errors that occur in the `catch` block. Here's a basic example:

```javascript
try {
  // Code that might cause an error
  const result = someUndefinedVariable * 2;
  console.log(result);
} catch (error) {
  // Handle the error
  console.error("An error occurred:", error.message);
}
```

In this example, the `try` block contains code that attempts to multiply an undefined variable by 2, which will result in a runtime error. When the error occurs, the code inside the `catch` block is executed. The `catch` block receives the error object as a parameter, and you can access properties like `message` to get more information about the error.

Here are a few more examples demonstrating different types of errors and error handling scenarios:

1. **Handling Specific Errors**:

```javascript
try {
  // Code that might cause an error
  const value = null;
  JSON.parse(value); // This will throw a SyntaxError
} catch (error) {
  if (error instanceof SyntaxError) {
    console.error("SyntaxError occurred:", error.message);
  } else {
    console.error("An error occurred:", error.message);
  }
}
```

2. **Using `finally`**: The `finally` block is executed regardless of whether an error occurred or not.

```javascript
try {
  // Code that might cause an error
  const result = someUndefinedVariable * 2;
  console.log(result);
} catch (error) {
  // Handle the error
  console.error("An error occurred:", error.message);
} finally {
  // This block is always executed
  console.log("Execution finished.");
}
```

3. **Throwing Custom Errors**:

```javascript
function divide(a, b) {
  if (b === 0) {
    throw new Error("Division by zero is not allowed.");
  }
  return a / b;
}

try {
  const result = divide(10, 0);
  console.log(result);
} catch (error) {
  console.error("An error occurred:", error.message);
}
```
