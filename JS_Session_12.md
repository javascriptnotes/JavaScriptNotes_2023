# Contents to be covered in this session.

## 1. JavaScript Basic OOps, 4 Pillars.

## 2. JavaScript Factories and Factory Function.

## 3. JavaScript Constructor & Constructor Functions.

## 4. JavaScript Constructor Property.

## 5. JavaScript Dynamic Nature of Objects.

## 6. JavaScript Functions and Objects.

## 7. JavaScript 'This' keyword.

# JavaScript Basic OOPs, 4 Pillars.

Object-Oriented Programming (OOPs) is a programming paradigm that uses objects to model and represent real-world entities, with the goal of encapsulating data and behavior into reusable and modular components. In JavaScript, you can implement OOP concepts using prototypes and classes.

1. **Class**: A blueprint for creating objects.

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}

const dog = new Animal("Dog");
dog.speak(); // Output: Dog makes a sound.
```

2. **Object**: An instance of a class.

```javascript
const cat = new Animal("Cat");
cat.speak(); // Output: Cat makes a sound.
```

3. **Constructor**: A special method that initializes object properties when an object is created.

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

const john = new Person("John", 30);
console.log(john.name); // Output: John
```

4. **Method**: Functions defined within a class to perform actions on class properties.

```javascript
class Rectangle {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }

  calculateArea() {
    return this.width * this.height;
  }
}

const rect = new Rectangle(5, 10);
console.log(rect.calculateArea()); // Output: 50
```

5. **Inheritance**: The ability of a class to inherit properties and methods from another class.

```javascript
class Vehicle {
  constructor(make, model) {
    this.make = make;
    this.model = model;
  }

  getInfo() {
    return `${this.make} ${this.model}`;
  }
}

class Car extends Vehicle {
  constructor(make, model, year) {
    super(make, model);
    this.year = year;
  }

  getInfo() {
    return `${this.year} ${super.getInfo()}`;
  }
}

const myCar = new Car("Toyota", "Camry", 2020);
console.log(myCar.getInfo()); // Output: 2020 Toyota Camry
```

6. **Encapsulation**: The concept of bundling data and methods that operate on that data within a single unit (class).

```javascript
class BankAccount {
  constructor(balance) {
    let _balance = balance; // Private variable

    this.getBalance = () => {
      return _balance;
    };

    this.deposit = (amount) => {
      _balance += amount;
    };

    this.withdraw = (amount) => {
      if (amount <= _balance) {
        _balance -= amount;
      } else {
        console.log("Insufficient funds.");
      }
    };
  }
}

const account = new BankAccount(1000);
console.log(account.getBalance()); // Output: 1000
account.deposit(500);
console.log(account.getBalance()); // Output: 1500
account.withdraw(2000); // Output: Insufficient funds.
```

7. **Polymorphism**: The ability of objects of different classes to respond to the same method.

```javascript
class Shape {
  area() {
    return 0;
  }
}

class Circle extends Shape {
  constructor(radius) {
    super();
    this.radius = radius;
  }

  area() {
    return Math.PI * this.radius * this.radius;
  }
}

class Square extends Shape {
  constructor(side) {
    super();
    this.side = side;
  }

  area() {
    return this.side * this.side;
  }
}

const shapes = [new Circle(5), new Square(4)];
shapes.forEach((shape) => {
  console.log(`Area: ${shape.area()}`);
});
// Output:
// Area: 78.53981633974483 (Circle)
// Area: 16 (Square)
```

8. **Prototype**:

   - In JavaScript, each object has a prototype. A prototype is an object that provides shared properties and methods that can be accessed by other objects.

   - Prototypes are used for inheritance in JavaScript. When a property or method is accessed on an object, JavaScript first checks if that property or method exists on the object itself. If it doesn't find it, it looks up the prototype chain to find it on the object's prototype, and so on.

   - The `prototype` property of a constructor function is used to set up the prototype for objects created using that constructor.

   ```javascript
   function Person(name) {
     this.name = name;
   }

   Person.prototype.sayHello = function () {
     console.log(`Hello, my name is ${this.name}.`);
   };

   const person1 = new Person("John");
   person1.sayHello(); // Output: Hello, my name is John.
   ```

