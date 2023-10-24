# Contents to be covered in this session.

## 1. JavaScript Asynchronous Programming.

## 2. JavaScript - JSON.

## 3. Ajax Introduction.

## 4. JavaScript setTimeout Function.

## 5. JavaScript setInterval Function.

## 6. JavaScript Promises.

## 7. JavaScript Promises.all.



# JavaScript Asynchronous Programming.

JavaScript is a single-threaded language, meaning it executes one task at a time. However, it supports asynchronous programming to handle tasks like network requests, file operations, and timers without blocking the main thread. Asynchronous programming is essential to create responsive and efficient web applications. 

1. Callbacks:

Callbacks are a traditional way to handle asynchronous code. A callback is a function that is passed as an argument and executed when the asynchronous operation is complete.

```javascript
function fetchData(callback) {
  setTimeout(() => {
    console.log("Data fetched");
    callback();
  }, 1000);
}

function processData() {
  console.log("Data processed");
}

fetchData(processData);
```

2. Promises:

Promises simplify asynchronous code by providing a more structured way to handle callbacks and errors. They have three states: pending, resolved, and rejected.

```javascript
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log("Data fetched");
      resolve();
    }, 1000);
  });
}

function processData() {
  console.log("Data processed");
}

fetchData()
  .then(processData)
  .catch((error) => console.error(error));
```

3. Async/Await:

Async/await is a more readable way to work with promises. It allows you to write asynchronous code in a synchronous-like style.

```javascript
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log("Data fetched");
      resolve();
    }, 1000);
  });
}

async function processData() {
  await fetchData();
  console.log("Data processed");
}

processData();
```

4. Event Listeners:

Asynchronous operations can also be handled using event listeners, such as for user interactions or HTTP requests.

```javascript
const button = document.getElementById("myButton");

function handleClick() {
  console.log("Button clicked");
}

button.addEventListener("click", handleClick);
```

5. Fetch API:

The Fetch API is used for making network requests. It returns a promise, making it suitable for asynchronous operations.

```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.error(error);
  });
```

6. Timers:

JavaScript provides timers for scheduling asynchronous code execution.

```javascript
console.log("Start");
setTimeout(() => {
  console.log("Timeout completed");
}, 1000);

console.log("End");
```


# JavaScript - JSON.
 
 JavaScript and JSON (JavaScript Object Notation) often go hand in hand, as JSON is a lightweight data interchange format that's easy to work with in JavaScript. Here are some code examples to illustrate how you can use JSON in JavaScript:

1. **Creating a JSON Object:**

   You can create a JSON object in JavaScript using JavaScript's object literal notation:

   ```javascript
   let person = {
       "name": "John Doe",
       "age": 30,
       "isStudent": false
   };
   ```

2. **Converting JSON to a JavaScript Object:**

   You can parse a JSON string into a JavaScript object using `JSON.parse()`:

   ```javascript
   let jsonString = '{"name":"Jane Smith","age":25,"isStudent":true}';
   let person = JSON.parse(jsonString);

   console.log(person.name); // Output: Jane Smith
   ```

3. **Converting a JavaScript Object to JSON:**

   You can convert a JavaScript object to a JSON string using `JSON.stringify()`:

   ```javascript
   let person = {
       name: "Alice",
       age: 35,
       isStudent: true
   };

   let jsonString = JSON.stringify(person);

   console.log(jsonString);
   // Output: {"name":"Alice","age":35,"isStudent":true}
   ```

4. **Working with Nested JSON Objects:**

   JSON can contain nested objects and arrays. Here's an example:

   ```javascript
   let product = {
       "name": "Smartphone",
       "price": 499.99,
       "specs": {
           "brand": "Samsung",
           "screenSize": 6.2,
           "colors": ["Black", "Blue", "White"]
       }
   };

   console.log(product.specs.brand); // Output: Samsung
   console.log(product.specs.colors[0]); // Output: Black
   ```

5. **Looping Through JSON Data:**

   You can loop through JSON data using `for...in` or `Object.keys()`:

   ```javascript
   let person = {
       "name": "David",
       "age": 28,
       "isStudent": false
   };

   for (let key in person) {
       console.log(key + ": " + person[key]);
   }
   ```

6. **Handling JSON Errors:**

   When parsing JSON, you should handle errors. For example:

   ```javascript
   let invalidJSON = '{"name": "Alice", "age": }';

   try {
       let person = JSON.parse(invalidJSON);
   } catch (error) {
       console.error("Error parsing JSON: " + error.message);
   }
   ```

