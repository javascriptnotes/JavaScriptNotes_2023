# Contents to be covered in this session.

## 1. JavaScript Error Handling - Try and Catch

## 2. JavaScript Functions

## 3. JavaScript Arrow Functions

## 4. JavaScript Lexical Environment

## 5. JavaScript First class functions

## 6. JavaScript Anonymous & Named Functions Expression
    
## 7. JavaScript Higher Order Functions

## 8. JavaScript Callback Functions

## 9. Difference between Params and Args

## 10. JavaScript Default Parameters

## 11. ReLearn: Bitwise Operators & Infinite Loops (Refer: JS_Session_5.md)

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

# JavaScript Functions

JavaScript functions are blocks of reusable code that perform a specific task. They allow you to encapsulate logic, make your code more modular, and facilitate code reuse. In JavaScript, functions are first-class citizens, which means you can assign them to variables, pass them as arguments to other functions, and return them from other functions. Here's a detailed explanation of JavaScript functions with code examples:

### 1. Function Declaration:

You can define a function using the `function` keyword followed by a name, a list of parameters enclosed in parentheses, and a block of code enclosed in curly braces. Here's a simple function declaration:

```javascript
function greet(name) {
  console.log(`Hello, ${name}!`);
}

// Calling the function
greet("John"); // Output: Hello, John!
```

### 2. Function Expression:

You can also create functions as expressions and assign them to variables. These are known as anonymous functions. Here's an example:

```javascript
const add = function (a, b) {
  return a + b;
};

const result = add(3, 5);
console.log(result); // Output: 8
```

### 3. Arrow Functions (ES6):

Arrow functions provide a more concise syntax for defining functions. They are especially useful for simple one-liner functions.

```javascript
const multiply = (a, b) => a * b;

const product = multiply(4, 6);
console.log(product); // Output: 24
```

### 4. Function Parameters and Arguments:

Functions can accept parameters, which are placeholders for values that are passed when the function is called. The actual values passed are called arguments.

```javascript
function greet(name) {
  console.log(`Hello, ${name}!`);
}

greet("Alice"); // "Alice" is an argument passed to the "name" parameter
```

### 5. Return Statement:

Functions can return values using the `return` statement. If no `return` statement is used, the function returns `undefined`.

```javascript
function add(a, b) {
  return a + b;
}

const sum = add(3, 4);
console.log(sum); // Output: 7
```

### 6. Default Parameters (ES6):

You can provide default values for function parameters, ensuring that the function works even if some arguments are not provided.

```javascript
function greet(name = "Guest") {
  console.log(`Hello, ${name}!`);
}

greet(); // Output: Hello, Guest!
```

### 7. Function Scope:

Variables declared inside a function are scoped to that function and are not accessible outside it.

```javascript
function scopeExample() {
  const localVar = 42;
  console.log(localVar); // Accessible inside the function
}

scopeExample();
console.log(localVar); // Error: localVar is not defined
```

### 8. Higher-Order Functions:

JavaScript allows you to pass functions as arguments to other functions and return functions from functions. These are called higher-order functions.

```javascript
function doMath(operation, a, b) {
  return operation(a, b);
}

function add(a, b) {
  return a + b;
}

function subtract(a, b) {
  return a - b;
}

console.log(doMath(add, 5, 3)); // Output: 8
console.log(doMath(subtract, 5, 3)); // Output: 2
```

### 9. Anonymous Functions and Callbacks:

Anonymous functions are functions without names. They are often used as callbacks in asynchronous operations.

```javascript
setTimeout(function () {
  console.log("This is an anonymous function.");
}, 1000);
```

### 10. Immediately Invoked Function Expressions (IIFE):

IIFE is a way to execute a function immediately after its declaration. It helps create a private scope for your code.

```javascript
(function () {
  const privateVar = "I'm private!";
  console.log(privateVar);
})();

console.log(privateVar); // Error: privateVar is not defined
```

# JavaScript Arrow Functions

Arrow functions are a concise way to write functions in JavaScript. They were introduced in ECMAScript 6 (ES6) and have a more compact syntax compared to traditional function expressions. Arrow functions are especially useful when you want to write small, anonymous functions or when you need to maintain the lexical `this` binding. Let's explore arrow functions in detail with code examples.

### Basic Syntax

The basic syntax of an arrow function is as follows:

```javascript
const functionName = (parameters) => {
  // function body
};
```

Here's a breakdown of the components:

- `const functionName`: You can assign the arrow function to a variable or use it anonymously.
- `(parameters)`: You can have zero or more parameters. If there's only one parameter, you can omit the parentheses.
- `=>`: This is the arrow notation.
- `{}`: The function body enclosed in curly braces.

### Examples

1. **Basic Arrow Function with No Parameters:**

   ```javascript
   const sayHello = () => {
     console.log("Hello, world!");
   };

   sayHello(); // Output: Hello, world!
   ```

2. **Arrow Function with Parameters:**

   ```javascript
   const add = (a, b) => {
     return a + b;
   };

   console.log(add(5, 3)); // Output: 8
   ```

3. **Implicit Return:**

   If the arrow function has a single expression, you can omit the curly braces `{}` and the `return` keyword. The expression's result will be implicitly returned.

   ```javascript
   const multiply = (a, b) => a * b;

   console.log(multiply(4, 2)); // Output: 8
   ```

4. **Arrow Functions with `this` Binding:**

   One of the significant advantages of arrow functions is that they inherit the `this` value from their containing scope. In contrast, regular functions create their own `this` binding. This makes arrow functions especially useful when working with event handlers or callback functions.

   ```javascript
   function Counter() {
     this.count = 0;
     setInterval(() => {
       // 'this' refers to the Counter object
       this.count++;
       console.log(this.count);
     }, 1000);
   }

   const counter = new Counter();
   ```

5. **Arrow Functions in Array Methods:**

   Arrow functions are often used with array methods like `map`, `filter`, and `reduce` to make the code more concise.

   ```javascript
   const numbers = [1, 2, 3, 4, 5];

   const doubled = numbers.map((num) => num * 2);
   console.log(doubled); // Output: [2, 4, 6, 8, 10]

   const evenNumbers = numbers.filter((num) => num % 2 === 0);
   console.log(evenNumbers); // Output: [2, 4]

   const sum = numbers.reduce((acc, num) => acc + num, 0);
   console.log(sum); // Output: 15
   ```

6. **Arrow Functions as Callbacks:**

   Arrow functions are often used as callback functions in asynchronous operations like `setTimeout` or `fetch`.

   ```javascript
   setTimeout(() => {
     console.log("This message will appear after 2 seconds.");
   }, 2000);
   ```

# JavaScript Lexical Environment

In JavaScript, a lexical environment is a data structure that holds variable and function declarations in a specific scope, along with a reference to the outer lexical environment. Lexical environments are an essential concept for understanding how variable scoping and closures work in JavaScript. Let's explore lexical environments with some code examples.

1. Global Lexical Environment:
   The global lexical environment represents the top-level scope in your JavaScript code. It contains all the global variables and functions.

```javascript
// Global variable
var globalVar = 10;

function globalFunction() {
  // Function within the global lexical environment
  console.log(globalVar); // Accessing globalVar from the outer lexical environment
}

globalFunction();
```

2. Function Lexical Environment:
   When you declare a function, it creates its own lexical environment, which includes its parameters and any variables declared inside the function.

```javascript
function outerFunction() {
  var outerVar = 20;

  function innerFunction() {
    var innerVar = 30;
    console.log(outerVar); // Accessing outerVar from the outer lexical environment
  }

  innerFunction();
}

outerFunction();
```

3. Nested Lexical Environments:
   Lexical environments can be nested. Inner functions have access to variables declared in their outer functions, creating closures.

```javascript
function outer() {
  var outerVar = "I'm in the outer function";

  function inner() {
    console.log(outerVar); // Accessing outerVar from the outer lexical environment (closure)
  }

  return inner;
}

var closureFunction = outer();
closureFunction(); // This still has access to outerVar even though outer() has finished executing.
```

4. Block Scope Lexical Environment (with `let` and `const`):
   Block-scoped variables created with `let` and `const` also have their own lexical environments confined to the block in which they are declared.

```javascript
if (true) {
  let blockVar = 42; // Block-scoped variable
  console.log(blockVar);
}

// console.log(blockVar); // This would result in an error because blockVar is not in scope here.
```

5. Lexical Environment Chain:
   Lexical environments are linked together in a chain. When a variable is accessed, JavaScript searches for it in the current lexical environment and then follows the chain to outer lexical environments until it finds the variable or reaches the global environment.

```javascript
var globalVar = "I'm global";

function outerFunction() {
  var outerVar = "I'm in outer";

  function innerFunction() {
    console.log(outerVar); // Accesses outerVar from the outer lexical environment
    console.log(globalVar); // Accesses globalVar from the global lexical environment
  }

  return innerFunction;
}

var innerFunc = outerFunction();
innerFunc();
```

