# Contents to be covered in this session.

## 1. JavaScript Multilevel Inheritance.

## 2. JavaScript changing this (call, bind, apply).

## 3. JavaScript Property Descriptors.

## 4. JavaScript Constructor Prototypes.

## 5. JavaScript Prototype vs instance members.

## 6. JavaScript Iterating Instance and Prototype Members.

## 7. JavaScript Avoid Extending the Built-in Objects.

## 8. JavaScript Prototype Inheritance.

## 9. JavaScript - Creating own Prototypical Inheritance.

## 10. JavaScript - Resetting the Constructor.

## 11. JavaScript - Calling the Super Constructor.

## 12. JavaScript - Intermediate Function Inheritance.

## 13. JavaScript - Method Overriding.

# JavaScript Multilevel Inheritance.

In JavaScript, you can achieve multilevel inheritance by creating a chain of constructor functions and using prototypes to inherit properties and methods from parent constructors.

```javascript
// Parent class (Superclass)
function Animal(name) {
  this.name = name;
}

Animal.prototype.eat = function () {
  console.log(this.name + " is eating.");
};

// Intermediate class (Subclass 1)
function Bird(name) {
  // Call the constructor of the parent class
  Animal.call(this, name);
}

// Inherit methods from the parent class
Bird.prototype = Object.create(Animal.prototype);

Bird.prototype.fly = function () {
  console.log(this.name + " is flying.");
};

// Subclass of Bird (Subclass 2, multilevel inheritance)
function Parrot(name) {
  // Call the constructor of the intermediate class (Bird)
  Bird.call(this, name);
}

// Inherit methods from the intermediate class (Bird)
Parrot.prototype = Object.create(Bird.prototype);

Parrot.prototype.talk = function () {
  console.log(this.name + " is talking.");
};

// Create instances of the classes
const eagle = new Bird("Eagle");
const africanGrey = new Parrot("African Grey");

eagle.eat(); // Output: Eagle is eating.
eagle.fly(); // Output: Eagle is flying.
africanGrey.eat(); // Output: African Grey is eating.
africanGrey.fly(); // Output: African Grey is flying.
africanGrey.talk(); // Output: African Grey is talking.
```

In this example:

1. We define a parent class `Animal` with a constructor function and a prototype method `eat`.
2. We create an intermediate class `Bird` that inherits from `Animal`. We use `Object.create(Animal.prototype)` to set the prototype of `Bird` to an object with `Animal`'s prototype. This allows `Bird` instances to inherit the `eat` method.
3. We define a new subclass `Parrot` that inherits from `Bird` in a similar way.
4. We create instances of `Bird` and `Parrot`, and they inherit methods from both their parent and intermediate classes, demonstrating multilevel inheritance.

# JavaScript changing this (call, bind, apply).

In JavaScript, you can change the value of the `this` keyword within a function using the `call`, `apply`, and `bind` methods. These methods are used to explicitly set the context (the object to which `this` refers) when calling a function.

1. **Using `call` method:**

The `call` method allows you to call a function with a specific `this` value and any number of arguments passed individually.

```javascript
const person = {
  name: "John",
};

function greet(message) {
  console.log(`${message}, ${this.name}!`);
}

greet.call(person, "Hello"); // Output: Hello, John!
```

In this example, we use `call` to call the `greet` function with the `person` object as the `this` value.

2. **Using `apply` method:**

The `apply` method is similar to `call`, but it takes an array of arguments.

```javascript
const person = {
  name: "John",
};

function greet(message1, message2) {
  console.log(`${message1} ${message2}, ${this.name}!`);
}

greet.apply(person, ["Hello", "there"]); // Output: Hello there, John!
```

Here, we use `apply` to pass an array of arguments to the `greet` function.

3. **Using `bind` method:**

The `bind` method creates a new function with a specified `this` value and, optionally, preset arguments.