7. **Fetching JSON Data (AJAX Example):**

   You can use JavaScript to fetch JSON data from a server using AJAX. Here's a basic example using the `fetch` API:

   ```javascript
   fetch('https://example.com/api/data.json')
       .then(response => response.json())
       .then(data => {
           console.log(data);
       })
       .catch(error => {
           console.error("Error fetching data: " + error);
       });
   ```

8. **JSON as Configuration:**

   JSON is often used to store configuration data. For example, a configuration file could be read and applied in your JavaScript application.


# Ajax Introduction.

Ajax, which stands for "Asynchronous JavaScript and XML," is a set of web development techniques that allow web applications to send and receive data from a web server asynchronously, without the need to reload the entire web page. Ajax enables web pages to be more dynamic and responsive, creating a smoother and more interactive user experience.

Here's an introduction to some key aspects of Ajax:

1. **Asynchronous:** The "A" in Ajax stands for asynchronous. This means that when an Ajax request is made, the web page doesn't wait for the response to come back from the server before continuing to function. This asynchronous behavior allows other parts of the web page to remain interactive while data is being fetched or sent to the server.

2. **JavaScript:** JavaScript is the primary language used in Ajax development. It's used to create the request to the server, handle the response, and manipulate the DOM (Document Object Model) to update the web page without requiring a full reload.

3. **XML or JSON:** Initially, the "X" in Ajax referred to XML, which is a markup language used for structuring data. However, JSON (JavaScript Object Notation) is now more commonly used due to its simplicity and efficiency. JSON is a lightweight data interchange format that's easy to work with in JavaScript.

4. **HTTP Requests:** Ajax relies on the HTTP protocol to send requests to a web server. These requests can be of different types, such as GET (for retrieving data) or POST (for sending data to the server). The server processes the request and sends a response back, typically in JSON or XML format.

5. **DOM Manipulation:** One of the primary purposes of using Ajax is to update parts of a web page without a full refresh. JavaScript is used to manipulate the DOM to insert, remove, or modify elements on the page based on the data received from the server.

6. **Frameworks and Libraries:** While it's possible to implement Ajax from scratch using JavaScript and the XMLHttpRequest object, many web developers use libraries and frameworks to simplify the process. Popular options include jQuery, Axios, and the Fetch API.

7. **Cross-Origin Requests:** Due to security restrictions, Ajax requests are typically limited to the same domain from which the web page was loaded. To make requests to different domains, techniques like JSONP (JSON with Padding) or Cross-Origin Resource Sharing (CORS) can be used.

8. **Error Handling:** Handling errors gracefully is crucial in Ajax development. There should be mechanisms in place to handle server errors, network issues, or other unexpected problems.

Ajax has become a fundamental part of modern web development, enabling the creation of web applications that feel more like desktop applications in terms of speed and responsiveness. It's widely used in features like form validation, auto-suggestions, real-time updates, and more, contributing to a more dynamic and user-friendly web.


# JavaScript setTimeout Function.

The `setTimeout` function in JavaScript is used to schedule the execution of a function (or the evaluation of an expression) after a specified delay in milliseconds. It is often used for tasks like triggering animations, delaying the execution of code, or making AJAX requests after a certain time interval.

Here's the basic syntax of `setTimeout`:

```javascript
setTimeout(function, delay);
```

- `function`: The function to be executed after the specified delay.
- `delay`: The time (in milliseconds) to wait before executing the function.

Here are some code examples to illustrate how to use `setTimeout`:

**Example 1: Basic Usage**

```javascript
function sayHello() {
  console.log("Hello, World!");
}

// Execute the sayHello function after a delay of 2000 milliseconds (2 seconds).
setTimeout(sayHello, 2000);
```

**Example 2: Using an Anonymous Function**

You can also use an anonymous function as the first argument.

```javascript
// Execute an anonymous function after a delay of 1500 milliseconds.
setTimeout(function() {
  console.log("This is an anonymous function!");
}, 1500);
```

**Example 3: Passing Arguments to the Function**

You can pass arguments to the function you want to execute after the delay.

```javascript
function greet(name) {
  console.log("Hello, " + name + "!");
}

// Pass the 'name' argument to the greet function after a delay of 1000 milliseconds.
setTimeout(greet, 1000, "Alice");
```

**Example 4: Clearing a Timeout**

You can use the `clearTimeout` function to cancel a scheduled timeout before it executes.

```javascript
function showMessage() {
  console.log("This message won't be displayed.");
}

// Schedule the showMessage function, but then cancel it immediately.
const timeoutId = setTimeout(showMessage, 2000);
clearTimeout(timeoutId);
```

