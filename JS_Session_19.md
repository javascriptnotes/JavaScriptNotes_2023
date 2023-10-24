# Contents to be covered in this session.

## 1. JavaScript Fetch.

## 2. JavaScript Async Await try catch.

## 3. JavaScript Axios.

## 4. JavaScript Currying.

## 5. How JS works with example (event loop, call stack, heap)



# JavaScript Fetch.

JavaScript's `fetch` API is a modern way to make HTTP requests in the browser or Node.js. It allows you to send HTTP requests and handle responses in a more user-friendly and promise-based manner.

**Basic GET Request:**

```javascript
fetch('https://jsonplaceholder.typicode.com/posts/1')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

In this example, we send a GET request to `https://jsonplaceholder.typicode.com/posts/1`, and when the response is received, we parse the JSON data and log it to the console.

**POST Request with JSON Data:**

```javascript
const postData = {
  title: 'My Post',
  body: 'This is the body of my post.',
  userId: 1
};

fetch('https://jsonplaceholder.typicode.com/posts', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify(postData)
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Here, we send a POST request to create a new post on the server. We specify the request method, set the `Content-Type` header to indicate that we're sending JSON data, and provide the JSON data in the request body.

**Handling Errors:**

As shown in the examples, you can use the `.catch()` method to handle errors that might occur during the fetch operation, such as network issues or failed requests.

**Handling Response Types:**

You can use different methods to handle various types of responses. `.json()` is used to parse JSON data, but you can also use `.text()` for plain text or `.blob()` for binary data.

```javascript
fetch('https://example.com/some-text-file.txt')
  .then(response => response.text())
  .then(textData => console.log(textData))
  .catch(error => console.error('Error:', error));
```

**Additional Options:**

The `fetch` function accepts an optional second argument, which can include additional options like headers, credentials, mode, and more. Here's an example that includes custom headers and credentials for a cross-origin request:

```javascript
fetch('https://api.example.com/data', {
  headers: {
    'Authorization': 'Bearer myAuthToken',
    'Custom-Header': 'SomeValue'
  },
  credentials: 'include'
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```


# JavaScript Async Await try catch.

Certainly! In JavaScript, the `async/await` syntax is used to work with asynchronous operations in a more synchronous and readable manner. You can use `try/catch` blocks to handle errors that might occur during asynchronous operations. Here are some code examples to illustrate how this works:

1. Basic `async/await` with `try/catch`:

```javascript
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    if (!response.ok) {
      throw new Error('Failed to fetch data');
    }
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('An error occurred:', error);
    return null;
  }
}

fetchData()
  .then(data => {
    if (data) {
      console.log('Data received:', data);
    } else {
      console.log('Data retrieval failed.');
    }
  });
```

In this example, we use `async/await` to fetch data from an API. If an error occurs during the `fetch` operation or while parsing the response as JSON, the `try/catch` block catches the error, and we can handle it appropriately.

2. Handling multiple asynchronous operations with `async/await` and `Promise.all`:

```javascript
async function fetchUserData(userId) {
  try {
    const userResponse = await fetch(`https://api.example.com/users/${userId}`);
    if (!userResponse.ok) {
      throw new Error('Failed to fetch user data');
    }
    const userData = await userResponse.json();
    return userData;
  } catch (error) {
    console.error('An error occurred while fetching user data:', error);
    throw error;
  }
}

async function fetchPostData(postId) {
  try {
    const postResponse = await fetch(`https://api.example.com/posts/${postId}`);
    if (!postResponse.ok) {
      throw new Error('Failed to fetch post data');
    }
    const postData = await postResponse.json();
    return postData;
  } catch (error) {
    console.error('An error occurred while fetching post data:', error);
    throw error;
  }
}

async function fetchUserAndPostData(userId, postId) {
  try {
    const [userData, postData] = await Promise.all([
      fetchUserData(userId),
      fetchPostData(postId)
    ]);
    
    console.log('User data:', userData);
    console.log('Post data:', postData);
  } catch (error) {
    console.error('An error occurred:', error);
  }
}

fetchUserAndPostData(1, 123);
```

In this example, we use `Promise.all` to concurrently fetch user and post data. The `try/catch` blocks in the individual `fetchUserData` and `fetchPostData` functions handle errors, and the `fetchUserAndPostData` function catches any errors that might occur during the combined operation.

By using `async/await` with `try/catch`, you can make your asynchronous code more robust and handle errors gracefully.


# JavaScript Axios.

Axios is a popular JavaScript library for making HTTP requests. It can be used in both browser and Node.js environments. To get started with Axios, you'll need to include it in your project. You can do this by adding it to your HTML file for the browser or installing it via npm for Node.js.

### Browser (HTML/JavaScript):

#### 1. Include Axios in your HTML file:

```html
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
```

#### 2. Making a GET request:

```javascript
// Using Axios to make a GET request
axios.get('https://jsonplaceholder.typicode.com/posts/1')
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