# JavaScript First class functions

In JavaScript, functions are first-class citizens, which means they can be treated like any other data type, such as strings, numbers, or objects. Here are some examples of how JavaScript allows you to work with first-class functions:

1. Assigning functions to variables:

```javascript
const sayHello = function () {
  console.log("Hello, world!");
};

sayHello(); // Calling the function
```

In this example, we assigned an anonymous function to the `sayHello` variable, and we can then call it like any other function.

2. Passing functions as arguments to other functions:

```javascript
function greet(name, greetingFunction) {
  console.log(greetingFunction(name));
}

function sayHi(name) {
  return `Hi, ${name}!`;
}

function sayHello(name) {
  return `Hello, ${name}!`;
}

greet("Alice", sayHi); // Output: Hi, Alice!
greet("Bob", sayHello); // Output: Hello, Bob!
```

In this example, the `greet` function accepts another function (`greetingFunction`) as an argument and uses it to generate a greeting message.

3. Returning functions from other functions:

```javascript
function multiplier(factor) {
  return function (x) {
    return x * factor;
  };
}

const double = multiplier(2);
const triple = multiplier(3);

console.log(double(5)); // Output: 10
console.log(triple(5)); // Output: 15
```

In this example, the `multiplier` function returns another function that can be used to multiply a number by the specified factor.

4. Storing functions in data structures:

```javascript
const mathOperations = {
  add: function (x, y) {
    return x + y;
  },
  subtract: function (x, y) {
    return x - y;
  },
};

console.log(mathOperations.add(5, 3)); // Output: 8
console.log(mathOperations.subtract(10, 2)); // Output: 8
```

In this example, we store functions as properties in an object.

5. Creating anonymous functions:

```javascript
const square = function (x) {
  return x * x;
};

console.log(square(4)); // Output: 16
```

# JavaScript Anonymous & Named Functions Expression

In JavaScript, functions can be defined using two main techniques: anonymous functions and named function expressions. Both of these techniques allow you to create functions as expressions, which means you can assign them to variables, pass them as arguments to other functions, and use them in various ways.

1. **Anonymous Function Expression**:

   An anonymous function expression is a function without a name. It is defined within an expression and is often used when you need a function for a short-lived purpose.

   ```javascript
   // Anonymous Function Expression
   const add = function (a, b) {
     return a + b;
   };

   // Usage
   const result = add(3, 4);
   console.log(result); // Output: 7
   ```

   In the example above, we've defined an anonymous function and assigned it to the `add` variable. This function can be invoked using `add(3, 4)`.

2. **Named Function Expression**:

   A named function expression is similar to an anonymous function expression but with a name. The name is useful for self-reference within the function and for stack trace debugging.

   ```javascript
   // Named Function Expression
   const multiply = function multiply(a, b) {
     return a * b;
   };

   // Usage
   const result = multiply(3, 4);
   console.log(result); // Output: 12
   ```

   In this example, we've given the function the name "multiply." The function can still be assigned to a variable (`multiply`) and used like any other function.

3. **Differences**:

   - Anonymous Function Expressions: They are often used when you don't need to refer to the function by name, and they can be shorter and more concise.

   - Named Function Expressions: They are helpful when you want the function to have a name for debugging purposes or when you need to reference the function inside itself (recursion).

Here's an example that demonstrates both anonymous and named function expressions in an array processing context:

```javascript
const numbers = [1, 2, 3, 4, 5];

// Anonymous function expression
const squaredAnonymous = numbers.map(function (x) {
  return x * x;
});

// Named function expression
const squaredNamed = numbers.map(function square(x) {
  return x * x;
});

console.log(squaredAnonymous); // [1, 4, 9, 16, 25]
console.log(squaredNamed); // [1, 4, 9, 16, 25]
```

# JavaScript Higher Order Functions

Higher-order functions are an essential concept in JavaScript. These functions either take other functions as arguments or return functions as their results. They enable you to write more flexible and reusable code. Let's explore higher-order functions in detail with code examples.

### 1. `map()`

The `map()` method creates a new array by calling a provided function on every element in the array.

```javascript
const numbers = [1, 2, 3, 4, 5];
const squaredNumbers = numbers.map(function (num) {
  return num * num;
});

console.log(squaredNumbers); // [1, 4, 9, 16, 25]
```

### 2. `filter()`

The `filter()` method creates a new array with all elements that pass a provided test function.