**Example 5: Repeated Execution (Interval)**

To execute a function repeatedly at a specified interval, you can use `setInterval`. Here's a simple example:

```javascript
function printCount() {
  console.log("Count: " + count);
  count++;
}

let count = 1;

// Execute the printCount function every 1000 milliseconds (1 second).
const intervalId = setInterval(printCount, 1000);

// To stop the interval after a certain number of repetitions, you can use clearInterval:
setTimeout(function() {
  clearInterval(intervalId);
  console.log("Interval stopped.");
}, 5000); // Stop after 5 seconds
```


# JavaScript setInterval Function.

The `setInterval` function in JavaScript is used to repeatedly execute a given function at a specified time interval. It takes two arguments: the function to be executed and the time interval (in milliseconds) at which the function should be called. The function will continue to run until you explicitly clear it using the `clearInterval` function.

Here's the basic syntax:

```javascript
var intervalID = setInterval(callback, delay);
```

- `callback`: The function to be executed at each interval.
- `delay`: The time (in milliseconds) between each execution of the callback function.

Here are some code examples demonstrating how to use `setInterval`:

### Example 1: Basic usage

This example demonstrates a simple countdown that updates every second:

```javascript
var countdown = 10;

function updateCountdown() {
  console.log(countdown);
  countdown--;

  if (countdown < 0) {
    clearInterval(intervalID);
    console.log("Countdown is over!");
  }
}

var intervalID = setInterval(updateCountdown, 1000); // Call updateCountdown every 1000ms (1 second)
```

### Example 2: Continuous clock

In this example, we create a continuously updating clock that displays the current time every second:

```javascript
function updateClock() {
  var now = new Date();
  var time = now.toLocaleTimeString();
  console.log("Current time: " + time);
}

var intervalID = setInterval(updateClock, 1000); // Update the clock every second
```

### Example 3: Clearing the interval

To stop an interval, you can use the `clearInterval` function. Here's how you can stop the clock from the previous example:

```javascript
// Assuming you have an intervalID from the previous example
clearInterval(intervalID);
```

The `clearInterval` function takes the interval ID returned by `setInterval` as an argument, allowing you to stop the execution of the specified interval.


# JavaScript Promises.

JavaScript Promises are a way to handle asynchronous operations in a more organized and readable manner. They provide a way to work with asynchronous code in a more structured and predictable way. Promises have three states: pending, fulfilled, and rejected. When the state changes, you can attach callbacks to handle the results.

### Creating a Promise

You can create a Promise using the `Promise` constructor, which takes a function as its argument. This function receives two parameters: `resolve` and `reject`. You call `resolve` when the asynchronous operation succeeds and `reject` when it fails.

```javascript
const myPromise = new Promise((resolve, reject) => {
  // Simulate an asynchronous operation
  setTimeout(() => {
    const success = true;
    if (success) {
      resolve('Operation completed successfully');
    } else {
      reject('Operation failed');
    }
  }, 1000);
});
```

### Consuming a Promise

To consume the result of a Promise, you can use the `.then()` method to attach a callback that runs when the Promise is fulfilled (resolved) or the `.catch()` method to handle any errors (rejected). Additionally, you can use `.finally()` to perform actions regardless of the Promise's outcome.

```javascript
myPromise
  .then((result) => {
    console.log('Success:', result);
  })
  .catch((error) => {
    console.error('Error:', error);
  })
  .finally(() => {
    console.log('Promise is settled');
  });
```

### Chaining Promises

Promises can be chained, allowing you to perform a sequence of asynchronous operations. Each `.then()` returns a new Promise, which allows for further chaining.

```javascript
const asyncOperation = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve('Step 1 completed');
    }, 1000);
  });
};

asyncOperation()
  .then((result) => {
    console.log(result);
    return 'Step 2 completed';
  })
  .then((result) => {
    console.log(result);
  })
  .catch((error) => {
    console.error('Error:', error);
  });
```

### Handling Multiple Promises

You can use `Promise.all()` to handle multiple Promises. It waits for all Promises to resolve successfully or reject with an error.

```javascript
const promise1 = fetch('https://api.example.com/data1.json');
const promise2 = fetch('https://api.example.com/data2.json');

Promise.all([promise1, promise2])
  .then((responses) => {
    const [response1, response2] = responses;
    return Promise.all([response1.json(), response2.json()]);
  })
  .then((data) => {
    const [data1, data2] = data;
    console.log('Data 1:', data1);
    console.log('Data 2:', data2);
  })
  .catch((error) => {
    console.error('Error:', error);
  });
```

