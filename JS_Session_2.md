# Contents to be covered in this session.

## 1. JavaScript Basics of Arrays

## 2. JavaScript Basics of Objects

## 3. JavaScript Basics of Functions

## 4. JavaScript Function Declaration vs Expression

# JavaScript Basics of Arrays

Arrays are an essential data structure in JavaScript that allow you to store and manipulate collections of data. Here are the basics of working with arrays in JavaScript:

1. **Array Declaration**:
   You can create an array using square brackets `[]`. Arrays can hold elements of various data types, including numbers, strings, objects, and even other arrays.

   ```javascript
   let fruits = ["apple", "banana", "cherry"];
   let numbers = [1, 2, 3, 4, 5];
   let mixedArray = [1, "apple", true, { name: "John" }];
   ```

2. **Accessing Elements**:
   Array elements are accessed using their index, which starts at 0 for the first element.

   ```javascript
   console.log(fruits[0]); // Outputs "apple"
   console.log(numbers[2]); // Outputs 3
   ```

3. **Array Length**:
   You can find the number of elements in an array using the `length` property.

   ```javascript
   console.log(fruits.length); // Outputs 3
   ```

4. **Adding and Modifying Elements**:
   You can add or modify elements in an array by assigning values to specific indexes.

   ```javascript
   fruits[1] = "grape"; // Modifies the second element
   fruits.push("kiwi"); // Adds "kiwi" to the end of the array
   ```

5. **Removing Elements**:
   You can remove elements from the end of an array using `pop()`, or from the beginning using `shift()`. You can also use `splice()` to remove elements at specific positions.

   ```javascript
   fruits.pop(); // Removes the last element ("kiwi")
   fruits.shift(); // Removes the first element ("apple")
   ```

6. **Adding Elements**:
   You can add elements to the beginning of an array using `unshift()` or at specific positions using `splice()`.

   ```javascript
   fruits.unshift("orange"); // Adds "orange" to the beginning
   fruits.splice(1, 0, "pear", "peach"); // Adds "pear" and "peach" at index 1
   ```

7. **Iterating Through an Array**:
   You can use loops, such as `for` or `for...of`, to iterate through the elements of an array.

   ```javascript
   for (let i = 0; i < fruits.length; i++) {
     console.log(fruits[i]);
   }

   for (let fruit of fruits) {
     console.log(fruit);
   }
   ```

8. **Array Methods**:
   JavaScript provides many built-in array methods for performing common operations, such as `push()`, `pop()`, `shift()`, `unshift()`, `concat()`, `join()`, `slice()`, `indexOf()`, `find()`, `filter()`, `map()`, and many more. These methods make working with arrays more efficient and convenient.

   ```javascript
   let numbers = [1, 2, 3, 4, 5];
   let doubled = numbers.map(function (num) {
     return num * 2;
   });
   // doubled is now [2, 4, 6, 8, 10]
   ```

9. **Multi-Dimensional Arrays**:
   You can create multi-dimensional arrays (arrays of arrays) to represent matrices or more complex data structures.

   ```javascript
   let matrix = [
     [1, 2, 3],
     [4, 5, 6],
     [7, 8, 9],
   ];
   ```

10. **Array Destructuring**:
    You can use array destructuring to assign values from an array to variables easily.

```javascript
let [first, second, third] = fruits;
console.log(first); // Outputs "apple"
```

# JavaScript Basics of Objects

In JavaScript, objects are a fundamental data type used to store and manipulate data in the form of key-value pairs. Objects are versatile and can represent a wide range of data structures and entities. Here are the basics of working with objects in JavaScript:

1. **Object Declaration**:
   You can create an object using curly braces `{}`. Inside the curly braces, you define the properties and their values as key-value pairs.

   ```javascript
   let person = {
     firstName: "John",
     lastName: "Doe",
     age: 30,
   };
   ```

2. **Accessing Object Properties**:
   You can access object properties using dot notation (`object.property`) or bracket notation (`object["property"]`).

   ```javascript
   console.log(person.firstName); // Outputs "John"
   console.log(person["age"]); // Outputs 30
   ```

3. **Adding and Modifying Properties**:
   You can add new properties or modify existing ones in an object by assignment.

   ```javascript
   person.email = "john.doe@example.com"; // Adding a new property
   person.age = 31; // Modifying an existing property
   ```

4. **Removing Properties**:
   You can delete properties from an object using the `delete` operator.

   ```javascript
   delete person.email;
   ```

5. **Nested Objects**:
   Objects can contain other objects as properties, creating a hierarchical structure.

   ```javascript
   let address = {
     street: "123 Main St",
     city: "Anytown",
     zipCode: "12345",
   };

   let person = {
     firstName: "John",
     lastName: "Doe",
     address: address,
   };
   ```

6. **Iterating Through Object Properties**:
   You can iterate through an object's properties using a `for...in` loop or the `Object.keys()`, `Object.values()`, or `Object.entries()` methods.

   ```javascript
   for (let key in person) {
     console.log(key + ": " + person[key]);
   }
   ```

7. **Object Methods**:
   Objects can also contain methods, which are functions defined as object properties.

   ```javascript
   let calculator = {
     add: function (x, y) {
       return x + y;
     },
     subtract: function (x, y) {
       return x - y;
     },
   };
   ```

8. **Object Constructor**:
   You can create objects using constructor functions or the class syntax (introduced in ES6).

   ```javascript
   function Person(firstName, lastName) {
     this.firstName = firstName;
     this.lastName = lastName;
   }

   let john = new Person("John", "Doe");
   ```