```javascript
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter(function (num) {
  return num % 2 === 0;
});

console.log(evenNumbers); // [2, 4]
```

### 3. `reduce()`

The `reduce()` method applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single value.

```javascript
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce(function (accumulator, current) {
  return accumulator + current;
}, 0);

console.log(sum); // 15
```

### 4. `forEach()`

The `forEach()` method executes a provided function once for each array element.

```javascript
const fruits = ["apple", "banana", "cherry"];
fruits.forEach(function (fruit) {
  console.log(fruit);
});
// Output:
// apple
// banana
// cherry
```

### 5. `sort()`

The `sort()` method sorts the elements of an array in place and returns the sorted array.

```javascript
const fruits = ["apple", "banana", "cherry"];
const sortedFruits = fruits.sort();

console.log(sortedFruits); // ['apple', 'banana', 'cherry']
```

### 6. `find()`

The `find()` method returns the first element in an array that satisfies a provided testing function.

```javascript
const numbers = [1, 2, 3, 4, 5];
const foundNumber = numbers.find(function (num) {
  return num > 3;
});

console.log(foundNumber); // 4
```

### 7. `some()` and `every()`

The `some()` method tests whether at least one element in the array passes the test implemented by the provided function. The `every()` method tests whether all elements in the array pass the test.

```javascript
const numbers = [1, 2, 3, 4, 5];

const hasEven = numbers.some(function (num) {
  return num % 2 === 0;
});
console.log(hasEven); // true

const allEven = numbers.every(function (num) {
  return num % 2 === 0;
});
console.log(allEven); // false
```

### 8. Custom Higher-Order Functions

You can create custom higher-order functions to suit your specific needs. For example, a function that returns a function:

```javascript
function multiplier(factor) {
  return function (number) {
    return number * factor;
  };
}

const double = multiplier(2);
const triple = multiplier(3);

console.log(double(5)); // 10
console.log(triple(5)); // 15
```

# JavaScript Callback Functions

JavaScript callback functions are a fundamental concept in JavaScript programming. They are functions that are passed as arguments to other functions and are executed when a specific event or condition occurs. Callback functions are often used in asynchronous programming, such as handling events, making API requests, or reading files, where you want to perform an action after an operation has completed.

Here's a detailed explanation of callback functions with code examples:

### 1. Basic Callback Function

A basic callback function is a function passed as an argument to another function and is executed when the parent function has completed its task.

```javascript
function doSomething(callback) {
  console.log("Doing something...");
  // Simulate some asynchronous operation
  setTimeout(function () {
    console.log("Operation completed.");
    callback(); // Call the callback function
  }, 2000);
}

function callbackFunction() {
  console.log("Callback function executed.");
}

doSomething(callbackFunction);
```

In this example, `doSomething` is a function that takes a `callback` function as an argument and calls it when it's done. When `doSomething` is called, it logs "Doing something..." and then simulates a delay using `setTimeout`. After the delay, it logs "Operation completed." and calls the `callback` function, which in this case is `callbackFunction`.

### 2. Callbacks in Event Handling

Callback functions are commonly used in event handling, such as handling button clicks:

```javascript
const button = document.getElementById("myButton");

function handleClick() {
  console.log("Button clicked!");
}

button.addEventListener("click", handleClick);
```

In this example, the `handleClick` function is used as a callback to the `addEventListener` method. When the "myButton" element is clicked, the `handleClick` function is executed.

### 3. Callbacks in Asynchronous Operations

Callback functions are frequently used in asynchronous operations like AJAX requests:

```javascript
function fetchData(url, callback) {
  const xhr = new XMLHttpRequest();
  xhr.open("GET", url, true);

  xhr.onload = function () {
    if (xhr.status === 200) {
      callback(null, xhr.responseText);
    } else {
      callback(new Error("Request failed"), null);
    }
  };

  xhr.send();
}

function handleResponse(error, data) {
  if (error) {
    console.error(error);
  } else {
    console.log(data);
  }
}

fetchData("https://jsonplaceholder.typicode.com/posts/1", handleResponse);
```

In this example, the `fetchData` function fetches data from a URL using an XMLHttpRequest. It takes a callback function, `handleResponse`, which is called with either an error or the fetched data.

### 4. Callback Hell (Callback Pyramid)

One issue with using callback functions extensively is callback hell, where you have deeply nested callbacks, making code hard to read and maintain. To mitigate this, you can use Promises or async/await.

Here's an example of callback hell:

```javascript
getData(function (data) {
  processData(data, function (processedData) {
    saveData(processedData, function (result) {
      console.log(result);
    });
  });
});
```

Using Promises or async/await can make the code more readable and maintainable.

```javascript
getData()
  .then(processData)
  .then(saveData)
  .then((result) => {
    console.log(result);
  })
  .catch((error) => {
    console.error(error);
  });
```

# Difference between Params and Args

In JavaScript, `params` and `args` are not built-in keywords like some other programming languages might have. Instead, they are typically used as conventional variable names to represent different concepts in function definitions. Let's break down the differences between `params` and `args` with code examples:

1. Parameters (`params`):

Parameters refer to the placeholders declared in a function definition. These placeholders are used to receive input values when the function is called. Parameters are essentially variables with local scope within the function.

Here's an example:

```javascript
function add(a, b) {
  return a + b;
}

// In this function, 'a' and 'b' are parameters.
// When you call add(2, 3), 2 and 3 are passed as arguments and become the values of 'a' and 'b'.
console.log(add(2, 3)); // Output: 5
```

In this example, `a` and `b` are parameters of the `add` function. They act as placeholders for the values you provide when you call the function.

2. Arguments (`args`):

Arguments refer to the actual values passed into a function when it is called. These values are assigned to the corresponding parameters within the function's scope.

Here's an example:

```javascript
function greet(name) {
  console.log("Hello, " + name + "!");
}

// In this function, 'name' is a parameter.
// When you call greet("Alice"), "Alice" is an argument that gets assigned to the 'name' parameter.
greet("Alice"); // Output: Hello, Alice!
```

In this example, `"Alice"` is an argument that is passed to the `greet` function, and it gets assigned to the `name` parameter within the function.

So, in summary:

- Parameters (`params`) are placeholders declared in the function definition.
- Arguments (`args`) are the actual values passed into the function when it is called.

# JavaScript Default Parameters

In JavaScript, default parameters allow you to assign default values to function parameters when they are not provided by the caller of the function. This feature is especially useful when you want to ensure that your function behaves predictably even when some arguments are missing.

Here's how you can use default parameters in JavaScript, along with some code examples:

### Basic Default Parameters

You can set default values for function parameters directly in the parameter list using the assignment (`=`) operator:

```javascript
function greet(name = "Anonymous") {
  console.log(`Hello, ${name}!`);
}

greet(); // Output: Hello, Anonymous!
greet("Alice"); // Output: Hello, Alice!
```

In the example above, the `name` parameter has a default value of `"Anonymous"`. If you call the `greet` function without providing an argument for `name`, it will use the default value.

### Default Parameters with Expressions

You can use more complex expressions as default values:

```javascript
function calculateTax(amount, taxRate = 0.1 * amount) {
  return amount + taxRate;
}

console.log(calculateTax(100)); // Output: 110 (100 + 0.1 * 100)
console.log(calculateTax(200, 0.2)); // Output: 200.2 (200 + 0.2)
```

In this example, the `taxRate` parameter's default value is calculated based on the `amount` parameter. If `taxRate` is not provided, it defaults to 10% of the `amount`.

### Default Parameters with Function Calls

You can also use function calls as default values. This can be useful when you want to create default values based on some logic:

```javascript
function generateUniqueId(prefix = generateRandomId()) {
  return `${prefix}-${Math.random().toString(36).substr(2, 9)}`;
}

function generateRandomId() {
  return Math.floor(Math.random() * 1000);
}

console.log(generateUniqueId()); // Output: <random number>-<random string>
```

In this example, the `generateUniqueId` function uses the `generateRandomId` function as the default value for the `prefix` parameter if one is not provided.

### Default Parameters with Undefined

Be aware that default parameters are only used when the parameter is `undefined`. If you pass `null`, `0`, an empty string, or any other value, the default value won't be used:

```javascript
function example(value = "Default") {
  console.log(value);
}

example(); // Output: Default
example(null); // Output: null
example(0); // Output: 0
example(""); // Output: ""
```

In the example above, `value` will only default to `"Default"` if it's not provided or explicitly set to `undefined`.

### Default Parameters with Destructuring

Default parameters can also be used in conjunction with destructuring in function parameters:

```javascript
function printInfo({ name = "Anonymous", age = 0 }) {
  console.log(`Name: ${name}, Age: ${age}`);
}

printInfo({ name: "Alice", age: 30 }); // Output: Name: Alice, Age: 30
printInfo({}); // Output: Name: Anonymous, Age: 0
```
