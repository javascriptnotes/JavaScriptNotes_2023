# Contents to be covered in this session.

## 1. JavaScript Getters and Setters.

## 2. JavaScript Template Literals.

## 3. JavaScript Date.

## 4. JavaScript Inheritance.

## 5. JavaScript Prototypes, prototype chain & prototypical inheritance.

# JavaScript Getters and Setters.

Getters and setters in JavaScript are used to control access to object properties. They allow you to define how a property should be read or written, enabling you to encapsulate and protect the data stored in an object. Getters are used to retrieve the value of a property, and setters are used to modify the value of a property.

### Using Getters and Setters

```javascript
// Define an object with a private property
const person = {
  _name: "John", // By convention, a leading underscore indicates a private property

  // Define a getter for the name property
  get name() {
    console.log("Getting name");
    return this._name;
  },

  // Define a setter for the name property
  set name(newName) {
    if (newName.length >= 3) {
      console.log("Setting name");
      this._name = newName;
    } else {
      console.log("Name must be at least 3 characters long.");
    }
  },
};

console.log(person.name); // Calls the getter method
person.name = "Alice"; // Calls the setter method
console.log(person.name); // Calls the getter method
person.name = "Bob"; // Calls the setter method (but with an invalid value)
```

In this example, we have an object `person` with a private property `_name`, which is not intended to be accessed directly. Instead, we define a getter and a setter for the `name` property. When you access `person.name`, the getter is invoked, and when you set `person.name`, the setter is invoked, allowing you to encapsulate the private property.

### Using Classes with Getters and Setters

You can also use getters and setters with classes in JavaScript. Here's an example:

```javascript
class Circle {
  constructor(radius) {
    this._radius = radius;
  }

  // Getter method to retrieve the radius
  get radius() {
    return this._radius;
  }

  // Setter method to set the radius (with validation)
  set radius(newRadius) {
    if (newRadius >= 0) {
      this._radius = newRadius;
    } else {
      console.log("Radius cannot be negative.");
    }
  }

  // Getter method to calculate the area
  get area() {
    return Math.PI * this._radius * this._radius;
  }
}

const myCircle = new Circle(5);
console.log(myCircle.radius); // Calls the getter
myCircle.radius = 10; // Calls the setter
console.log(myCircle.radius); // Calls the getter
myCircle.radius = -3; // Calls the setter (with an invalid value)
console.log(myCircle.area); // Calls the area getter
```

# JavaScript Template Literals.

JavaScript template literals, introduced in ECMAScript 6 (ES6), provide a more convenient way to work with strings and embed expressions within them. Template literals are created using backticks (``) instead of single or double quotes. You can embed expressions within `${}` placeholders within the template literal.

1. Basic Template Literal:

```javascript
const name = "John";
const age = 30;

const message = `My name is ${name} and I am ${age} years old.`;

console.log(message); // Output: My name is John and I am 30 years old.
```

2. Multiline Strings:

Template literals can also be used for multiline strings without the need for explicit line breaks:

```javascript
const multiLine = `
  This is a
  multiline
  string.
`;

console.log(multiLine);
```

3. Expressions in Template Literals:

You can embed expressions and calculations within `${}` placeholders:

```javascript
const x = 10;
const y = 5;

const result = `The sum of ${x} and ${y} is ${x + y}.`;

console.log(result); // Output: The sum of 10 and 5 is 15.
```

4. Function Calls in Template Literals:

You can call functions and use their return values within template literals:

```javascript
function greet(name) {
  return `Hello, ${name}!`;
}

const userName = "Alice";
const greeting = greet(userName);

console.log(greeting); // Output: Hello, Alice!
```

5. Tagged Template Literals:

You can use tagged template literals by defining a function that processes the template literal. The function is called with an array of string parts and the evaluated expressions:

```javascript
function tagFunction(strings, ...values) {
  // 'strings' is an array of string parts
  // 'values' is an array of evaluated expressions
  return `${strings[0]}${values[0]}${strings[1]}${values[1]}`;
}

const a = 5;
const b = 10;

const result = tagFunction`The sum of ${a} and ${b} is ${a + b}.`;

console.log(result); // Output: The sum of 5 and 10 is 15.
```

# JavaScript Date.

JavaScript provides a built-in `Date` object that allows you to work with dates and times. You can create, manipulate, and format dates using this object. Here are some common operations and examples using the JavaScript `Date` object:

1. Creating a Date Object:

   You can create a `Date` object using the `new Date()` constructor. You can pass various arguments to specify a date and time, or you can create an instance for the current date and time without any arguments.

   ```javascript
   // Create a Date object for the current date and time
   const currentDate = new Date();

   // Create a Date object for a specific date and time
   const specificDate = new Date("2023-10-13T14:30:00");
   ```

2. Getting Date Components:

   You can retrieve various components of a date using the `Date` object's methods.

   ```javascript
   const date = new Date();

   const year = date.getFullYear();
   const month = date.getMonth(); // Month (0-11)
   const day = date.getDate(); // Day of the month (1-31)
   const hours = date.getHours(); // Hours (0-23)
   const minutes = date.getMinutes(); // Minutes (0-59)
   const seconds = date.getSeconds(); // Seconds (0-59)
   const milliseconds = date.getMilliseconds(); // Milliseconds (0-999)
   const dayOfWeek = date.getDay(); // Day of the week (0-6, 0=Sunday)
   ```

3. Setting Date Components:

   You can also set various date components using the `Date` object's methods.

   ```javascript
   const date = new Date();

   date.setFullYear(2024);
   date.setMonth(3); // April (0-based)
   date.setDate(15);
   date.setHours(12);
   date.setMinutes(30);
   date.setSeconds(0);
   date.setMilliseconds(500);
   ```

4. Formatting Dates:

   JavaScript doesn't provide built-in methods for formatting dates, so you often use libraries like `Intl.DateTimeFormat` or third-party libraries like `moment.js`. Here's an example using `Intl.DateTimeFormat`:

   ```javascript
   const date = new Date();

   const options = { year: "numeric", month: "long", day: "numeric" };
   const formattedDate = new Intl.DateTimeFormat("en-US", options).format(date);

   console.log(formattedDate); // Output: "October 13, 2023"
   ```

5. Date Arithmetic:

   You can perform date arithmetic by adding or subtracting milliseconds from a `Date` object.

   ```javascript
   const today = new Date();
   const tomorrow = new Date(today.getTime() + 24 * 60 * 60 * 1000); // Add 24 hours
   ```

6. Comparing Dates:

   You can compare two `Date` objects to check which is greater, lesser, or equal.

   ```javascript
   const date1 = new Date("2023-10-13");
   const date2 = new Date("2023-10-14");

   if (date1 < date2) {
     console.log("date1 is earlier than date2");
   } else if (date1 > date2) {
     console.log("date1 is later than date2");
   } else {
     console.log("date1 and date2 are the same");
   }
   ```

# JavaScript Inheritance.

JavaScript supports inheritance through prototypes. Here's an example of how you can create a simple inheritance hierarchy in JavaScript:

```javascript
// Parent class (constructor function)
function Animal(name) {
  this.name = name;
}

// Add a method to the Animal prototype
Animal.prototype.sayName = function () {
  console.log(`My name is ${this.name}`);
};

// Child class (constructor function) that inherits from Animal
function Dog(name, breed) {
  // Call the parent class constructor using "call" or "apply"
  Animal.call(this, name);
  this.breed = breed;
}

// Set up the inheritance relationship
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog; // Reset the constructor to Dog

// Add a method to the Dog prototype
Dog.prototype.bark = function () {
  console.log("Woof! Woof!");
};

// Create instances of the classes
const dog1 = new Dog("Rover", "Labrador");
const dog2 = new Dog("Buddy", "Golden Retriever");

// Call methods on the instances
dog1.sayName(); // Output: My name is Rover
dog1.bark(); // Output: Woof! Woof!

dog2.sayName(); // Output: My name is Buddy
dog2.bark(); // Output: Woof! Woof!
```