9. **Object Destructuring**:
   Object destructuring allows you to extract values from an object and assign them to variables.

   ```javascript
   let { firstName, lastName } = person;
   console.log(firstName); // Outputs "John"
   ```

10. **Object Property Shorthand**:
    In object literals, if the variable name and property name are the same, you can use shorthand notation.

```javascript
let name = "Alice";
let age = 25;
let person = { name, age }; // Equivalent to { name: name, age: age }
```

# JavaScript Basics of Functions

Functions are a fundamental concept in JavaScript. They allow you to encapsulate and reuse blocks of code. Here are the basics of working with functions in JavaScript:

1. **Function Declaration**:
   You can declare a function using the `function` keyword followed by a name, a list of parameters (enclosed in parentheses), and a block of code (enclosed in curly braces).

   ```javascript
   function greet(name) {
     console.log(`Hello, ${name}!`);
   }
   ```

2. **Function Expression**:
   You can also define functions as expressions, which can be anonymous or named. These functions can be assigned to variables.

   ```javascript
   // Anonymous function expression
   let greet = function (name) {
     console.log(`Hello, ${name}!`);
   };

   // Named function expression
   let multiply = function multiply(a, b) {
     return a * b;
   };
   ```

3. **Function Invocation**:
   To execute a function, you "invoke" or "call" it by using its name followed by parentheses, passing any required arguments.

   ```javascript
   greet("Alice"); // Outputs: Hello, Alice!
   let result = multiply(5, 3); // result contains 15
   ```

4. **Parameters and Arguments**:
   Parameters are variables declared in the function definition, while arguments are the actual values passed to the function when it's called.

   ```javascript
   function add(a, b) {
     return a + b;
   }

   let sum = add(2, 3); // a is 2, b is 3
   ```

5. **Return Statements**:
   Functions can return values using the `return` statement. When a function encounters a `return`, it immediately exits, and the specified value is sent back to the caller.

   ```javascript
   function subtract(a, b) {
     return a - b;
   }

   let result = subtract(10, 4); // result contains 6
   ```

6. **Function Scope**:
   Variables declared within a function are scoped to that function and are not accessible from outside.

   ```javascript
   function myFunction() {
     let localVar = "I am a local variable";
     console.log(localVar);
   }

   myFunction();
   console.log(localVar); // This will result in an error
   ```

7. **Hoisting**:
   Function declarations are hoisted, which means they can be used before they are declared in the code.

   ```javascript
   sayHello(); // This works because the function is hoisted

   function sayHello() {
     console.log("Hello!");
   }
   ```

8. **Anonymous Functions**:
   You can create and use functions without giving them a name, especially when passing functions as arguments to other functions (e.g., in event handlers or array methods).

   ```javascript
   let double = function (x) {
     return x * 2;
   };

   let numbers = [1, 2, 3];
   let doubledNumbers = numbers.map(double);
   ```

9. **Arrow Functions** (ES6):
   Arrow functions provide a more concise syntax for defining functions, especially for short, one-liner functions.

   ```javascript
   let double = (x) => x * 2;
   ```

10. **Function Parameters with Default Values** (ES6):
    You can specify default values for function parameters, which will be used if the caller does not provide a value.

```javascript
function greet(name = "Guest") {
  console.log(`Hello, ${name}!`);
}
```

# JavaScript Function Declaration vs Expression

JavaScript allows you to define functions using two main approaches: function declarations and function expressions. While both approaches create functions, they have some key differences in how they are defined, hoisted, and used.

1. **Function Declaration**:

   - **Syntax**: Function declarations use the `function` keyword followed by a function name, a list of parameters enclosed in parentheses, and a block of code enclosed in curly braces.

     ```javascript
     function greet(name) {
       console.log(`Hello, ${name}!`);
     }
     ```

   - **Hoisting**: Function declarations are hoisted to the top of their containing scope. This means you can call a function before its actual declaration in the code.

     ```javascript
     sayHello(); // This works because the function is hoisted

     function sayHello() {
       console.log("Hello!");
     }
     ```

   - **Usage**: Function declarations are typically used when you want to create named functions that can be called from anywhere within their scope.

2. **Function Expression**:

   - **Syntax**: Function expressions define a function as part of an expression. They can be named or anonymous. Named function expressions can be useful for debugging, but they don't pollute the containing scope with the function name.

     ```javascript
     // Anonymous function expression
     let double = function (x) {
       return x * 2;
     };

     // Named function expression
     let multiply = function multiply(a, b) {
       return a * b;
     };
     ```

   - **Hoisting**: Function expressions are not hoisted in the same way as function declarations. They can only be used after they are defined in the code.

     ```javascript
     sayHello(); // This will result in an error

     let sayHello = function () {
       console.log("Hello!");
     };
     ```

   - **Usage**: Function expressions are commonly used when you want to assign functions to variables, pass them as arguments to other functions, or create functions dynamically. They offer more flexibility in terms of when and where a function is defined and used.

3. **Arrow Functions** (a type of function expression, ES6 and later):

   - Arrow functions provide a concise way to define functions, especially for short, one-liner functions. They are often used for anonymous functions.

     ```javascript
     // Arrow function
     let double = (x) => x * 2;

     // Arrow function with implicit return
     let square = (x) => x * x;
     ```

   - Arrow functions have a shorter syntax and lexically bind the `this` keyword, which can be useful in certain contexts, such as callbacks and event handlers.