```javascript
const person = {
  name: "John",
};

function greet(message) {
  console.log(`${message}, ${this.name}!`);
}

const greetJohn = greet.bind(person);
greetJohn("Hi"); // Output: Hi, John!
```

# JavaScript Property Descriptors.

In JavaScript, property descriptors are objects that define the attributes of an object's property, such as whether it's writable, enumerable, or configurable. You can access and manipulate these descriptors using the `Object.getOwnPropertyDescriptor()`, `Object.defineProperty()`, and `Object.defineProperties()` methods. Here are some code examples to demonstrate property descriptors:

1. Getting Property Descriptors:

You can use `Object.getOwnPropertyDescriptor()` to get the descriptor of a property in an object.

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
};

const descriptor = Object.getOwnPropertyDescriptor(person, "firstName");
console.log(descriptor);
```

Output:

```javascript
{
  value: 'John',
  writable: true,
  enumerable: true,
  configurable: true
}
```

2. Modifying Property Descriptors:

You can use `Object.defineProperty()` to modify property descriptors.

```javascript
const car = {};
Object.defineProperty(car, "color", {
  value: "red",
  writable: false,
  enumerable: true,
  configurable: true,
});

console.log(car.color); // Output: 'red'
car.color = "blue"; // Throws an error in strict mode or silently fails in non-strict mode.
```

3. Creating Multiple Properties with Descriptors:

You can use `Object.defineProperties()` to define multiple properties with descriptors in a single object.

```javascript
const person = {};
Object.defineProperties(person, {
  firstName: {
    value: "John",
    writable: true,
    enumerable: true,
    configurable: true,
  },
  lastName: {
    value: "Doe",
    writable: true,
    enumerable: true,
    configurable: true,
  },
});

console.log(person.firstName); // Output: 'John'
```

4. Making a Property Non-enumerable:

You can set `enumerable` to `false` to make a property non-enumerable, meaning it won't show up in `for...in` loops.

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
};

Object.defineProperty(person, "age", {
  value: 30,
  enumerable: false,
  writable: true,
  configurable: true,
});

for (let key in person) {
  console.log(key); // Output: 'firstName' and 'lastName'
}
```

5. Making a Property Immutable:

You can set `writable` to `false` to make a property read-only.

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
};

Object.defineProperty(person, "firstName", {
  writable: false,
});

person.firstName = "Jane"; // Throws an error in strict mode or silently fails in non-strict mode.
```

6. Preventing Property Deletion:

You can set `configurable` to `false` to prevent a property from being deleted or having its attributes modified.

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
};

Object.defineProperty(person, "firstName", {
  configurable: false,
});

delete person.firstName; // Throws an error in strict mode or silently fails in non-strict mode.
```

# JavaScript Constructor Prototypes.

In JavaScript, constructors and prototypes are important concepts for creating and working with objects. Constructors are functions used to create objects, and prototypes are used to define properties and methods that can be shared among objects of the same type.

**1. Constructors:**

Constructors are functions that create and initialize objects. They are typically named with an initial capital letter and are used with the `new` keyword. When a constructor is called with `new`, a new object is created, and `this` refers to the newly created object.

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Create instances using the constructor
const person1 = new Person("Alice", 30);
const person2 = new Person("Bob", 25);

console.log(person1.name); // Output: "Alice"
console.log(person2.age); // Output: 25
```

**2. Prototypes:**

Prototypes allow you to share properties and methods among objects created by the same constructor. By adding properties and methods to a constructor's prototype, you ensure that all instances of that constructor inherit those properties and methods.

```javascript
// Add a method to the Person constructor's prototype
Person.prototype.sayHello = function () {
  console.log(`Hello, my name is ${this.name}, and I'm ${this.age} years old.`);
};

person1.sayHello(); // Output: "Hello, my name is Alice, and I'm 30 years old."
person2.sayHello(); // Output: "Hello, my name is Bob, and I'm 25 years old."
```

**3. Inheritance with Prototypes:**

You can also achieve inheritance using prototypes. For example, you can create a new constructor that inherits properties and methods from an existing constructor's prototype.

```javascript
function Student(name, age, school) {
  // Call the parent constructor to initialize name and age
  Person.call(this, name, age);
  this.school = school;
}

