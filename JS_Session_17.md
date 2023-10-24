# Contents to be covered in this session.

## 1. JS Static Methods.

## 2. JS Destructuring Assignment.

## 3. ES6 Getters and Setters.

## 4. ES6 Inheritance.

## 5. ES6 Method Overriding.

## 6. Private Members using Symbol. (Pending - yet to be done)

## 7. Scoping & Scope chaining.



# JS Static Methods.

In JavaScript, static methods are methods that are associated with a class itself rather than with instances of the class. You define static methods using the `static` keyword within a class. Static methods are called on the class itself, not on instances of the class. They are often used for utility functions that are related to the class but do not require access to instance-specific data.

```javascript
class MathUtils {
  // Static method to add two numbers
  static add(a, b) {
    return a + b;
  }

  // Static method to subtract two numbers
  static subtract(a, b) {
    return a - b;
  }
}

// Calling static methods on the class itself
const sum = MathUtils.add(5, 3);
console.log("Sum:", sum); // Output: Sum: 8

const difference = MathUtils.subtract(10, 4);
console.log("Difference:", difference); // Output: Difference: 6
```

In the example above, we define a `MathUtils` class with two static methods, `add` and `subtract`. We then call these static methods directly on the class without creating instances of the class.

Here's another example with a class that uses static methods to work with dates:

```javascript
class DateUtils {
  // Static method to format a date as a string
  static formatDate(date) {
    const options = { year: "numeric", month: "long", day: "numeric" };
    return date.toLocaleDateString(undefined, options);
  }

  // Static method to get the current date
  static getCurrentDate() {
    return new Date();
  }
}

const currentDate = DateUtils.getCurrentDate();
console.log("Current Date:", currentDate);

const formattedDate = DateUtils.formatDate(currentDate);
console.log("Formatted Date:", formattedDate);
```


# JS Destructuring Assignment.

Destructuring assignment is a feature in JavaScript that allows you to extract values from objects and arrays and assign them to variables in a more concise and convenient way.

1. Destructuring Objects:

```javascript
// Example 1: Destructuring an object
const person = { firstName: "John", lastName: "Doe", age: 30 };

// Extracting values into variables
const { firstName, lastName, age } = person;

console.log(firstName); // Output: "John"
console.log(lastName);  // Output: "Doe"
console.log(age);       // Output: 30

// Example 2: Assigning a default value
const { city = "Unknown" } = person;
console.log(city); // Output: "Unknown" (since 'city' doesn't exist in 'person')

// Example 3: Renaming variables
const { firstName: fName, lastName: lName } = person;
console.log(fName); // Output: "John"
console.log(lName); // Output: "Doe"
```

2. Destructuring Arrays:

```javascript
// Example 1: Destructuring an array
const colors = ["red", "green", "blue"];

// Extracting values into variables
const [color1, color2, color3] = colors;

console.log(color1); // Output: "red"
console.log(color2); // Output: "green"
console.log(color3); // Output: "blue"

// Example 2: Ignoring values using the rest operator
const [firstColor, ...restColors] = colors;

console.log(firstColor); // Output: "red"
console.log(restColors); // Output: ["green", "blue"]

// Example 3: Skipping values
const [, secondColor] = colors;

console.log(secondColor); // Output: "green"
```

3. Destructuring Function Parameters:

```javascript
// Example: Destructuring function parameters
function printPerson({ firstName, lastName }) {
  console.log(`First Name: ${firstName}`);
  console.log(`Last Name: ${lastName}`);
}

const person = { firstName: "Alice", lastName: "Smith" };
printPerson(person);

// Output:
// First Name: Alice
// Last Name: Smith
```

4. Destructuring Nested Objects and Arrays:

```javascript
const user = {
  name: "John",
  info: {
    age: 30,
    email: "john@example.com",
  },
  hobbies: ["reading", "hiking"],
};

// Destructuring nested objects and arrays
const {
  name,
  info: { age, email },
  hobbies: [hobby1, hobby2],
} = user;

console.log(name);    // Output: "John"
console.log(age);     // Output: 30
console.log(email);   // Output: "john@example.com"
console.log(hobby1);  // Output: "reading"
console.log(hobby2);  // Output: "hiking"
```


# ES6 Getters and Setters.

ES6 (ECMAScript 2015) introduced getters and setters as a way to define special methods for getting and setting the values of object properties. Getters are used to access the properties of an object, and setters are used to modify those properties. They allow you to control the behavior of reading and writing properties in your JavaScript objects.

**Using Getters:**

A getter is defined using the `get` keyword followed by a function. It's called when you access the property, just like a regular property access.