In this example:

1. We define a `Animal` constructor function, which takes a `name` parameter and assigns it to the object created with the `new` keyword. We also add a `sayName` method to the `Animal` prototype.

2. We create a `Dog` constructor function, which takes both `name` and `breed` as parameters. To inherit the properties and methods of the `Animal` class, we use `Animal.call(this, name)` to call the `Animal` constructor with the current instance and the `name` parameter.

3. We set up the inheritance relationship between the `Animal` and `Dog` classes by using `Object.create(Animal.prototype)`. This creates a new object that has the `Animal` prototype as its prototype, establishing the inheritance. We also reset the `constructor` property of the `Dog` prototype to point back to the `Dog` constructor function.

4. We add a `bark` method to the `Dog` prototype.

5. Finally, we create instances of the `Dog` class and demonstrate how they can access both their own methods (`bark`) and inherited methods (`sayName`) from the `Animal` class.

# JavaScript Prototypes, prototype chain & prototypical inheritance.

JavaScript prototypes, the prototype chain, and prototypical inheritance are fundamental concepts in the language.

1. **Prototypes:**
   In JavaScript, every object has a prototype, which is another object that it inherits properties and methods from. You can think of a prototype as a blueprint for creating objects. The `Object.prototype` is the root prototype for all objects.

   Example:

   ```javascript
   // Create an object
   const person = {
     firstName: "John",
     lastName: "Doe",
   };

   // Access properties using dot notation
   console.log(person.firstName); // "John"
   console.log(person.lastName); // "Doe"
   ```

2. **Prototype Chain:**
   Objects can have prototypes, and those prototypes can have prototypes of their own, creating a chain. When you access a property or method on an object, JavaScript will look up the prototype chain until it finds the property or method or reaches the end of the chain.

   Example:

   ```javascript
   const person = {
     firstName: "John",
     lastName: "Doe",
     getFullName: function () {
       return this.firstName + " " + this.lastName;
     },
   };

   const employee = {
     jobTitle: "Developer",
   };

   // Set the prototype of `employee` to `person`
   employee.__proto__ = person;

   console.log(employee.firstName); // "John" (inherited from `person`)
   console.log(employee.jobTitle); // "Developer" (own property)
   console.log(employee.getFullName()); // "John Doe" (inherited from `person`)
   ```

3. **Prototypical Inheritance:**
   Prototypical inheritance is a way to create a chain of objects where one object inherits properties and methods from another. It's a simple way to achieve inheritance in JavaScript without using classes.

   Example:

   ```javascript
   function Person(firstName, lastName) {
     this.firstName = firstName;
     this.lastName = lastName;
   }

   Person.prototype.getFullName = function () {
     return this.firstName + " " + this.lastName;
   };

   function Employee(firstName, lastName, jobTitle) {
     Person.call(this, firstName, lastName); // Call the parent constructor
     this.jobTitle = jobTitle;
   }

   Employee.prototype = Object.create(Person.prototype); // Set the prototype chain

   const emp = new Employee("John", "Doe", "Developer");

   console.log(emp.firstName); // "John"
   console.log(emp.jobTitle); // "Developer"
   console.log(emp.getFullName()); // "John Doe"
   ```

In the above code:

- `Person` is a constructor function that sets up a basic person object.
- `Employee` is another constructor function that inherits from `Person` using the `Object.create` method.
- The `__proto__` property is used to set the prototype of an object explicitly, but it's generally better to use `Object.create` or constructor functions for inheritance.
- You can create a new instance of `Employee`, which inherits properties and methods from both `Person` and itself.
