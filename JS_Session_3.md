# Contents to be covered in this session.

## 1. JavaScript ParseInt and ParseFloat

## 2. JavaScript return Keyword

## 3. JavaScript Operators

## 4. JavaScript Ternary Operator

# JavaScript ParseInt and ParseFloat

`parseInt` and `parseFloat` are two JavaScript functions used for parsing strings into numbers. They are commonly used when you have a string containing numeric data, and you want to convert it into a numeric type (integer or floating-point number) for mathematical operations or comparisons.

Here's how `parseInt` and `parseFloat` work:

1. **parseInt**:

   - `parseInt` is used to convert a string into an integer (whole number).
   - It takes two arguments: the string to be parsed and an optional `radix` (base) specifying the numeral system to be used (default is base 10).

   ```javascript
   let num = parseInt("42"); // Parses "42" as a base-10 integer
   console.log(num); // Outputs 42
   ```

   - If the string starts with "0x," it's parsed as a hexadecimal number.

   ```javascript
   let hexNum = parseInt("0xFF"); // Parses "0xFF" as a hexadecimal number
   console.log(hexNum); // Outputs 255
   ```

2. **parseFloat**:

   - `parseFloat` is used to convert a string into a floating-point number (decimal number).
   - It parses the string until it encounters a character that is not a valid part of a floating-point number.

   ```javascript
   let num = parseFloat("3.14"); // Parses "3.14" as a floating-point number
   console.log(num); // Outputs 3.14
   ```

   - `parseFloat` does not support specifying a `radix` because it always parses numbers in base 10.

Here are some additional considerations:

- `parseInt` and `parseFloat` return `NaN` (Not-a-Number) if they cannot parse a valid number from the string.

  ```javascript
  let result = parseInt("abc123"); // Returns NaN
  ```

- `parseInt` can be used for parsing integers from strings, but be cautious when dealing with non-integer input, as it will truncate the decimal part.

  ```javascript
  let integer = parseInt("3.14"); // Parses as 3
  ```

- `parseFloat` is more suitable for parsing floating-point numbers, including decimals.

  ```javascript
  let decimal = parseFloat("3.14"); // Parses as 3.14
  ```

- Always validate user input to ensure that the input string can be successfully converted into a number. You can use functions like `isNaN` or `Number.isNaN` to check if a value is `NaN`.

  ```javascript
  let userInput = "42abc";
  let num = parseFloat(userInput);
  if (!isNaN(num)) {
    console.log("Valid number:", num);
  } else {
    console.log("Invalid input");
  }
  ```

# JavaScript return Keyword

In JavaScript, the `return` keyword is used within functions to specify the value that the function should return when it is called or invoked. It serves several important purposes:

1. **Returning a Value**:
   When a function is called, it can perform some computation and then use the `return` keyword to send a value back to the caller. This returned value can be of any data type, including numbers, strings, objects, arrays, or even other functions.

   ```javascript
   function add(a, b) {
     return a + b;
   }

   let result = add(3, 4); // The function returns 7, which is assigned to 'result'
   ```

2. **Terminating Execution**:
   When the `return` statement is encountered in a function, it not only specifies the value to be returned but also terminates the execution of the function immediately. Any code after the `return` statement within the same function is not executed.

   ```javascript
   function greet(name) {
     if (!name) {
       return "Hello, Guest!";
     }
     return "Hello, " + name + "!";
     // The code below this line is never executed
   }
   ```

3. **Returning Early**:
   The `return` statement is often used for conditional execution, allowing you to return a value early from a function if a certain condition is met. This can make your code more efficient and readable.

   ```javascript
   function divide(a, b) {
     if (b === 0) {
       return "Cannot divide by zero.";
     }
     return a / b;
   }
   ```

4. **Returning Undefined**:
   If a function does not have a `return` statement or if the `return` statement does not specify a value, the function implicitly returns `undefined`.

   ```javascript
   function doSomething() {
     // No return statement, so it returns undefined
   }
   ```

5. **Returning Complex Values**:
   Functions can return complex data types like objects or arrays, allowing you to package multiple pieces of data into a single return value.

   ```javascript
   function createUser(name, age) {
     return {
       name: name,
       age: age,
     };
   }
   ```

6. **Returning Functions**:
   Functions can also return other functions. This is useful for creating closures and for implementing advanced techniques like function factories.

   ```javascript
   function multiplier(factor) {
     return function (x) {
       return x * factor;
     };
   }

   let double = multiplier(2);
   let triple = multiplier(3);
   ```

# JavaScript Operators