```javascript
class Circle {
  constructor(radius) {
    this._radius = radius;
  }

  get radius() {
    return this._radius;
  }

  get area() {
    return Math.PI * this._radius ** 2;
  }
}

const myCircle = new Circle(5);

console.log(myCircle.radius); // Accessing the getter for 'radius'
console.log(myCircle.area);   // Accessing the getter for 'area'
```

In this example, the `radius` and `area` properties are exposed using getters. The getters allow you to calculate the area based on the radius when you access the `area` property.

**Using Setters:**

Setters are used to modify properties and are defined with the `set` keyword, followed by a function that takes the new value as an argument.

```javascript
class Circle {
  constructor(radius) {
    this._radius = radius;
  }

  get radius() {
    return this._radius;
  }

  set radius(newRadius) {
    if (newRadius > 0) {
      this._radius = newRadius;
    }
  }
}

const myCircle = new Circle(5);

console.log(myCircle.radius); // Accessing the getter for 'radius'

myCircle.radius = 10;  // Setting the radius using the setter
console.log(myCircle.radius); // Accessing the getter for 'radius'
```

In this example, the `radius` property can be set using the setter. The setter allows you to validate and control the assignment of the property.

**Using Getters and Setters with Computed Properties:**

Getters and setters are often used with computed properties, where the value of one property depends on the value of another.

```javascript
class Rectangle {
  constructor(width, height) {
    this._width = width;
    this._height = height;
  }

  get area() {
    return this._width * this._height;
  }

  get perimeter() {
    return 2 * (this._width + this._height);
  }

  set dimensions({ width, height }) {
    if (width > 0 && height > 0) {
      this._width = width;
      this._height = height;
    }
  }
}

const myRectangle = new Rectangle(5, 7);

console.log(myRectangle.area); // Accessing the getter for 'area'
console.log(myRectangle.perimeter); // Accessing the getter for 'perimeter'

myRectangle.dimensions = { width: 8, height: 10 }; // Setting dimensions using the setter
console.log(myRectangle.area); // Recalculating area
console.log(myRectangle.perimeter); // Recalculating perimeter
```


# ES6 Inheritance.

ES6 (ECMAScript 2015) introduced class-based object-oriented programming features, including inheritance, making it easier to create and manage object hierarchies in JavaScript. In ES6, you can use the `class` syntax to define classes and the `extends` keyword to create subclasses.

**1. Creating a Base Class:**

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}
```

**2. Creating a Subclass:**

```javascript
class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Call the constructor of the base class
    this.breed = breed;
  }

  speak() {
    console.log(`${this.name} barks.`);
  }

  fetch() {
    console.log(`${this.name} is fetching.`);
  }
}
```

In this example, `Dog` is a subclass of `Animal`, and it inherits the `speak` method from the base class. It also has its own method, `fetch`.

**3. Using Inheritance:**

```javascript
const myAnimal = new Animal("Generic Animal");
const myDog = new Dog("Buddy", "Golden Retriever");

myAnimal.speak(); // Output: Generic Animal makes a sound.
myDog.speak();    // Output: Buddy barks.
myDog.fetch();    // Output: Buddy is fetching.
```

By creating instances of these classes, you can see how the inheritance works. The `myDog` object inherits the `speak` method from `Animal`, and it also has its own `fetch` method.

**4. Accessing the Superclass' Methods:**

You can access the superclass methods using `super`:

```javascript
class Cat extends Animal {
  constructor(name, color) {
    super(name);
    this.color = color;
  }

  speak() {
    super.speak(); // Call the speak method of the base class
    console.log(`${this.name} meows.`);
  }
}

const myCat = new Cat("Whiskers", "Calico");
myCat.speak();
```


# ES6 Method Overriding.

Method overriding in ES6 (ECMAScript 2015) allows you to provide a new implementation for a method in a subclass that is inherited from its parent class. This is a fundamental concept in object-oriented programming, where a subclass can provide its own version of a method that has been defined in its parent class.

```javascript
// Parent class
class Animal {
  constructor(name) {
    this.name = name;
  }

  // Method to make a sound
  makeSound() {
    return "Some generic animal sound";
  }
}

// Subclass that overrides the makeSound method
class Dog extends Animal {
  // Constructor calls the parent class constructor
  constructor(name, breed) {
    super(name);
    this.breed = breed;
  }

  // Override the makeSound method
  makeSound() {
    return "Woof! Woof!";
  }
}

// Subclass that doesn't override the makeSound method
class Cat extends Animal {
  constructor(name, color) {
    super(name);
    this.color = color;
  }
}

// Create instances of the classes
const genericAnimal = new Animal("Mysterious Animal");
const dog = new Dog("Buddy", "Golden Retriever");
const cat = new Cat("Whiskers", "Calico");