9. **Abstraction**:

   - Abstraction is a fundamental concept in OOP that involves hiding the complex implementation details of an object and exposing only the essential features and functionalities to the outside world.

   - In JavaScript, abstraction can be achieved through encapsulation, where you hide the internal details of an object and provide a clear interface for interacting with it.

   - You can use access modifiers like `private` variables or methods to achieve encapsulation and abstraction.

   ```javascript
   class BankAccount {
     constructor(balance) {
       let _balance = balance; // Private variable

       this.getBalance = () => {
         return _balance;
       };

       this.deposit = (amount) => {
         _balance += amount;
       };

       this.withdraw = (amount) => {
         if (amount <= _balance) {
           _balance -= amount;
         } else {
           console.log("Insufficient funds.");
         }
       };
     }
   }

   const account = new BankAccount(1000);

   console.log(account.getBalance()); // Accessing balance (abstraction)
   account.deposit(500); // Modifying balance (abstraction)
   console.log(account.getBalance()); // Accessing balance (abstraction)
   account.withdraw(2000); // Modifying balance (abstraction)
   ```

# JavaScript Factories and Factory Function.

In JavaScript, factory functions are a design pattern used for creating and returning objects. They provide a way to encapsulate object creation, promote code reusability, and allow for more flexible and consistent object initialization. Factory functions are essentially functions that create and return objects, and they don't require the use of the `new` keyword like constructor functions.

```javascript
// Factory function to create person objects
function createPerson(name, age) {
  return {
    name,
    age,
    greet() {
      console.log(
        `Hello, my name is ${this.name} and I am ${this.age} years old.`
      );
    },
  };
}

const person1 = createPerson("Alice", 30);
const person2 = createPerson("Bob", 25);

person1.greet(); // Output: Hello, my name is Alice and I am 30 years old.
person2.greet(); // Output: Hello, my name is Bob and I am 25 years old.
```

In the example above, `createPerson` is a factory function that takes `name` and `age` as arguments and returns a new person object with properties and methods.

Factory functions can also be used to create objects with private variables or closures to encapsulate data. Here's an example:

```javascript
// Factory function with private variable
function createCounter() {
  let count = 0;

  return {
    increment() {
      count++;
    },
    decrement() {
      count--;
    },
    getCount() {
      return count;
    },
  };
}

const counter1 = createCounter();
const counter2 = createCounter();

counter1.increment();
counter1.increment();
counter1.decrement();

counter2.increment();

console.log(counter1.getCount()); // Output: 1
console.log(counter2.getCount()); // Output: 1
```

# JavaScript Constructor & Constructor Functions.

In JavaScript, constructor functions are used to create and initialize objects. They are essentially a blueprint for creating objects of a specific type. Constructor functions are often used in conjunction with the `new` keyword to create new instances of objects.

### Constructor Function Definition:

```javascript
// Constructor function for creating Person objects
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Adding a method to the Person prototype
Person.prototype.greet = function () {
  console.log(`Hello, my name is ${this.name} and I'm ${this.age} years old.`);
};
```

In the code above, we've defined a constructor function `Person` that takes two parameters (`name` and `age`) and assigns them as properties to the newly created object using the `this` keyword. We've also added a `greet` method to the `Person` prototype, which all instances of `Person` will be able to access.

### Creating Instances using the Constructor Function:

```javascript
// Creating instances of Person using the constructor function
const person1 = new Person("Alice", 30);
const person2 = new Person("Bob", 25);

// Calling the greet method on the instances
person1.greet(); // Outputs: Hello, my name is Alice and I'm 30 years old.
person2.greet(); // Outputs: Hello, my name is Bob and I'm 25 years old.
```

To create instances of the `Person` object, we use the `new` keyword followed by the constructor function. This allocates memory for a new object, sets the prototype of the object to the constructor's prototype, and invokes the constructor function with the provided arguments.

### Constructor Functions vs. Class Syntax (ES6):

In modern JavaScript (ECMAScript 6 and later), you can use class syntax to achieve the same functionality more succinctly. Here's an example using classes:

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(
      `Hello, my name is ${this.name} and I'm ${this.age} years old.`
    );
  }
}

