# Contents to be covered in this session.

## 1. JavaScript Polymorphism.

## 2. When to use inheritance in JavaScript.

## 3. JavaScript Mixins.

## 4. JS Advanced.

## 5. ES6 Version.

## 6. ES6 Classes.

## 7. ES6 this keyword.



# JavaScript Polymorphism.

Polymorphism is a fundamental concept in object-oriented programming that allows objects of different classes to be treated as objects of a common base class. In JavaScript, polymorphism is achieved through the use of prototypes and inheritance.

1. **Basic Polymorphism with Inheritance**:

   ```javascript
   // Base class
   function Animal(name) {
       this.name = name;
   }

   // Derived class
   function Dog(name) {
       Animal.call(this, name);
   }

   Dog.prototype = Object.create(Animal.prototype);

   // Polymorphic function
   function animalSound(animal) {
       console.log(`${animal.name} makes a sound.`);
   }

   // Usage
   const cat = new Animal("Whiskers");
   const dog = new Dog("Fido");

   animalSound(cat); // Whiskers makes a sound.
   animalSound(dog); // Fido makes a sound.
   ```

2. **Polymorphism with Interfaces**:

   In JavaScript, there's no native support for interfaces, but you can achieve a similar effect using duck typing.

   ```javascript
   // Interface
   function CanSpeak() {}

   CanSpeak.prototype.speak = function() {
       throw new Error("Subclasses must implement the speak method.");
   };

   // Implementing interface
   function Dog(name) {
       this.name = name;
   }

   Dog.prototype.speak = function() {
       console.log(`${this.name} says Woof!`);
   };

   function Cat(name) {
       this.name = name;
   }

   Cat.prototype.speak = function() {
       console.log(`${this.name} says Meow!`);
   }

   // Usage
   const dog = new Dog("Fido");
   const cat = new Cat("Whiskers");

   function makePetSpeak(pet) {
       if (pet instanceof CanSpeak) {
           pet.speak();
       } else {
           console.log("This pet can't speak.");
       }
   }

   makePetSpeak(dog); // Fido says Woof!
   makePetSpeak(cat); // Whiskers says Meow!
   ```

3. **Polymorphism with Class Extensions (ES6)**:

   Modern JavaScript supports class syntax which simplifies polymorphism:

   ```javascript
   // Base class
   class Animal {
       constructor(name) {
           this.name = name;
       }

       makeSound() {
           console.log(`${this.name} makes a sound.`);
       }
   }

   // Derived class
   class Dog extends Animal {
       makeSound() {
           console.log(`${this.name} says Woof!`);
       }
   }

   class Cat extends Animal {
       makeSound() {
           console.log(`${this.name} says Meow!`);
       }
   }

   // Usage
   const cat = new Cat("Whiskers");
   const dog = new Dog("Fido");

   cat.makeSound(); // Whiskers says Meow!
   dog.makeSound(); // Fido says Woof!
   ```


# When to use inheritance in JavaScript.

Inheritance in JavaScript is a mechanism that allows one object to inherit properties and methods from another object. This concept is often used in object-oriented programming to create relationships between objects, and it's essential for building complex and maintainable code. There are several ways to implement inheritance in JavaScript, including prototype-based inheritance, ES6 class-based inheritance, and mixins.

1. **Code Reusability**: Inheritance is useful when you have objects that share common properties and methods. By creating a parent (superclass) object and having child (subclass) objects inherit from it, you can avoid code duplication and ensure that changes to shared functionality are applied consistently.

2. **Creating Object Hierarchies**: Inheritance is used to define relationships between objects. For example, you might have a base "Shape" class and subclasses like "Circle" and "Rectangle" that inherit properties and methods from the base class. This helps maintain a logical hierarchy in your code.

3. **Polymorphism**: Inheritance enables polymorphism, which allows different objects to respond to the same method call in a way that's appropriate for their specific type. This is often used in design patterns like the Strategy or Factory patterns.

4. **Extending Built-in Objects**: You can extend or modify the behavior of built-in JavaScript objects (like `Array`, `Object`, or `String`) using inheritance. Be cautious when doing this, as it can lead to unexpected behavior and conflicts if not done carefully.

Here are two common approaches to implementing inheritance in JavaScript:

- **Prototype-Based Inheritance**: This is the traditional way of achieving inheritance in JavaScript. You create a prototype chain where objects inherit from other objects. You use the `prototype` property to define shared methods and properties. Subclasses are created by setting their prototypes to instances of the parent class.

```javascript
function Parent() {
  this.property = 'value';
}

Parent.prototype.method = function() {
  // ...
};

function Child() {
  // Constructor chaining
  Parent.call(this);
  // ...
}

Child.prototype = Object.create(Parent.prototype);
Child.prototype.constructor = Child;
```

- **Class-Based Inheritance (ES6)**: With the introduction of ES6, JavaScript has a more familiar class-based syntax for inheritance. While it's syntactic sugar over prototype-based inheritance, it's easier to understand for developers familiar with object-oriented programming in other languages.

```javascript
class Parent {
  constructor() {
    this.property = 'value';
  }

  method() {
    // ...
  }
}

class Child extends Parent {
  constructor() {
    super(); // Call the parent constructor
    // ...
  }
}
```


# JavaScript Mixins.

Mixins in JavaScript are a way to reuse and share behavior among objects without using traditional inheritance. They allow you to compose objects by mixing in functionality from other objects or modules. Below are some code examples to demonstrate the concept of mixins in JavaScript:

**Example 1: Basic Mixin**

```javascript
// Define a mixin object with some methods
const carMixin = {
  startEngine() {
    console.log('Engine started');
  },
  stopEngine() {
    console.log('Engine stopped');
  }
};

// Create an object and mix in the carMixin
const myCar = {};

Object.assign(myCar, carMixin);

myCar.startEngine();  // Output: Engine started
myCar.stopEngine();   // Output: Engine stopped
```

In this example, we created a `carMixin` object with methods to start and stop the engine. We then mixed these methods into the `myCar` object using `Object.assign`.

**Example 2: Mixin with Parameters**

```javascript
// Define a mixin that accepts parameters
const withLogging = {
  log(message) {
    console.log(message);
  }
};

// Create an object and mix in the withLogging mixin
const user = {
  name: "John"
};

Object.assign(user, withLogging);

user.log("User created");  // Output: User created
```

In this example, we defined a `withLogging` mixin that provides a `log` method, and we mixed it into the `user` object.

**Example 3: Mixin Factory Function**

You can also use a function to create mixins:

```javascript
function createMixin(base) {
  return {
    sayHello() {
      console.log(`Hello from ${base.name}`);
    }
  };
}

const person = {
  name: "Alice"
};

const greetablePerson = createMixin(person);

greetablePerson.sayHello();  // Output: Hello from Alice
```

Here, we created a `createMixin` function that accepts a base object and returns a mixin with a `sayHello` method. We then used it to create `greetablePerson`.

**Example 4: Multiple Mixins**

You can combine multiple mixins into a single object:

```javascript
const canWalkMixin = {
  walk() {
    console.log("Walking...");
  }
};

const canSwimMixin = {
  swim() {
    console.log("Swimming...");
  }
};

const canFlyMixin = {
  fly() {
    console.log("Flying...");
  }
};

const superhero = {};
Object.assign(superhero, canWalkMixin, canFlyMixin);
superhero.walk();  // Output: Walking...
superhero.fly();   // Output: Flying...
```


# JS Advanced.

JavaScript (JS) is a versatile programming language used for web development, among other things. It's a crucial part of building interactive and dynamic web applications. I'll provide you with some advanced JavaScript concepts and code examples to help you better understand how to use them.

1. **Closures:**
   Closures allow functions to "remember" their lexical scope even after they've finished executing. They are used to create private variables and maintain state.

   ```javascript
   function outer() {
     let outerVar = 'I am from outer!';
     function inner() {
       console.log(outerVar);
     }
     return inner;
   }

   const innerFunc = outer();
   innerFunc(); // Outputs: "I am from outer!"
   ```

2. **Promises and Async/Await:**
   Promises are used for handling asynchronous operations. Async/await is a more readable way to work with promises.

   ```javascript
   function fetchData() {
     return new Promise((resolve, reject) => {
       setTimeout(() => resolve('Data fetched!'), 1000);
     });
   }

   async function getData() {
     try {
       const data = await fetchData();
       console.log(data);
     } catch (error) {
       console.error(error);
     }
   }

   getData(); // After 1 second, it logs: "Data fetched!"
   ```