// Call the makeSound method for each instance
console.log(genericAnimal.makeSound()); // Output: Some generic animal sound
console.log(dog.makeSound()); // Output: Woof! Woof!
console.log(cat.makeSound()); // Output: Some generic animal sound (inherited from the parent class)
```


In JavaScript, variables declared with `var`, `let`, and `const` have different scoping rules. Let's explore scoping and scope chaining for each of these variable declarations with code examples.

1. **`var` Scoping:**
   Variables declared with `var` have function-level scope. This means they are visible throughout the entire function in which they are declared, and they are not block-scoped.

   ```javascript
   function exampleVarScope() {
     if (true) {
       var localVar = "I am a var"; // Function-scoped variable
     }

     console.log(localVar); // Accessible within the function
   }

   exampleVarScope(); // Outputs: "I am a var"
   ```

   Note that using `var` outside of a function scope makes it a global variable, which can lead to unintended consequences and should be avoided.

2. **`let` Scoping:**
   Variables declared with `let` have block-level scope. This means they are only visible within the block in which they are declared (e.g., within an `if` statement or loop).

   ```javascript
   function exampleLetScope() {
     if (true) {
       let blockScopedVar = "I am a let"; // Block-scoped variable
     }

     console.log(blockScopedVar); // Error: blockScopedVar is not defined
   }
   ```

   `blockScopedVar` is only accessible within the `if` block and is not defined outside of it.

3. **`const` Scoping:**
   Variables declared with `const` also have block-level scope, similar to `let`. However, they cannot be reassigned after their initial value is set.

   ```javascript
   function exampleConstScope() {
     if (true) {
       const constantVar = "I am a const"; // Block-scoped and constant variable
     }

     console.log(constantVar); // Error: constantVar is not defined
   }
   ```

   `constantVar` is only accessible within the `if` block and cannot be reassigned.

4. **Scope Chaining:**
   JavaScript has lexical scoping, which means it follows a nested hierarchy of scopes. When a variable is accessed, JavaScript looks for it in the current scope and then moves up the scope chain until it finds the variable or reaches the global scope.

   Example of scope chaining:

   ```javascript
   function outerFunction() {
     let outerVar = "I am from the outer function";

     function innerFunction() {
       let innerVar = "I am from the inner function";
       console.log(outerVar); // Access outerVar from the outer function's scope
     }

     innerFunction();
     console.log(innerVar); // Error: innerVar is not defined in the outer function's scope
   }

   outerFunction();
   ```


# Scoping & Scope chaining.

In JavaScript, variables declared with `var`, `let`, and `const` have different scoping rules. Let's explore scoping and scope chaining for each of these variable declarations with code examples.

1. **`var` Scoping:**
   Variables declared with `var` have function-level scope. This means they are visible throughout the entire function in which they are declared, and they are not block-scoped.

   ```javascript
   function exampleVarScope() {
     if (true) {
       var localVar = "I am a var"; // Function-scoped variable
     }

     console.log(localVar); // Accessible within the function
   }

   exampleVarScope(); // Outputs: "I am a var"
   ```

   Note that using `var` outside of a function scope makes it a global variable, which can lead to unintended consequences and should be avoided.

2. **`let` Scoping:**
   Variables declared with `let` have block-level scope. This means they are only visible within the block in which they are declared (e.g., within an `if` statement or loop).

   ```javascript
   function exampleLetScope() {
     if (true) {
       let blockScopedVar = "I am a let"; // Block-scoped variable
     }

     console.log(blockScopedVar); // Error: blockScopedVar is not defined
   }
   ```

   `blockScopedVar` is only accessible within the `if` block and is not defined outside of it.

3. **`const` Scoping:**
   Variables declared with `const` also have block-level scope, similar to `let`. However, they cannot be reassigned after their initial value is set.

   ```javascript
   function exampleConstScope() {
     if (true) {
       const constantVar = "I am a const"; // Block-scoped and constant variable
     }

     console.log(constantVar); // Error: constantVar is not defined
   }
   ```

   `constantVar` is only accessible within the `if` block and cannot be reassigned.

4. **Scope Chaining:**
   JavaScript has lexical scoping, which means it follows a nested hierarchy of scopes. When a variable is accessed, JavaScript looks for it in the current scope and then moves up the scope chain until it finds the variable or reaches the global scope.

   Example of scope chaining:

   ```javascript
   function outerFunction() {
     let outerVar = "I am from the outer function";

     function innerFunction() {
       let innerVar = "I am from the inner function";
       console.log(outerVar); // Access outerVar from the outer function's scope
     }

     innerFunction();
     console.log(innerVar); // Error: innerVar is not defined in the outer function's scope
   }

   outerFunction();
   ```