const person1 = new Person("Alice", 30);
const person2 = new Person("Bob", 25);

person1.greet(); // Outputs: Hello, my name is Alice and I'm 30 years old.
person2.greet(); // Outputs: Hello, my name is Bob and I'm 25 years old.
```

# JavaScript Constructor Property.

In JavaScript, the `constructor` property is a built-in property of objects that refers to the constructor function that was used to create the object. This property can be useful when you want to identify the type or class of an object, especially in situations where objects are created using constructor functions or classes.

1. Using Constructor Functions:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

const john = new Person("John", 30);

console.log(john.constructor); // Outputs: ƒ Person(name, age) { ... }
console.log(john.constructor === Person); // Outputs: true
```

In this example, we have a constructor function `Person`, and we create an object `john` using the `new` keyword. The `constructor` property of `john` refers to the `Person` constructor function.

2. Using Classes:

```javascript
class Car {
  constructor(make, model) {
    this.make = make;
    this.model = model;
  }
}

const myCar = new Car("Toyota", "Camry");

console.log(myCar.constructor); // Outputs: class Car { ... }
console.log(myCar.constructor === Car); // Outputs: true
```

In this example, we define a class `Car` and create an object `myCar` using the class constructor. The `constructor` property of `myCar` refers to the `Car` class.

3. Changing the Constructor Property:

You can also change the `constructor` property if you want, although it's not a common practice:

```javascript
function Dog(name) {
  this.name = name;
}

const myDog = new Dog("Buddy");
console.log(myDog.constructor === Dog); // Outputs: true

function Cat(name) {
  this.name = name;
}
myDog.constructor = Cat; // Change the constructor property
console.log(myDog.constructor === Dog); // Outputs: false
console.log(myDog.constructor === Cat); // Outputs: true
```

In this example, we initially create a `myDog` object with the `Dog` constructor, and its `constructor` property points to `Dog`. Later, we change the `constructor` property to `Cat`, so it now points to the `Cat` constructor.

The `constructor` property can be helpful for type checking and for determining the origin of an object, but it's not foolproof and may not always accurately represent the object's actual class or type, especially in scenarios involving inheritance and prototype chains.

# JavaScript Dynamic Nature of Objects.

JavaScript is a dynamically typed and loosely typed language, which means that the nature of objects and variables can change during runtime. This dynamic nature allows you to add, remove, and modify properties and methods of objects on the fly. Here are some examples to illustrate the dynamic nature of objects in JavaScript:

1. Adding properties to an object:

```javascript
const person = { name: "John" };
person.age = 30;
console.log(person); // { name: "John", age: 30 }
```

In this example, we added an "age" property to the "person" object after it was initially created.

2. Modifying properties of an object:

```javascript
const car = { make: "Toyota", model: "Camry" };
car.model = "Corolla";
console.log(car); // { make: "Toyota", model: "Corolla" }
```

We modified the "model" property of the "car" object.

3. Deleting properties from an object:

```javascript
const student = { name: "Alice", age: 25, grade: "A" };
delete student.grade;
console.log(student); // { name: "Alice", age: 25 }
```

We removed the "grade" property from the "student" object using the `delete` operator.

4. Reassigning objects to variables:

```javascript
let apple = { color: "red" };
let orange = apple;
orange.color = "orange";
console.log(apple.color); // "orange"
```

In this case, modifying the "orange" object also affects the "apple" object because they reference the same underlying object in memory.

5. Adding and removing methods from objects:

```javascript
const calculator = {
  add: function (a, b) {
    return a + b;
  },
  subtract: function (a, b) {
    return a - b;
  },
};

calculator.multiply = function (a, b) {
  return a * b;
};

delete calculator.subtract;

console.log(calculator.add(5, 3)); // 8
console.log(calculator.multiply(4, 2)); // 8
```

Here, we added a "multiply" method and removed the "subtract" method from the "calculator" object.

6. Changing an object's prototype:

```javascript
function Person(name) {
  this.name = name;
}

const john = new Person("John");
const jane = { name: "Jane" };

jane.__proto__ = john;

console.log(jane.name); // "Jane"
console.log(jane.hasOwnProperty("name")); // true
console.log(jane.hasOwnProperty("sayHello")); // false
console.log(jane.__proto__.name); // "John"
```

