# Contents to be covered in this session.

## 1. JavaScript Objects - Adding and Removing Properties.

## 2. JavaScript Objects - Enumerating Properties.

## 3. JavaScript Abstraction.

## 4. JavaScript Private Properties & Methods.


# JavaScript Objects - Adding and Removing Properties.

In JavaScript, objects are one of the fundamental data structures used to store and manage data. You can add and remove properties from objects easily.

### Adding Properties to an Object:

You can add properties to an object by simply assigning a value to a new property or overwriting an existing property. Here's an example:

```javascript
// Creating an empty object
const person = {};

// Adding properties to the object
person.firstName = 'John';
person.lastName = 'Doe';
person.age = 30;

// You can also use square brackets to add properties with dynamic keys
const key = 'email';
person[key] = 'john.doe@example.com';

console.log(person);
```

Output:

```javascript
{
  firstName: 'John',
  lastName: 'Doe',
  age: 30,
  email: 'john.doe@example.com'
}
```

### Removing Properties from an Object:

You can remove properties from an object using the `delete` operator. Here's an example:

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 30,
  email: 'john.doe@example.com'
};

// Removing the 'age' property
delete person.age;

console.log(person);
```

Output:

```javascript
{
  firstName: 'John',
  lastName: 'Doe',
  email: 'john.doe@example.com'
}
```

Keep in mind that while you can remove properties from an object, it's generally not recommended to do so unless you have a specific use case, as it can make your code less predictable and harder to maintain.

In addition to these basic methods of adding and removing properties, you can also use methods like `Object.assign()` to add properties from one object to another and create a new object. Here's an example:

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe'
};

const details = {
  age: 30,
  email: 'john.doe@example.com'
};

// Merge properties from 'details' into 'person'
const mergedPerson = Object.assign({}, person, details);

console.log(mergedPerson);
```

Output:

```javascript
{
  firstName: 'John',
  lastName: 'Doe',
  age: 30,
  email: 'john.doe@example.com'
}
```

In this example, we created a new object `mergedPerson` by merging properties from both `person` and `details` objects using `Object.assign()`.


# JavaScript Objects - Enumerating Properties.

In JavaScript, you can enumerate (loop through) the properties of an object using a variety of methods.

1. **For...In Loop:**
   The `for...in` loop allows you to iterate over the enumerable properties of an object.

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 30,
};

for (let key in person) {
  console.log(key, person[key]);
}
```

2. **Object.keys():**
   The `Object.keys()` method returns an array of an object's own enumerable property names.

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 30,
};

const keys = Object.keys(person);
keys.forEach(key => {
  console.log(key, person[key]);
});
```

3. **Object.values():**
   The `Object.values()` method returns an array of an object's own enumerable property values.

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 30,
};

const values = Object.values(person);
values.forEach(value => {
  console.log(value);
});
```

4. **Object.entries():**
   The `Object.entries()` method returns an array of an object's own enumerable property key-value pairs.

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 30,
};

const entries = Object.entries(person);
entries.forEach(([key, value]) => {
  console.log(key, value);
});
```

5. **Object.getOwnPropertyNames():**
   The `Object.getOwnPropertyNames()` method returns an array of all own property names, including non-enumerable properties.

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 30,
};

const propertyNames = Object.getOwnPropertyNames(person);
propertyNames.forEach(propertyName => {
  console.log(propertyName, person[propertyName]);
});
```

6. **Reflect.ownKeys():**
   The `Reflect.ownKeys()` method returns an array of all property names, including both enumerable and non-enumerable properties.

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 30,
};

const keys = Reflect.ownKeys(person);
keys.forEach(key => {
  console.log(key, person[key]);
});
```

It's important to note that `for...in` and `Object.keys()` loop over enumerable properties and do not include non-enumerable properties or properties inherited from prototypes. If you want to include non-enumerable properties or properties from the object's prototype chain, you can use `Object.getOwnPropertyNames()` or `Reflect.ownKeys()`.

