# Contents to be covered in this session.

## 1. JavaScript in Browsers

## 2. Difference among var, let and const

## 3. JavaScript Hoisting

## 4. JavaScript Conditional Statements

## 5. JavaScript Nested Conditionals

## 6. JavaScript Looping/Jumping Statements

## 7. JavaScript Nested Looping/Jumping

# JavaScript in Browsers

JavaScript is a widely-used programming language for web development, and it plays a crucial role in modern web browsers. Here's an overview of how JavaScript works in browsers:

1. **JavaScript Execution Environment:**

   - Browsers have built-in JavaScript engines that interpret and execute JavaScript code. The most common JavaScript engines are V8 (used in Chrome), SpiderMonkey (used in Firefox), and JavaScriptCore (used in Safari).

2. **HTML Integration:**

   - JavaScript is primarily used to enhance the functionality and interactivity of web pages. It can be embedded directly within HTML documents using `<script>` tags. For example:

   ```html
   <script>
     // JavaScript code goes here
   </script>
   ```

   You can include this `<script>` tag in the `<head>` or `<body>` of an HTML document.

3. **External JavaScript Files:**

   - It's a common practice to place JavaScript code in separate external files with a `.js` extension and then reference them in HTML files using the `<script>` tag's `src` attribute. For example:

   ```html
   <script src="myscript.js"></script>
   ```

   This allows for better code organization and reusability.

4. **Asynchronous Loading:**

   - JavaScript can be loaded asynchronously or deferred in order to avoid blocking the rendering of the web page. This is achieved by using the `async` or `defer` attributes on the `<script>` tag:

   ```html
   <script src="myscript.js" async></script>
   <script src="myscript.js" defer></script>
   ```

   - `async`: The script is fetched asynchronously, and the browser can continue parsing the HTML. The script is executed as soon as it's downloaded, which may not preserve the order of execution.

   - `defer`: The script is fetched asynchronously but is executed only after the HTML parsing is complete, preserving the order of execution.

5. **DOM Manipulation:**

   - JavaScript is used to interact with the Document Object Model (DOM) of a web page. Developers can use JavaScript to manipulate the structure, content, and style of the web page dynamically. Common tasks include adding, removing, or modifying HTML elements and handling user interactions.

6. **Event Handling:**

   - JavaScript enables the creation of interactive web applications by allowing developers to define event handlers. These handlers respond to user actions such as clicks, key presses, and mouse movements.

7. **AJAX and Fetch:**

   - JavaScript is used to make asynchronous requests to web servers using technologies like the XMLHttpRequest object or the newer Fetch API. This allows web pages to load data and update content without requiring a full page refresh.

8. **Security:**

   - Browsers have security mechanisms in place to protect users from malicious scripts. For example, the same-origin policy restricts scripts from making requests to domains different from the one that served the web page.

9. **ECMAScript:**

   - JavaScript follows the ECMAScript standard, which defines the language's core features and syntax. Browsers implement different versions of ECMAScript, and web developers need to consider cross-browser compatibility.

10. **Debugging and Developer Tools:**
    - Browsers come with developer tools that include debugging capabilities, allowing developers to inspect, debug, and profile their JavaScript code for troubleshooting and optimization.

# Difference among var, let and const

`let`, `var`, and `const` are all used for variable declarations in JavaScript, but they have some key differences in terms of scope, hoisting, and mutability:

1. **Scope**:

   - `var`:

     - Variables declared with `var` are function-scoped. They are only accessible within the function in which they are declared or globally if declared outside any function.
     - Variables declared with `var` are not block-scoped, meaning they can "leak" out of block statements like `if`, `for`, or `while` loops.

   - `let` and `const`:
     - Variables declared with `let` and `const` are block-scoped, which means they are only accessible within the block in which they are declared (e.g., inside a function or within a loop).
     - Block-scoping helps avoid issues like variable leakage and makes code easier to reason about.

2. **Hoisting**:

   - `var`:

     - Variables declared with `var` are hoisted to the top of their containing function or global scope. However, only the declaration is hoisted, not the initialization.
     - This can lead to unexpected behavior, as the variable is accessible before it's defined but has the value `undefined`.

   - `let` and `const`:
     - Variables declared with `let` and `const` are also hoisted, but they are not initialized during hoisting. Instead, they remain in the "temporal dead zone" until they are explicitly declared in the code.
     - Accessing a variable in the temporal dead zone results in a ReferenceError.

3. **Reassignment**:

   - `var`:

     - Variables declared with `var` can be reassigned, even within the same scope.

   - `let`:

     - Variables declared with `let` can be reassigned within their scope, but they cannot be re-declared within the same scope.

   - `const`:
     - Variables declared with `const` cannot be reassigned after their initial value is set.
     - However, for objects and arrays declared with `const`, their properties or elements can be modified. The reference itself is constant, but the contents can change.

Here are some examples to illustrate these differences:

```javascript
// Example with var
var x = 10;
if (true) {
  var x = 20; // This reassigns the global x
}
console.log(x); // Outputs 20

// Example with let
let y = 10;
if (true) {
  let y = 20; // This creates a new block-scoped y
}
console.log(y); // Outputs 10

// Example with const
const z = 10;
if (true) {
  const z = 20; // This creates a new block-scoped z
}
console.log(z); // Outputs 10
```

# JavaScript Hoisting

Hoisting is a behavior in JavaScript where variable and function declarations are moved to the top of their containing scope during the compilation phase. However, there are some differences in how hoisting works for variables declared with `var`, `let`, and `const`. Let's explore hoisting for each of these variable declarations:

1. **Hoisting with `var`**:
   When you declare a variable with `var`, it is hoisted to the top of its containing function or global scope. However, only the declaration is hoisted, not the initialization (assignment). This means that the variable is "hoisted" but remains undefined until the point in the code where it's actually declared and initialized.

   ```javascript
   console.log(x); // undefined
   var x = 10;
   ```

   In the example above, `x` is hoisted, so the `console.log` statement doesn't result in an error, but the value is `undefined` until it's assigned `10`.

2. **Hoisting with `let` and `const`**:
   Variables declared with `let` and `const` are also hoisted but with a slight difference compared to `var`. Like `var`, the declaration is hoisted to the top of the containing scope. However, unlike `var`, variables declared with `let` and `const` are not initialized before their actual declaration. This is known as the "temporal dead zone" (TDZ). If you try to access a `let` or `const` variable before it's declared, you'll get a ReferenceError.

   ```javascript
   console.log(y); // ReferenceError: y is not defined
   let y = 20;
   ```

   In this example, the `console.log` statement throws an error because `y` is accessed before its declaration.

In summary, both `var`, `let`, and `const` declarations are hoisted, but there are differences in how they are initialized and accessed:

- `var` variables are initialized with `undefined` and can be used before their declaration in the code.
- `let` and `const` variables are not initialized and cannot be accessed before their declaration, resulting in a ReferenceError within the temporal dead zone.

# JavaScript Conditionals

Conditional statements in JavaScript are used to make decisions in your code based on certain conditions. These statements allow you to execute different blocks of code depending on whether a condition evaluates to true or false. The main conditional statements in JavaScript are:

1. **if statement:** The `if` statement is used to execute a block of code if a specified condition is true.

```javascript
let temperature = 25;

if (temperature > 30) {
  console.log("It's a hot day!");
} else {
  console.log("It's not too hot today.");
}
```

2. **else if statement:** You can use the `else if` statement to provide multiple conditions to check.

```javascript
let hour = 14;

if (hour < 12) {
  console.log("Good morning!");
} else if (hour < 18) {
  console.log("Good afternoon!");
} else {
  console.log("Good evening!");
}
```

3. **else statement:** The `else` statement is used to execute a block of code if the condition in the `if` statement is false.

```javascript
let loggedIn = true;

if (loggedIn) {
  console.log("Welcome, user!");
} else {
  console.log("Please log in.");
}
```

4. **switch statement:** The `switch` statement is used when you want to compare a variable to multiple possible values and execute different code blocks for each value.

```javascript
let dayOfWeek = "Wednesday";

switch (dayOfWeek) {
  case "Monday":
    console.log("It's the start of the week.");
    break;
  case "Wednesday":
    console.log("It's the middle of the week.");
    break;
  case "Friday":
    console.log("It's almost the weekend.");
    break;
  default:
    console.log("It's an ordinary day.");
}
```

5. **ternary operator (conditional operator):** The ternary operator is a concise way to write simple if-else statements in a single line.

```javascript
let age = 18;
let canVote = age >= 18 ? "Yes" : "No";

console.log(`Can the person vote? ${canVote}`);
```

6. **Truthy and Falsy values:** In JavaScript, some values are considered truthy and others falsy. You can use these concepts in conditional statements.

```javascript
let user = null;

if (user) {
  console.log("User exists.");
} else {
  console.log("User does not exist.");
}
```

# JavaScript Nested Conditionals

Nested conditionals occur when you place one or more conditional statements inside another conditional statement. This allows you to create more complex decision-making structures. Here are some examples of nested conditionals in JavaScript:

1. **Nested if...else**:

   In this example, we use nested `if...else` statements to determine a person's eligibility to vote based on age and citizenship.

   ```javascript
   let age = 18;
   let isCitizen = true;

   if (isCitizen) {
     if (age >= 18) {
       console.log("You are eligible to vote.");
     } else {
       console.log("You are not old enough to vote.");
     }
   } else {
     console.log("You must be a citizen to vote.");
   }
   ```

2. **Nested switch within if...else**:

   Here, we use a `switch` statement within an `if...else` statement to categorize a person's age group.

   ```javascript
   let age = 25;
   let message = "";

   if (age >= 0) {
     switch (true) {
       case age < 13:
         message = "Child";
         break;
       case age >= 13 && age < 18:
         message = "Teenager";
         break;
       default:
         message = "Adult";
     }
   } else {
     message = "Invalid age";
   }

   console.log(`You are an ${message}.`);
   ```