// Inherit methods from the Person prototype
Student.prototype = Object.create(Person.prototype);

// Add a method specific to Student
Student.prototype.saySchool = function () {
  console.log(`I go to ${this.school}.`);
};

const student = new Student("Eve", 20, "University X");
student.sayHello(); // Output: "Hello, my name is Eve, and I'm 20 years old."
student.saySchool(); // Output: "I go to University X."
```

In the example above, we created a `Student` constructor that inherits the `sayHello` method from the `Person` prototype and also has its own method, `saySchool`.

# JavaScript Prototype vs instance members.

In JavaScript, you can define members (properties and methods) on objects and their prototypes. Understanding the difference between instance members and prototype members is crucial in JavaScript.

### Instance Members:

Instance members are properties and methods that are specific to individual objects created from a constructor function or a class. Each instance of an object has its own copy of these members.

```javascript
// Constructor Function
function Person(name, age) {
  this.name = name; // Instance property
  this.age = age; // Instance property
}

Person.prototype.greet = function () {
  console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
};

// Creating instances
const person1 = new Person("Alice", 25);
const person2 = new Person("Bob", 30);

person1.greet(); // Output: Hello, my name is Alice and I am 25 years old.
person2.greet(); // Output: Hello, my name is Bob and I am 30 years old.
```

In the code above, `name` and `age` are instance properties, and the `greet` function is an instance method. Each instance of the `Person` constructor has its own `name` and `age` properties, but they share the same `greet` method.

### Prototype Members:

Prototype members are properties and methods defined on the prototype object of a constructor function or class. These members are shared among all instances created from the constructor function, helping to save memory as they are not duplicated for each instance.

```javascript
// Constructor Function
function Car(make, model) {
  this.make = make; // Instance property
  this.model = model; // Instance property
}

Car.prototype.drive = function () {
  console.log(`I'm driving a ${this.make} ${this.model}.`);
};

// Creating instances
const car1 = new Car("Toyota", "Camry");
const car2 = new Car("Honda", "Civic");

car1.drive(); // Output: I'm driving a Toyota Camry.
car2.drive(); // Output: I'm driving a Honda Civic.
```

# JavaScript Iterating Instance and Prototype Members.

In JavaScript, you can iterate over instance and prototype members of an object. Instance members are properties and methods that belong to a specific object, while prototype members are properties and methods shared across multiple objects through their prototype chain.

1. Iterating Instance Members:

   Instance members are specific to a particular object and are defined within the object itself. You can iterate over them using a `for...in` loop or `Object.keys()` method.

```javascript
// Define a constructor function
function Person(name, age) {
  this.name = name; // Instance property
  this.age = age; // Instance property
}

// Add an instance method to the prototype
Person.prototype.sayHello = function () {
  console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
};

// Create an instance
const person1 = new Person("Alice", 30);

// Iterate over instance members using for...in loop
for (let key in person1) {
  if (person1.hasOwnProperty(key)) {
    console.log(`Instance property: ${key} = ${person1[key]}`);
  }
}
```

2. Iterating Prototype Members:

   Prototype members are shared among all instances created from the same constructor function. You can access them through the prototype object of the constructor function. To iterate over prototype members, you can use a `for...in` loop or `Object.keys()` on the prototype object.

```javascript
// Using the same Person constructor function from the previous example

// Create another instance
const person2 = new Person("Bob", 25);