JavaScript operators are symbols used to perform operations on values or variables. They can be categorized into several types, including arithmetic, assignment, comparison, logical, bitwise, and more. Here, I'll provide an overview of these operator types with code examples.

1. **Arithmetic Operators:**
   These operators perform mathematical calculations.

   - Addition `+`:

     ```javascript
     let result = 5 + 3; // result is 8
     ```

   - Subtraction `-`:

     ```javascript
     let result = 10 - 5; // result is 5
     ```

   - Multiplication `*`:

     ```javascript
     let result = 4 * 6; // result is 24
     ```

   - Division `/`:

     ```javascript
     let result = 16 / 4; // result is 4
     ```

   - Modulus `%` (remainder):

     ```javascript
     let result = 17 % 5; // result is 2 (remainder of 17 / 5)
     ```

   - Exponentiation `**` (ES6):
     ```javascript
     let result = 2 ** 3; // result is 8 (2 to the power of 3)
     ```

2. **Assignment Operators:**
   These operators are used to assign values to variables.

   - Assignment `=`:

     ```javascript
     let x = 10; // Assigns the value 10 to variable x
     ```

   - Add and Assign `+=`:
     ```javascript
     let x = 5;
     x += 3; // Equivalent to x = x + 3; (x is now 8)
     ```

   Similar assignment operators exist for other arithmetic operations (`-=`, `*=`, `/=`, `%=`).

3. **Comparison Operators:**
   These operators compare values and return a Boolean result.

   - Equality `==`:

     ```javascript
     5 == 5; // true
     "5" == 5; // true (loose equality, type coercion)
     ```

   - Inequality `!=`:

     ```javascript
     5 != 3; // true
     "5" != 5; // false (loose inequality)
     ```

   - Strict Equality `===`:

     ```javascript
     5 === 5; // true
     "5" === 5; // false (strict equality, no type coercion)
     ```

   - Strict Inequality `!==`:
     ```javascript
     5 !== 3; // true
     "5" !== 5; // true (strict inequality)
     ```

   Other comparison operators include `>`, `<`, `>=`, and `<=`.

4. **Logical Operators:**
   These operators perform logical operations on Boolean values.

   - Logical AND `&&`:

     ```javascript
     true && false; // false
     ```

   - Logical OR `||`:

     ```javascript
     true || false; // true
     ```

   - Logical NOT `!`:
     ```javascript
     !true; // false
     ```

5. **Bitwise Operators:**
   These operators perform bitwise operations on integer values.

   - Bitwise AND `&`:

     ```javascript
     5 & 3; // 1 (binary: 101 & 011)
     ```

   - Bitwise OR `|`:

     ```javascript
     5 | 3; // 7 (binary: 101 | 011)
     ```

   - Bitwise XOR `^`:

     ```javascript
     5 ^ 3; // 6 (binary: 101 ^ 011)
     ```

   - Bitwise NOT `~`:
     ```javascript
     ~5; // -6 (binary: ~0101)
     ```

6. **Other Operators:**

   - Conditional (Ternary) Operator `? :`:

     ```javascript
     let age = 18;
     let message = age >= 18 ? "Adult" : "Minor";
     ```

   - typeof Operator:
     ```javascript
     typeof 42; // "number"
     typeof "hello"; // "string"
     ```

# JavaScript Ternary Operator

The ternary operator, also known as the conditional operator, is a shorthand way of writing simple `if...else` statements in JavaScript. It allows you to make a decision and return a value based on a condition. The syntax of the ternary operator is as follows:

```javascript
condition ? expression_if_true : expression_if_false;
```

- `condition`: An expression that evaluates to either `true` or `false`.
- `expression_if_true`: The value or expression to return if the `condition` is `true`.
- `expression_if_false`: The value or expression to return if the `condition` is `false`.

Here are some examples of how the ternary operator can be used:

1. Assigning a value based on a condition:

```javascript
let age = 20;
let message = age >= 18 ? "Adult" : "Minor";
console.log(message); // Outputs: "Adult"
```

2. Displaying different text based on a condition in an HTML document:

```javascript
const isLoggedIn = true;
const loginStatus = isLoggedIn ? "Logged in" : "Logged out";
document.getElementById("status").textContent = loginStatus;
```

In this example, the text content of an HTML element with the id "status" is set based on whether the `isLoggedIn` variable is `true` or `false`.

3. Returning values in a function:

```javascript
function isEven(number) {
  return number % 2 === 0 ? "Even" : "Odd";
}

console.log(isEven(6)); // Outputs: "Even"
console.log(isEven(7)); // Outputs: "Odd"
```