### Promise.race()

`Promise.race()` resolves or rejects as soon as one of the Promises in an array resolves or rejects, whichever comes first. This can be useful for scenarios where you want to use the result of the first Promise to complete.

```javascript
const promise1 = new Promise((resolve) => setTimeout(() => resolve('First'), 1000));
const promise2 = new Promise((resolve) => setTimeout(() => resolve('Second'), 500));

Promise.race([promise1, promise2])
  .then((result) => {
    console.log('First Promise to resolve:', result);
  })
  .catch((error) => {
    console.error('Error:', error);
  });
```


# JavaScript Promises.all.

JavaScript `Promise.all` is a method that allows you to execute multiple promises in parallel and wait for all of them to complete before moving on. It takes an array of promises as input and returns a new promise that resolves when all the promises in the input array have resolved or rejects when any of the promises in the input array have rejected.

1. **Basic Usage**:

   ```javascript
   const promise1 = new Promise((resolve, reject) => {
     setTimeout(() => resolve('Promise 1'), 1000);
   });

   const promise2 = new Promise((resolve, reject) => {
     setTimeout(() => resolve('Promise 2'), 2000);
   });

   const promise3 = new Promise((resolve, reject) => {
     setTimeout(() => resolve('Promise 3'), 1500);
   });

   Promise.all([promise1, promise2, promise3])
     .then((results) => {
       console.log('All promises have resolved:', results);
     })
     .catch((error) => {
       console.error('At least one promise was rejected:', error);
     });
   ```

   In this example, we have three promises that resolve after different time intervals. `Promise.all` waits for all of them to complete and then returns an array of resolved values. If any of the promises is rejected, the `.catch` block will be executed.

2. **Handling Errors**:

   You can use `.catch` to handle errors for any of the promises in the array:

   ```javascript
   const promise1 = new Promise((resolve, reject) => {
     setTimeout(() => resolve('Promise 1'), 1000);
   });

   const promise2 = new Promise((resolve, reject) => {
     setTimeout(() => reject('Promise 2 failed'), 2000);
   });

   const promise3 = new Promise((resolve, reject) => {
     setTimeout(() => resolve('Promise 3'), 1500);
   });

   Promise.all([promise1, promise2, promise3])
     .then((results) => {
       console.log('All promises have resolved:', results);
     })
     .catch((error) => {
       console.error('At least one promise was rejected:', error);
     });
   ```

   In this case, the output will be:

   ```
   At least one promise was rejected: Promise 2 failed
   ```

3. **Iterating Over Results**:

   You can use `Promise.all` to wait for multiple asynchronous operations and process the results individually:

   ```javascript
   const fetchUserData = () => {
     return fetch('https://api.example.com/user')
       .then((response) => response.json());
   };

   const fetchProductData = () => {
     return fetch('https://api.example.com/products')
       .then((response) => response.json());
   };

   Promise.all([fetchUserData(), fetchProductData()])
     .then((results) => {
       const userData = results[0];
       const productData = results[1];
       console.log('User data:', userData);
       console.log('Product data:', productData);
     })
     .catch((error) => {
       console.error('At least one promise was rejected:', error);
     });
   ```

   In this example, we're making two API requests and processing the results when both are resolved.

4. **Promise.all with Dynamic Array**:

   You can use `Promise.all` with an array of promises generated dynamically:

   ```javascript
   const promiseArray = [];
   for (let i = 1; i <= 5; i++) {
     promiseArray.push(new Promise((resolve) => setTimeout(() => resolve(`Promise ${i}`), i * 1000)));
   }

   Promise.all(promiseArray)
     .then((results) => {
       console.log('All promises have resolved:', results);
     })
     .catch((error) => {
       console.error('At least one promise was rejected:', error);
     });
   ```

   This code creates an array of promises with dynamic values and waits for all of them to resolve.

5. **Promise.all with Promises and Non-Promises**:

   `Promise.all` can handle an array that includes both promises and non-promises. Non-promises are treated as immediately resolved promises:

   ```javascript
   const promise1 = new Promise((resolve) => setTimeout(() => resolve('Promise 1'), 1000));
   const nonPromise = 'Not a Promise';
   const promise2 = new Promise((resolve) => setTimeout(() => resolve('Promise 2'), 1500));

   Promise.all([promise1, nonPromise, promise2])
     .then((results) => {
       console.log('All promises have resolved (including non-promises):', results);
     })
     .catch((error) => {
       console.error('At least one promise was rejected:', error);
     });
   ```

   