// Iterate over prototype members using for...in loop
for (let key in Person.prototype) {
  if (Person.prototype.hasOwnProperty(key)) {
    console.log(`Prototype property: ${key} = ${Person.prototype[key]}`);
  }
}
```

In modern JavaScript, you can use `Object.getOwnPropertyNames()` and `Object.getOwnPropertySymbols()` to retrieve all own properties (including non-enumerable properties) of an object.

```javascript
// Iterating all own properties (instance + prototype)
const allProperties = Object.getOwnPropertyNames(person1).concat(
  Object.getOwnPropertyNames(Person.prototype)
);
for (let key of allProperties) {
  console.log(`All own property: ${key}`);
}
```

# JavaScript Avoid Extending the Built-in Objects.

Extending built-in objects in JavaScript can lead to unexpected and error-prone behavior, and it's generally considered a bad practice. It can create compatibility issues with other code and libraries, as well as future updates to the language.

1. **Compatibility Issues:** Extending built-in objects can lead to conflicts with other libraries or code that may have also extended these objects in different ways. This can result in unpredictable behavior and hard-to-debug issues.

2. **Maintainability:** It makes your code harder to understand and maintain since it's not immediately clear where certain methods or properties come from.

3. **Future Updates:** JavaScript is an evolving language. Future versions may introduce new methods and properties on built-in objects, and your extensions could break when you update your environment or libraries.

Here are a few code examples that demonstrate the problems with extending built-in objects:

**1. Extending the Array prototype:**

```javascript
// Extending the Array prototype
Array.prototype.sum = function () {
  return this.reduce((acc, val) => acc + val, 0);
};

const numbers = [1, 2, 3];
console.log(numbers.sum()); // Outputs 6

// The problem is that the 'sum' method could become a standard method in future JavaScript versions
// or other libraries may already use 'sum' for a different purpose, causing conflicts.
```

**2. Extending the String prototype:**

```javascript
// Extending the String prototype
String.prototype.capitalize = function () {
  return this.charAt(0).toUpperCase() + this.slice(1);
};

const name = "john";
console.log(name.capitalize()); // Outputs 'John'

// The problem here is that if 'capitalize' becomes a standard method in the String prototype in the future,
// it will lead to conflicts and unexpected behavior.
```

**3. Extending the Object prototype:**

```javascript
// Extending the Object prototype
Object.prototype.isEmpty = function () {
  for (let key in this) {
    if (this.hasOwnProperty(key)) {
      return false;
    }
  }
  return true;
};

const data = { name: "John", age: 30 };
console.log(data.isEmpty()); // Outputs false

// The problem is that this extension can lead to issues when iterating over objects or using libraries that
// rely on the standard behavior of objects.
```

To avoid these problems, it's better to create your own utility functions or classes to encapsulate the behavior you need, rather than extending the built-in objects. This approach makes your code more maintainable and less prone to conflicts with other code.

# JavaScript Prototype Inheritance.

JavaScript uses prototype-based inheritance, which means that objects can inherit properties and methods from other objects. In JavaScript, each object has an associated prototype object, and you can use this prototype chain to create inheritance relationships.

**1. Creating a Constructor Function:**

You can create a constructor function to define the properties and methods of an object. Then, you can add methods to the constructor function's prototype to make those methods available to all instances created from that constructor.

```javascript
// Constructor function for a Person
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Adding a method to the Person prototype
Person.prototype.sayHello = function () {
  console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
};

// Creating instances of Person
const person1 = new Person("Alice", 30);
const person2 = new Person("Bob", 25);

// Calling the sayHello method
person1.sayHello();
person2.sayHello();
```

**2. Inheriting from Another Object:**

You can use the `Object.create` method to create a new object that inherits from an existing object's prototype.

```javascript
// Parent constructor function
function Animal(name) {
  this.name = name;
}

// Adding a method to the Animal prototype
Animal.prototype.speak = function () {
  console.log(`${this.name} makes a sound.`);
};

// Child constructor function inheriting from Animal
function Dog(name, breed) {
  Animal.call(this, name);
  this.breed = breed;
}

// Inheriting Animal's prototype
Dog.prototype = Object.create(Animal.prototype);

// Adding a method specific to Dog
Dog.prototype.bark = function () {
  console.log(`${this.name} the ${this.breed} barks.`);
};

