# Contents to be covered in this session.

## 1. JavaScript Spread Operator.

## 2. JavaScript Rest Operator.

## 3. JavaScript Objects.

## 4. JavaScript Closure (Lexical Environment/Scope).

# JavaScript Spread Operator.

The spread operator (`...`) is a powerful feature in JavaScript that allows you to spread elements of an iterable (like an array or object) into another array, object, or function call. It's useful for a variety of tasks, including copying, combining, and extracting elements from data structures.

### Spread Operator with Arrays:

1. Copying an array:

   ```javascript
   const originalArray = [1, 2, 3];
   const copyArray = [...originalArray];
   console.log(copyArray); // [1, 2, 3]
   ```

2. Merging arrays:

   ```javascript
   const array1 = [1, 2, 3];
   const array2 = [4, 5, 6];
   const mergedArray = [...array1, ...array2];
   console.log(mergedArray); // [1, 2, 3, 4, 5, 6]
   ```

3. Adding elements to an array:
   ```javascript
   const array = [1, 2, 3];
   const newArray = [...array, 4, 5];
   console.log(newArray); // [1, 2, 3, 4, 5]
   ```

### Spread Operator with Objects:

1. Copying an object:

   ```javascript
   const originalObject = { name: "John", age: 30 };
   const copyObject = { ...originalObject };
   console.log(copyObject); // { name: "John", age: 30 }
   ```

2. Merging objects:

   ```javascript
   const object1 = { name: "John" };
   const object2 = { age: 30 };
   const mergedObject = { ...object1, ...object2 };
   console.log(mergedObject); // { name: "John", age: 30 }
   ```

3. Modifying an object while copying:
   ```javascript
   const originalObject = { name: "John" };
   const modifiedObject = { ...originalObject, age: 30 };
   console.log(modifiedObject); // { name: "John", age: 30 }
   ```

### Spread Operator in Function Calls:

1. Passing an array as arguments to a function:

   ```javascript
   function sum(a, b, c) {
     return a + b + c;
   }
   const numbers = [1, 2, 3];
   const result = sum(...numbers);
   console.log(result); // 6
   ```

2. Combining objects in function calls:
   ```javascript
   function mergeObjects(obj1, obj2) {
     return { ...obj1, ...obj2 };
   }
   const object1 = { a: 1 };
   const object2 = { b: 2 };
   const merged = mergeObjects(object1, object2);
   console.log(merged); // { a: 1, b: 2 }
   ```

# JavaScript Rest Operator.

The JavaScript rest operator, represented by three dots (`...`), allows you to capture multiple function arguments or elements from an iterable (like an array) into a single variable. This is particularly useful when you have a variable number of arguments or elements to work with.

1. Using the Rest Operator with Function Arguments:

```javascript
// Example 1: Sum all the arguments passed to a function
function sum(...args) {
  return args.reduce((total, current) => total + current, 0);
}

console.log(sum(1, 2, 3, 4, 5)); // Output: 15

// Example 2: Concatenate multiple strings into one
function concatenateStrings(...strings) {
  return strings.join(" ");
}

console.log(concatenateStrings("Hello", "world", "from", "JavaScript")); // Output: "Hello world from JavaScript"
```

2. Using the Rest Operator with Arrays:

```javascript
// Example 3: Extract the first element and collect the rest into an array
const [first, ...rest] = [1, 2, 3, 4, 5];

console.log(first); // Output: 1
console.log(rest); // Output: [2, 3, 4, 5]

// Example 4: Merge two arrays using the spread operator and rest operator
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const mergedArray = [...arr1, ...arr2];

console.log(mergedArray); // Output: [1, 2, 3, 4, 5, 6]
```

3. Using the Rest Operator with Objects:

```javascript
// Example 5: Destructure an object, capturing the rest of the properties
const person = { firstName: "John", lastName: "Doe", age: 30, gender: "male" };
const { firstName, lastName, ...details } = person;

console.log(firstName); // Output: 'John'
console.log(lastName); // Output: 'Doe'
console.log(details); // Output: { age: 30, gender: 'male' }
```

# JavaScript Objects.

JavaScript objects are one of the fundamental data types in the language, and they can be used to represent real-world entities and concepts with both properties and methods.

## 1. Creating Objects:

You can create objects in JavaScript using object literals or constructor functions.

### Using Object Literals:

```javascript
// Object literal
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
};
```

### Using Constructor Functions:

```javascript
// Constructor function
function Person(firstName, lastName, age) {
  this.firstName = firstName;
  this.lastName = lastName;
  this.age = age;
}

const person = new Person("John", "Doe", 30);
```

## 2. Accessing Properties:

You can access object properties using dot notation or square brackets.

```javascript
console.log(person.firstName); // John
console.log(person["lastName"]); // Doe
```

## 3. Adding and Modifying Properties:

You can add new properties or modify existing ones.

```javascript
person.email = "john@example.com";
person.age = 31;
```

## 4. Object Methods:

Methods are functions stored as object properties.

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  sayHello: function () {
    console.log(`Hello, my name is ${this.firstName} ${this.lastName}`);
  },
};

person.sayHello(); // Hello, my name is John Doe
```

## 5. Shorthand Method Definition:

ES6 introduced a shorthand method definition.

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  sayHello() {
    console.log(`Hello, my name is ${this.firstName} ${this.lastName}`);
  },
};

person.sayHello(); // Hello, my name is John Doe
```

## 6. Object Property Shorthand:

You can create objects with properties having the same names as variables.

```javascript
const firstName = "John";
const lastName = "Doe";

const person = {
  firstName,
  lastName,
};

console.log(person.firstName); // John
```

## 7. 'this' Keyword:

The `this` keyword refers to the current object, allowing access to its properties and methods.

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  sayHello() {
    console.log(`Hello, my name is ${this.firstName} ${this.lastName}`);
  },
};

person.sayHello(); // Hello, my name is John Doe
```

## 8. Object Constructor:

You can use a constructor function to create multiple objects of the same type.

```javascript
function Person(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
  this.sayHello = function () {
    console.log(`Hello, my name is ${this.firstName} ${this.lastName}`);
  };
}

const person1 = new Person("John", "Doe");
const person2 = new Person("Jane", "Smith");

person1.sayHello(); // Hello, my name is John Doe
person2.sayHello(); // Hello, my name is Jane Smith
```

## 9. Object Prototypes:

You can add methods to all objects of a particular type using prototypes.

```javascript
function Person(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}

Person.prototype.sayHello = function () {
  console.log(`Hello, my name is ${this.firstName} ${this.lastName}`);
};

const person1 = new Person("John", "Doe");
const person2 = new Person("Jane", "Smith");

person1.sayHello(); // Hello, my name is John Doe
person2.sayHello(); // Hello, my name is Jane Smith
```

# JavaScript Closure (Lexical Environment/Scope).

A closure is a fundamental concept in JavaScript that allows inner functions to access variables from their outer (enclosing) function, even after the outer function has completed execution. Closures are created when an inner function references variables from an outer function.

Here's an example of a JavaScript closure:

```javascript
function outerFunction() {
  let outerVar = "I am from the outer function";

  function innerFunction() {
    console.log(outerVar); // inner function can access outerVar
  }

  return innerFunction;
}

const closure = outerFunction();
closure(); // This will log "I am from the outer function"
```

In this example:

1. `outerFunction` defines a variable `outerVar` and an inner function `innerFunction`.
2. `innerFunction` has access to the `outerVar` variable even though it's declared in the outer function.
3. `outerFunction` returns the `innerFunction`, which is then assigned to the `closure` variable.
4. When you call `closure()`, it logs the value of `outerVar`.

Closures are commonly used in JavaScript for various purposes.

1. **Data Encapsulation and Information Hiding**:

   ```javascript
   function createCounter() {
     let count = 0;

     return {
       increment: function () {
         count++;
       },
       getCount: function () {
         return count;
       },
     };
   }

   const counter = createCounter();
   counter.increment();
   console.log(counter.getCount()); // Outputs 1
   ```

   In this example, the `count` variable is hidden from the outer scope, and you can only access it through the methods provided by the closure, ensuring data encapsulation.

2. **Event Handling**:

   ```javascript
   function createButton() {
     let clickCount = 0;
     const button = document.createElement("button");

     button.innerText = "Click me";
     button.addEventListener("click", function () {
       clickCount++;
       console.log(`Button clicked ${clickCount} times.`);
     });

     return button;
   }

   const button = createButton();
   document.body.appendChild(button);
   ```

   The `clickCount` variable is enclosed within the closure, allowing it to persist and be updated across multiple button clicks.

3. **Private Variables**:

   ```javascript
   function createPerson(name) {
     let age = 0;

     return {
       getName: function () {
         return name;
       },
       getAge: function () {
         return age;
       },
       setAge: function (newAge) {
         age = newAge;
       },
     };
   }

   const person = createPerson("Alice");
   console.log(person.getName()); // Outputs "Alice"
   console.log(person.getAge()); // Outputs 0
   person.setAge(30);
   console.log(person.getAge()); // Outputs 30
   ```

   In this example, the `name` and `age` variables are encapsulated within the closure, providing data privacy.