3. **ES6 Classes:**
   ES6 introduced class syntax to JavaScript, making it easier to create and manage object-oriented code.

   ```javascript
   class Person {
     constructor(name, age) {
       this.name = name;
       this.age = age;
     }

     sayHello() {
       console.log(`Hello, my name is ${this.name} and I'm ${this.age} years old.`);
     }
   }

   const person1 = new Person('Alice', 25);
   person1.sayHello(); // Outputs: "Hello, my name is Alice and I'm 25 years old."
   ```

4. **Modules (ES6):**
   ES6 introduced a module system for organizing and encapsulating code.

   **math.js**
   ```javascript
   export function add(a, b) {
     return a + b;
   }
   ```

   **app.js**
   ```javascript
   import { add } from './math.js';

   console.log(add(5, 3)); // Outputs: 8
   ```

5. **Event Handling:**
   JavaScript allows you to handle user interactions with events.

   ```javascript
   const button = document.getElementById('myButton');
   button.addEventListener('click', function() {
     alert('Button clicked!');
   });
   ```

6. **Local Storage:**
   You can use `localStorage` to store data on the client's browser.

   ```javascript
   localStorage.setItem('username', 'john_doe');
   const username = localStorage.getItem('username');
   console.log(username); // Outputs: "john_doe"
   ```

7. **API Requests:**
   JavaScript is often used to make API requests and process the responses.

   ```javascript
   fetch('https://jsonplaceholder.typicode.com/posts/1')
     .then(response => response.json())
     .then(data => console.log(data));
   ```

8. **Error Handling:**
   Proper error handling is essential for robust code.

   ```javascript
   try {
     // Code that might throw an error
     throw new Error('Something went wrong!');
   } catch (error) {
     console.error(error.message);
   }
   ```


# ES6 Version.

ES6, or ECMAScript 2015, is a major update to the JavaScript language. It introduced several new features and syntax improvements that make JavaScript more powerful and expressive.

1. **let and const**: ES6 introduced block-scoped variables using `let` and `const` which are more predictable than `var`.

   ```javascript
   let x = 10; // Can be reassigned
   const y = 20; // Constant, cannot be reassigned
   ```

2. **Arrow Functions**: Arrow functions provide a concise syntax for writing functions.

   ```javascript
   // Regular function
   function add(a, b) {
       return a + b;
   }

   // Arrow function
   const add = (a, b) => a + b;
   ```

3. **Template Literals**: Template literals allow you to interpolate variables into strings.

   ```javascript
   const name = "Alice";
   console.log(`Hello, ${name}!`);
   ```

4. **Destructuring**: Easily extract values from objects and arrays.

   ```javascript
   const person = { name: "Bob", age: 30 };
   const { name, age } = person;

   const [first, second] = [1, 2];
   ```

5. **Spread and Rest Operators**: Spread operator (`...`) spreads elements of an array or object, and the rest operator collects elements into an array.

   ```javascript
   const arr = [1, 2, 3];
   const newArr = [...arr, 4, 5];

   const { a, b, ...rest } = { a: 1, b: 2, c: 3 };
   ```

6. **Classes**: ES6 introduced a class syntax for defining objects and their behavior.

   ```javascript
   class Person {
       constructor(name) {
           this.name = name;
       }
       sayHello() {
           console.log(`Hello, my name is ${this.name}`);
       }
   }
   ```

7. **Promises**: Promises provide a cleaner way to work with asynchronous code.

   ```javascript
   function fetchData() {
       return new Promise((resolve, reject) => {
           // Asynchronous operation
           if (success) {
               resolve(data);
           } else {
               reject(error);
           }
       });
   }
   ```

8. **Modules**: ES6 introduced a standardized module system, allowing you to easily export and import code between files.

   ```javascript
   // math.js
   export function add(a, b) {
       return a + b;
   }

   // main.js
   import { add } from './math';
   ```

9. **Default Parameters**: You can specify default values for function parameters.

   ```javascript
   function greet(name = "World") {
       console.log(`Hello, ${name}!`);
   }
   ```

10. **Map and Set**: ES6 introduced new data structures, `Map` and `Set`, for key-value pairs and unique values, respectively.

   ```javascript
   const myMap = new Map();
   myMap.set("key", "value");

   const mySet = new Set();
   mySet.add(1);
   mySet.add(2);
   ```


# ES6 Classes.

ES6 (ECMAScript 2015) introduced classes to JavaScript, providing a more structured and syntactically cleaner way to create and work with objects. 

1. **Basic Class Declaration:**

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  sayHello() {
    console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
  }
}

const person1 = new Person('Alice', 30);
person1.sayHello(); // Hello, my name is Alice and I am 30 years old.
```