const myDog = new Dog("Buddy", "Golden Retriever");
myDog.speak(); // Inherited from Animal
myDog.bark(); // Specific to Dog
```

**3. Class Syntax (ES6):**

JavaScript also introduced class syntax to make working with prototypes more intuitive. It's essentially syntactic sugar for the prototype-based inheritance we saw earlier. Here's the previous example using class syntax:

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name);
    this.breed = breed;
  }

  bark() {
    console.log(`${this.name} the ${this.breed} barks.`);
  }
}

const myDog = new Dog("Buddy", "Golden Retriever");
myDog.speak();
myDog.bark();
```

# JavaScript - Creating own Prototypical Inheritance.

In JavaScript, you can create your own prototypical inheritance by using constructors and prototypes. This allows you to define a "class" with shared methods and properties that can be inherited by instances of that class.

```javascript
// Define a constructor function
function Animal(name) {
  this.name = name;
}

// Add a method to the prototype of the Animal constructor
Animal.prototype.sayHello = function () {
  console.log(`Hello, I'm ${this.name}`);
};

// Create a new instance of Animal
const cat = new Animal("Whiskers");
const dog = new Animal("Buddy");

// Call the shared method
cat.sayHello(); // Output: Hello, I'm Whiskers
dog.sayHello(); // Output: Hello, I'm Buddy
```

You can also create a subclass by inheriting from a parent class. Here's an example of how to do that:

```javascript
// Define a subclass constructor
function Dog(name, breed) {
  // Call the parent constructor to initialize the name property
  Animal.call(this, name);
  this.breed = breed;
}

// Inherit from the Animal prototype
Dog.prototype = Object.create(Animal.prototype);

// Add a method to the Dog prototype
Dog.prototype.bark = function () {
  console.log(`${this.name} (a ${this.breed} dog) barks: Woof, woof!`);
};

// Create a new instance of Dog
const myDog = new Dog("Rex", "Golden Retriever");

myDog.sayHello(); // Output: Hello, I'm Rex
myDog.bark(); // Output: Rex (a Golden Retriever dog) barks: Woof, woof!
```

# JavaScript - Resetting the Constructor.

In JavaScript, you can't directly reset the constructor of an object after it has been created. The constructor of an object is set at the time of the object's creation and is a read-only property. However, you can achieve a similar effect by creating a new object with a different constructor.

1. Changing the Constructor of an Object:

```javascript
function Car(make, model) {
  this.make = make;
  this.model = model;
}

const myCar = new Car("Toyota", "Camry");
console.log(myCar.constructor); // Outputs: [Function: Car]

// Create a new object with a different constructor
function Motorcycle(make, model) {
  this.make = make;
  this.model = model;
}

const myMotorcycle = new Motorcycle("Harley-Davidson", "Sportster");
console.log(myMotorcycle.constructor); // Outputs: [Function: Motorcycle]
```

In this example, we change the constructor of `myCar` by creating a new object `myMotorcycle` with a different constructor.

2. Copying Properties to a New Object:

You can also copy the properties of an existing object to a new object with a different constructor:

```javascript
function Car(make, model) {
  this.make = make;
  this.model = model;
}

const myCar = new Car("Toyota", "Camry");
console.log(myCar.constructor); // Outputs: [Function: Car]

// Create a new object with a different constructor and copy properties
function Motorcycle(make, model) {
  this.make = make;
  this.model = model;
}

const myMotorcycle = new Motorcycle();
Object.assign(myMotorcycle, myCar);
console.log(myMotorcycle.constructor); // Outputs: [Function: Motorcycle]
```

# JavaScript - Calling the Super Constructor.

In JavaScript, you can call the super constructor of a parent class in an ES6 class using the `super()` method. This is commonly used when you want to initialize properties and perform setup tasks defined in the parent class's constructor before customizing the child class's behavior.

1. Calling the Super Constructor in a Subclass:

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound`);
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Call the parent class constructor with 'name'
    this.breed = breed;
  }

  speak() {
    console.log(`${this.name} barks!`);
  }
}