#### 3. Making a POST request:

```javascript
// Using Axios to make a POST request
axios.post('https://jsonplaceholder.typicode.com/posts', {
  title: 'foo',
  body: 'bar',
  userId: 1
})
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

### Node.js:

#### 1. Install Axios:

You need to install Axios in your Node.js project using npm or yarn:

```bash
npm install axios
# or
yarn add axios
```

#### 2. Making a GET request:

```javascript
const axios = require('axios');

// Using Axios to make a GET request
axios.get('https://jsonplaceholder.typicode.com/posts/1')
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

#### 3. Making a POST request:

```javascript
const axios = require('axios');

// Using Axios to make a POST request
axios.post('https://jsonplaceholder.typicode.com/posts', {
  title: 'foo',
  body: 'bar',
  userId: 1
})
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```


# JavaScript Currying.

JavaScript currying is a technique where you transform a function that takes multiple arguments into a series of functions that each take a single argument. This can be useful in various situations, such as creating reusable function factories or simplifying function calls. I'll provide some code examples to help you understand currying in JavaScript.

**Basic Currying Example:**

```javascript
// Regular function that takes two arguments
function add(x, y) {
  return x + y;
}

// Currying the function
function curryAdd(x) {
  return function(y) {
    return x + y;
  };
}

const addFive = curryAdd(5);
console.log(addFive(3)); // Output: 8
```

In this example, `curryAdd` takes an initial argument `x` and returns a new function that expects the second argument `y`. This creates a curried version of the `add` function.

**Currying Using Arrow Functions:**

You can achieve the same result using arrow functions:

```javascript
const curryAdd = (x) => (y) => x + y;
const addFive = curryAdd(5);
console.log(addFive(3)); // Output: 8
```

**Currying with Multiple Arguments:**

Currying is not limited to functions with just two arguments. You can curry functions with any number of arguments:

```javascript
function multiply(x) {
  return function(y) {
    return function(z) {
      return x * y * z;
    };
  };
}

const multiplyByTwo = multiply(2);
const multiplyByTwoAndThree = multiplyByTwo(3);
console.log(multiplyByTwoAndThree(4)); // Output: 24
```

**Using a Currying Utility Function:**

You can also create a utility function for currying any function, making the process more generic:

```javascript
function curry(func) {
  return function curried(...args) {
    if (args.length >= func.length) {
      return func(...args);
    } else {
      return (...moreArgs) => curried(...args, ...moreArgs);
    }
  }
}

function add(x, y, z) {
  return x + y + z;
}

const curriedAdd = curry(add);
const add2 = curriedAdd(2);
const add2And3 = add2(3);
console.log(add2And3(4)); // Output: 9
```


# How JS works with example (event loop, call stack, heap).

JavaScript is a single-threaded, non-blocking, and asynchronous language. It uses an event loop and a call stack to manage the execution of code. Let's break down how JavaScript works with examples:

1. **Call Stack**:
   - The call stack is a data structure that keeps track of the currently executing function or code. It follows the Last-In-First-Out (LIFO) principle.
   - When a function is called, it's pushed onto the stack. When the function returns, it's popped off the stack.
   - Consider this example:

    ```javascript
    function first() {
        console.log("First function");
    }

    function second() {
        first();
        console.log("Second function");
    }

    second();
    ```

   - The call stack would look like this as functions are called and return:

   ```
   [second]
   [second, first]
   [second]
   []
   ```

2. **Event Loop**:
   - JavaScript's event loop is responsible for handling asynchronous operations. It constantly checks the message queue for events to be processed.
   - JavaScript uses callbacks, Promises, and async/await to manage asynchronous code.

   ```javascript
   console.log("Start");
   setTimeout(() => {
       console.log("Timeout");
   }, 1000);
   console.log("End");
   ```

   - In this example, the code doesn't wait for the `setTimeout` to finish. It continues executing and logs "Start" and "End" immediately. After 1 second, "Timeout" will be logged.

3. **Heap**:
   - The heap is where objects and data are stored, including variables and objects created in your code.
   - Variables are stored in the heap, and references to those variables are placed on the call stack.

Here's the sequence of events in the example above:

1. The `second()` function is called and pushed onto the call stack.
2. Inside `second()`, the `first()` function is called and pushed onto the call stack.
3. `first()` logs "First function" and returns, so it's popped from the call stack.
4. Execution returns to `second()`, and it logs "Second function" and also returns, getting popped from the call stack.
5. The call stack is empty.

Now, let's consider the asynchronous example:

1. The script starts executing and logs "Start."
2. It encounters `setTimeout`, which is a non-blocking function. It's pushed to the call stack.
3. `setTimeout` is popped from the call stack, and the event loop registers the callback function to be executed after the specified time (1 second).
4. The script continues, logging "End."
5. After 1 second, the event loop places the callback function (console.log("Timeout")) back on the call stack, and "Timeout" is logged.