3. **Nested if with multiple conditions**:

   In this example, we use nested `if` statements to check multiple conditions related to a user's access permissions.

   ```javascript
   let isAdmin = true;
   let isLoggedIn = true;

   if (isLoggedIn) {
     if (isAdmin) {
       console.log("You have full access.");
     } else {
       console.log("You have limited access.");
     }
   } else {
     console.log("Please log in to access the site.");
   }
   ```

4. **Nested ternary operators**:

   You can also nest ternary operators to create more complex conditional expressions. In this example, we determine whether a person can watch a movie based on age and parental consent.

   ```javascript
   let age = 15;
   let hasParentalConsent = true;

   let canWatchMovie =
     age >= 18
       ? "Allowed"
       : hasParentalConsent
       ? "Allowed with consent"
       : "Not allowed";

   console.log(`You are ${canWatchMovie} to watch the movie.`);
   ```

# JavaScript Looping/Jumping

JavaScript provides several looping statements that allow you to execute a block of code repeatedly as long as a certain condition is met or for a specified number of times. Here are the main looping statements in JavaScript with code examples:

1. **for loop**:

   The `for` loop is used to execute a block of code a specific number of times.

   ```javascript
   for (let i = 0; i < 5; i++) {
     console.log(`Iteration ${i}`);
   }
   ```

2. **while loop**:

   The `while` loop is used to execute a block of code as long as a specified condition is true.

   ```javascript
   let i = 0;

   while (i < 5) {
     console.log(`Iteration ${i}`);
     i++;
   }
   ```

3. **do...while loop**:

   The `do...while` loop is similar to the `while` loop, but it ensures that the block of code is executed at least once before checking the condition.

   ```javascript
   let i = 0;

   do {
     console.log(`Iteration ${i}`);
     i++;
   } while (i < 5);
   ```

4. **for...in loop**:

   The `for...in` loop is used to iterate over the properties of an object.

   ```javascript
   const person = {
     name: "John",
     age: 30,
     city: "New York",
   };

   for (let key in person) {
     console.log(`${key}: ${person[key]}`);
   }
   ```

5. **for...of loop**:

   The `for...of` loop is used to iterate over iterable objects like arrays, strings, and more.

   ```javascript
   const fruits = ["apple", "banana", "cherry"];

   for (const fruit of fruits) {
     console.log(fruit);
   }
   ```

6. **forEach method** (for arrays):

   The `forEach` method is used to iterate over each element in an array.

   ```javascript
   const numbers = [1, 2, 3, 4, 5];

   numbers.forEach(function (number) {
     console.log(number);
   });
   ```

7. **break statement**:

   The `break` statement is used to exit a loop prematurely.

   ```javascript
   for (let i = 0; i < 5; i++) {
     if (i === 3) {
       break;
     }
     console.log(`Iteration ${i}`);
   }
   ```

8. **continue statement**:

   The `continue` statement is used to skip the current iteration of a loop and proceed to the next one.

   ```javascript
   for (let i = 0; i < 5; i++) {
     if (i === 3) {
       continue;
     }
     console.log(`Iteration ${i}`);
   }
   ```

# JavaScript Nested Looping/Jumping

Nested loops are loops that are placed inside another loop. They are useful for situations where you need to iterate over multiple sets of data or perform repetitive tasks within repetitive tasks. Here are some examples of nested loops in JavaScript:

1. **Nested for Loop**:

   This example demonstrates a nested `for` loop to create a multiplication table.

   ```javascript
   for (let i = 1; i <= 5; i++) {
     for (let j = 1; j <= 5; j++) {
       console.log(`${i} * ${j} = ${i * j}`);
     }
   }
   ```

   This code will generate a multiplication table from 1 to 5.

2. **Nested while Loop**:

   Here's an example of a nested `while` loop to generate a grid pattern:

   ```javascript
   let row = 1;

   while (row <= 3) {
     let column = 1;
     while (column <= 3) {
       console.log(`Row ${row}, Column ${column}`);
       column++;
     }
     row++;
   }
   ```

   This code will produce a grid with three rows and three columns.

3. **Nested for...in Loop**:

   This example demonstrates nested `for...in` loops to iterate through a two-dimensional array.

   ```javascript
   const matrix = [
     [1, 2, 3],
     [4, 5, 6],
     [7, 8, 9],
   ];

   for (let row in matrix) {
     for (let col in matrix[row]) {
       console.log(`Matrix[${row}][${col}] = ${matrix[row][col]}`);
     }
   }
   ```

   It will iterate through each element of the 2D array and display its value along with its row and column indices.

4. **Nested for...of Loop**:

   This example shows nested `for...of` loops to iterate over arrays within an array.

   ```javascript
   const matrix = [
     [1, 2, 3],
     [4, 5, 6],
     [7, 8, 9],
   ];

   for (const row of matrix) {
     for (const value of row) {
       console.log(`Value: ${value}`);
     }
   }
   ```