const myDog = new Dog("Buddy", "Golden Retriever");
myDog.speak(); // Output: Buddy barks!
```

In this example, the `Dog` class extends the `Animal` class. The `super(name)` call in the `Dog` constructor invokes the parent class's constructor, passing the `name` parameter to initialize the `name` property inherited from the `Animal` class.

2. Using super() with No Additional Arguments:

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
    super(make, model); // Call the parent class constructor with 'make' and 'model'
    this.year = year;
  }

  getFullInfo() {
    return `${this.getInfo()} (${this.year})`;
  }
}

const myCar = new Car("Toyota", "Camry", 2023);
console.log(myCar.getFullInfo()); // Output: Toyota Camry (2023)
```

In this example, the `Car` class extends the `Vehicle` class. The `super(make, model)` call in the `Car` constructor invokes the parent class's constructor, passing the `make` and `model` parameters to initialize the properties inherited from the `Vehicle` class.

By calling `super()` in the child class constructor, you ensure that the parent class's constructor is executed before any child class-specific initialization, allowing you to set up the inherited properties and perform common setup tasks.

# JavaScript - Intermediate Function Inheritance.

Intermediate function inheritance in JavaScript involves creating a new function constructor that inherits properties and methods from an existing function constructor. This can be achieved through prototypes and the `Object.create()` method.

```javascript
// Parent Constructor Function
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Adding a method to the Parent Constructor's prototype
Person.prototype.sayHello = function () {
  console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
};

// Child Constructor Function
function Student(name, age, grade) {
  // Call the parent constructor with 'this' context
  Person.call(this, name, age);
  this.grade = grade;
}

// Inherit from the Parent Constructor's prototype using Object.create
Student.prototype = Object.create(Person.prototype);

// Set the constructor of the Child Constructor back to itself
Student.prototype.constructor = Student;

// Adding a method to the Child Constructor's prototype
Student.prototype.study = function (subject) {
  console.log(
    `${this.name} is a student in grade ${this.grade}, studying ${subject}.`
  );
};

// Instantiate objects
const person1 = new Person("Alice", 30);
const student1 = new Student("Bob", 15, 9);

person1.sayHello(); // Output: Hello, my name is Alice and I am 30 years old.
student1.sayHello(); // Output: Hello, my name is Bob and I am 15 years old.
student1.study("Math"); // Output: Bob is a student in grade 9, studying Math.
```

# JavaScript - Method Overriding.

Method overriding in JavaScript involves creating a new method in a subclass that has the same name as a method in its superclass. When you call the method on an instance of the subclass, the overridden method in the subclass is executed instead of the one in the superclass. This is a key concept in object-oriented programming and is often used to implement polymorphism.

```javascript
// Parent class
class Animal {
  speak() {
    console.log("Animal makes a sound");
  }
}

// Subclass
class Dog extends Animal {
  speak() {
    console.log("Dog barks");
  }
}

// Subclass
class Cat extends Animal {
  speak() {
    console.log("Cat meows");
  }
}

// Creating instances
const genericAnimal = new Animal();
const dog = new Dog();
const cat = new Cat();

// Method overriding in action
genericAnimal.speak(); // Output: Animal makes a sound
dog.speak(); // Output: Dog barks
cat.speak(); // Output: Cat meows
```

In the example above:

1. We define a `Animal` class with a `speak` method that logs a generic message.
2. We create two subclasses, `Dog` and `Cat`, both of which extend the `Animal` class.
3. In each subclass, we override the `speak` method with a specific implementation.
4. We create instances of the `Animal`, `Dog`, and `Cat` classes.
5. When we call the `speak` method on each instance, the overridden method in the respective subclass is executed.

Method overriding allows you to create specialized behavior for subclasses while still benefiting from the inheritance of properties and methods from the superclass. It's an essential concept in object-oriented programming for achieving polymorphism and code reusability.