# JavaScript Functions and Objects.

JavaScript functions can be used in combination with objects to create methods, which are functions that are associated with an object. These methods can manipulate the object's properties or perform specific actions related to the object.

1. **Creating an Object:**

   You can create an object using an object literal notation. In this example, we'll create an object representing a person:

   ```javascript
   const person = {
     firstName: "John",
     lastName: "Doe",
     age: 30,
   };
   ```

2. **Adding a Method to an Object:**

   You can add a function (method) to an object by defining a property with a function value. Here's how you can add a `getFullName` method to the `person` object:

   ```javascript
   person.getFullName = function () {
     return this.firstName + " " + this.lastName;
   };
   ```

   Now, you can call this method on the `person` object:

   ```javascript
   console.log(person.getFullName()); // Output: "John Doe"
   ```

3. **Using `this` Keyword:**

   Inside the method, we use the `this` keyword to refer to the object itself. This allows you to access the object's properties within the method.

4. **Constructor Functions:**

   Another way to create objects with methods is by using constructor functions. Constructor functions are used to create multiple instances of an object. Here's an example:

   ```javascript
   function Car(make, model) {
     this.make = make;
     this.model = model;
     this.start = function () {
       console.log(`Starting the ${this.make} ${this.model}`);
     };
   }

   const myCar = new Car("Toyota", "Camry");
   myCar.start(); // Output: "Starting the Toyota Camry"
   ```

   In this example, the `Car` constructor function creates instances of `Car` objects, each with a `start` method.

5. **Object Methods with ES6 Classes:**

   In modern JavaScript, you can also use ES6 classes to define objects and their methods in a more organized way. Here's an example using a class:

   ```javascript
   class Dog {
     constructor(name, breed) {
       this.name = name;
       this.breed = breed;
     }

     bark() {
       console.log(`${this.name} is barking!`);
     }
   }

   const myDog = new Dog("Buddy", "Golden Retriever");
   myDog.bark(); // Output: "Buddy is barking!"
   ```

# JavaScript 'This' keyword.

In JavaScript, the `this` keyword refers to the current execution context, which can vary depending on how and where a function is called. Understanding `this` is crucial for working with object-oriented programming, event handling, and various JavaScript patterns.

1. Global Context:
   In the global context, `this` refers to the global object, which is usually `window` in a web browser.

```javascript
console.log(this); // Outputs the global object (e.g., window in a browser)
```

2. Function Context:
   Inside a regular function, `this` typically refers to the global object (window), unless the function is in strict mode.

```javascript
function myFunction() {
  console.log(this); // Outputs the global object (window in a browser)
}

myFunction();
```

3. Object Methods:
   When a function is a method of an object, `this` refers to the object itself.

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  fullName: function () {
    console.log(this.firstName + " " + this.lastName);
  },
};

person.fullName(); // Outputs "John Doe"
```

4. Event Handlers:
   In event handler functions, `this` often refers to the DOM element that triggered the event.

```html
<button id="myButton">Click me</button>

<script>
  document.getElementById("myButton").addEventListener("click", function () {
    console.log(this); // Outputs the button element
  });
</script>
```

5. Constructor Functions:
   Inside constructor functions, `this` refers to the newly created object.

```javascript
function Car(make, model) {
  this.make = make;
  this.model = model;
}

const myCar = new Car("Toyota", "Camry");
console.log(myCar.make); // Outputs "Toyota"
```

6. Arrow Functions:
   Arrow functions do not have their own `this` context. They inherit the `this` value from the surrounding code.

```javascript
const obj = {
  value: 42,
  getValue: () => {
    console.log(this.value); // 'this' refers to the enclosing scope (e.g., global scope)
  },
};

obj.getValue(); // Outputs undefined (value is not in the global scope)
```

7. Call and Apply Methods:
   You can explicitly set the `this` context using the `call()` or `apply()` methods of a function.

```javascript
const person1 = { name: "Alice" };
const person2 = { name: "Bob" };

function greet() {
  console.log(`Hello, ${this.name}`);
}

greet.call(person1); // Outputs "Hello, Alice"
greet.call(person2); // Outputs "Hello, Bob"
```