2. **Inheritance:**

You can create a subclass that extends another class.

```javascript
class Student extends Person {
  constructor(name, age, grade) {
    super(name, age);
    this.grade = grade;
  }

  study() {
    console.log(`${this.name} is studying in grade ${this.grade}.`);
  }
}

const student1 = new Student('Bob', 18, 12);
student1.sayHello(); // Hello, my name is Bob and I am 18 years old.
student1.study();    // Bob is studying in grade 12.
```

3. **Getter and Setter Methods:**

You can define getter and setter methods for class properties.

```javascript
class Circle {
  constructor(radius) {
    this._radius = radius;
  }

  get radius() {
    return this._radius;
  }

  set radius(value) {
    if (value < 0) {
      console.log("Radius cannot be negative.");
      return;
    }
    this._radius = value;
  }

  get area() {
    return Math.PI * Math.pow(this._radius, 2);
  }
}

const myCircle = new Circle(5);
console.log(myCircle.radius); // 5
myCircle.radius = 7;
console.log(myCircle.radius); // 7
console.log(myCircle.area);   // 153.93804002589985
```

4. **Static Methods:**

Static methods are called on the class itself, not on instances.

```javascript
class MathUtil {
  static add(x, y) {
    return x + y;
  }

  static multiply(x, y) {
    return x * y;
  }
}

console.log(MathUtil.add(3, 4));       // 7
console.log(MathUtil.multiply(2, 5));  // 10
```

5. **Class Expressions:**

Classes can also be defined as expressions.

```javascript
const Animal = class {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound.`);
  }
};

const dog = new Animal('Dog');
dog.speak(); // Dog makes a sound.
```

6. **Using Constructors and Prototypes:**

ES6 classes provide a cleaner syntax for creating objects and defining methods, but under the hood, they are still based on prototypes. Here's how you can create a class that is equivalent to traditional constructor functions and prototypes:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.sayHello = function() {
  console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
};

const person2 = new Person('Eve', 25);
person2.sayHello(); // Hello, my name is Eve and I am 25 years old.
```


# ES6 this keyword.

In ECMAScript 6 (ES6), the `this` keyword in class constructors and methods behaves similarly to the way it works in traditional JavaScript. However, ES6 introduced some changes and features that can affect the behavior of `this`.

1. `this` in a class constructor:

```javascript
class Person {
  constructor(name) {
    this.name = name;
  }

  sayHello() {
    console.log(`Hello, my name is ${this.name}`);
  }
}

const person1 = new Person('Alice');
person1.sayHello(); // Output: Hello, my name is Alice
```

In this example, `this` refers to the instance of the class (i.e., `person1`) within the constructor and the `sayHello` method.

2. `this` in an arrow function within a class:

```javascript
class Counter {
  constructor() {
    this.count = 0;
  }

  increaseCount() {
    setInterval(() => {
      console.log(`Current count: ${this.count}`);
      this.count++;
    }, 1000);
  }
}

const counter = new Counter();
counter.increaseCount();
```

In this case, using an arrow function within the `setInterval` callback allows us to capture the lexical `this`, which refers to the `Counter` instance. If you used a regular function instead of an arrow function, you would need to bind `this` explicitly.

3. Binding `this` using `.bind()`:

```javascript
class Button {
  constructor(label) {
    this.label = label;
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    console.log(`Clicked the ${this.label} button`);
  }
}

const button1 = new Button('Submit');
const button2 = new Button('Cancel');

document.getElementById('submit-button').addEventListener('click', button1.handleClick);
document.getElementById('cancel-button').addEventListener('click', button2.handleClick);
```

In this example, we explicitly bind `this` to the `handleClick` method in the constructor to ensure that `this` inside the event listener refers to the specific instance. Otherwise, `this` would refer to the element that triggered the event.

4. Using arrow functions directly as class methods:

In ES6, you can also use arrow functions directly as class methods, which automatically bind `this` to the class instance:

```javascript
class Calculator {
  add = (a, b) => {
    return a + b;
  }
}

const calc = new Calculator();
console.log(calc.add(5, 3)); // Output: 8
```