Be cautious when using `for...in` with objects, as it may iterate over properties from the object's prototype chain as well. You can use methods like `hasOwnProperty` to filter out inherited properties.


# JavaScript Abstraction.

JavaScript allows you to create abstractions through various techniques. Abstraction in programming involves hiding complex implementation details and exposing a simplified interface to users.

1. **Functions:** Functions are a fundamental way to abstract functionality.

```javascript
function add(a, b) {
  return a + b;
}

const result = add(3, 4); // Abstraction of addition
console.log(result); // Output: 7
```

2. **Objects and Classes:** You can use objects and classes to create more complex abstractions. Here's an example of a class that abstracts a `Person`:

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

const john = new Person("John", 30);
john.sayHello(); // Abstraction of a person
```

3. **Closures:** Closures allow you to encapsulate data and functions within a private scope.

```javascript
function counter() {
  let count = 0;
  
  return {
    increment: () => {
      count++;
    },
    getCount: () => {
      return count;
    }
  };
}

const counterInstance = counter(); // Abstraction of a counter
counterInstance.increment();
console.log(counterInstance.getCount()); // Output: 1
```

4. **Modules:** In modern JavaScript, you can use modules to encapsulate functionality.

```javascript
// math.js
export function add(a, b) {
  return a + b;
}

// main.js
import { add } from './math.js';

const result = add(3, 4); // Abstraction of addition from a module
console.log(result); // Output: 7
```

5. **Promises:** Promises abstract asynchronous operations.

```javascript
function fetchData() {
  return new Promise((resolve, reject) => {
    // Simulate an asynchronous operation
    setTimeout(() => {
      resolve("Data fetched successfully");
    }, 2000);
  });
}

fetchData()
  .then((data) => {
    console.log(data); // Abstraction of asynchronous data fetching
  })
  .catch((error) => {
    console.error(error);
  });
```

6. **Callbacks:** Callbacks can abstract asynchronous operations in an older style.

```javascript
function fetchData(callback) {
  setTimeout(() => {
    callback("Data fetched successfully");
  }, 2000);
}

fetchData((data) => {
  console.log(data); // Abstraction of asynchronous data fetching with a callback
});
```

# JavaScript Private Properties & Methods.

In JavaScript, there isn't a true concept of "private" properties or methods like you might find in some other programming languages. However, you can achieve a level of encapsulation and privacy using closures and naming conventions.

1. Using Closures:

One common way to create private properties and methods is by using closures. You encapsulate the data and methods within a function scope, and only expose what is necessary. Here's an example:

```javascript
function createPerson(name, age) {
  let _name = name; // Private property
  let _age = age;   // Private property

  // Private method
  function isAdult() {
    return _age >= 18;
  }

  // Public methods (exposed)
  return {
    getName: function() {
      return _name;
    },
    getAge: function() {
      return _age;
    },
    isAdult: isAdult
  };
}

const person = createPerson("John", 25);
console.log(person.getName());     // "John"
console.log(person.getAge());      // 25
console.log(person.isAdult());     // true
console.log(person._name);         // undefined (private)
console.log(person.isAdult());     // true
```

In this example, `_name` and `_age` are private properties, and `isAdult` is a private method. Only the functions returned from `createPerson` have access to these private members.

2. Using ES6 Classes (Weak Private Fields):

In modern JavaScript, you can use Weak Private Fields to create private properties. These fields are not truly private but are marked as private by naming convention with a `#` prefix.

```javascript
class Person {
  #name; // Private property
  #age;  // Private property

  constructor(name, age) {
    this.#name = name;
    this.#age = age;
  }

  // Public methods
  getName() {
    return this.#name;
  }

  getAge() {
    return this.#age;
  }
}

const person = new Person("Alice", 30);
console.log(person.getName());     // "Alice"
console.log(person.#name);         // SyntaxError: Private field '#name' must be declared in an enclosing class
```

With the `#` prefix, the properties are considered private, and attempts to access them outside the class will result in an error.

