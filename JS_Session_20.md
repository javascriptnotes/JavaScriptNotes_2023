# Contents to be covered in this session.

## 1. JavaScript Polyfill.

## 2. JavaScript Throttling.

## 3. JavaScript Debouncing.


# JavaScript Polyfill.

A JavaScript polyfill is a piece of code that provides modern JavaScript features or APIs to older browsers that don't support them. This allows developers to write code using the latest features while ensuring compatibility with a wider range of browsers.

1. **Array.prototype.forEach() Polyfill:**

   The `forEach` method is used to iterate over an array. Some older browsers may not support it, so you can use a polyfill to provide this functionality:

   ```javascript
   if (!Array.prototype.forEach) {
     Array.prototype.forEach = function(callback, thisArg) {
       for (var i = 0; i < this.length; i++) {
         callback.call(thisArg, this[i], i, this);
       }
     };
   }
   ```

2. **Promises Polyfill:**

   Promises are a powerful way to handle asynchronous operations in JavaScript. Some older browsers may not support Promises, so you can use a polyfill to add Promise support:

   ```javascript
   if (!window.Promise) {
     window.Promise = require('es6-promise').Promise;
   }
   ```

   You'll need to include the `es6-promise` library for this polyfill to work.

3. **Object.assign() Polyfill:**

   `Object.assign` is used to copy the values of all enumerable properties of one or more source objects to a target object. For older browsers, you can use a polyfill like this:

   ```javascript
   if (typeof Object.assign !== 'function') {
     Object.assign = function(target) {
       for (var i = 1; i < arguments.length; i++) {
         var source = arguments[i];
         for (var key in source) {
           if (Object.prototype.hasOwnProperty.call(source, key)) {
             target[key] = source[key];
           }
         }
       }
       return target;
     };
   }
   ```

4. **Fetch API Polyfill:**

   The Fetch API is used for making network requests. Older browsers might not support it, so you can use the `whatwg-fetch` polyfill:

   ```javascript
   if (!window.fetch) {
     require('whatwg-fetch');
   }
   ```

   Be sure to include the `whatwg-fetch` library for this polyfill to work.

5. **String.includes() Polyfill:**

   `String.prototype.includes` is used to check if one string contains another. Here's a simple polyfill for it:

   ```javascript
   if (!String.prototype.includes) {
     String.prototype.includes = function(search, start) {
       return this.indexOf(search, start) !== -1;
     };
   }
   ```


# JavaScript Throttling.

Throttling is a technique used in JavaScript to limit the rate at which a particular function can be executed, typically to prevent performance issues or reduce the number of API requests. Throttling ensures that a function is called at a controlled and steady pace, such as no more than once every X milliseconds.

### Throttling with a Timer

```javascript
function throttle(func, delay) {
  let lastCallTime = 0;
  return function (...args) {
    const now = Date.now();
    if (now - lastCallTime >= delay) {
      func.apply(this, args);
      lastCallTime = now;
    }
  };
}

// Example usage
const throttledFunction = throttle(function () {
  console.log("Throttled function called.");
}, 1000);

// This will call the throttled function at most once every 1000ms (1 second)
setInterval(throttledFunction, 100);
```

In this example, the `throttle` function returns a new function that wraps the original function (`func`). It ensures that the original function is called at most once every `delay` milliseconds.

### Throttling with Request Animation Frame

```javascript
function throttleAnimationFrame(func) {
  let animationFrameId;
  return function (...args) {
    if (!animationFrameId) {
      animationFrameId = requestAnimationFrame(() => {
        func.apply(this, args);
        animationFrameId = null;
      });
    }
  };
}

// Example usage
const throttledFunction = throttleAnimationFrame(function () {
  console.log("Throttled function called.");
});

// This will call the throttled function at most once per animation frame
window.addEventListener("scroll", throttledFunction);
```

In this example, the `throttleAnimationFrame` function uses the `requestAnimationFrame` method to throttle the function to the browser's frame rate.

### Lodash Throttle

You can also use the popular library Lodash, which provides a `throttle` function:

```javascript
const throttledFunction = _.throttle(function () {
  console.log("Throttled function called.");
}, 1000);

// Example usage
window.addEventListener("scroll", throttledFunction);
```

Lodash simplifies the process of implementing throttling and provides additional options and flexibility.


# JavaScript Debouncing.

Debouncing is a technique in JavaScript to control the rate at which a function is executed, especially when dealing with events like scroll, resize, or input. It ensures that the function is called only after a certain period of inactivity.

1. Debouncing Input Events:

```javascript
// HTML
<input type="text" id="searchInput">

// JavaScript
const searchInput = document.getElementById('searchInput');
const debounce = (func, delay) => {
  let timer;
  return function() {
    clearTimeout(timer);
    timer = setTimeout(() => {
      func.apply(this, arguments);
    }, delay);
  };
};

function search() {
  // Code to perform the search
}

const debouncedSearch = debounce(search, 300);

searchInput.addEventListener('input', debouncedSearch);
```

This example debounces the `search` function, which is called when the user types into the input field. It ensures that the search is triggered only after the user has stopped typing for 300 milliseconds.

2. Debouncing Scroll Events:

```javascript
const debounce = (func, delay) => {
  let timer;
  return function() {
    clearTimeout(timer);
    timer = setTimeout(() => {
      func.apply(this, arguments);
    }, delay);
  };
};

function handleScroll() {
  // Code to handle scroll event
}

const debouncedScroll = debounce(handleScroll, 300);

window.addEventListener('scroll', debouncedScroll);
```

This example debounces the `handleScroll` function when the user scrolls the page, ensuring it is only called after a 300ms pause in scrolling.

3. Debouncing Resize Events:

```javascript
const debounce = (func, delay) => {
  let timer;
  return function() {
    clearTimeout(timer);
    timer = setTimeout(() => {
      func.apply(this, arguments);
    }, delay);
  };
};

function handleResize() {
  // Code to handle window resize event
}

const debouncedResize = debounce(handleResize, 300);

window.addEventListener('resize', debouncedResize);
```

This example debounces the `handleResize` function for window resize events, preventing excessive calls to the function.

4. Debouncing Mousemove Events:

```javascript
const debounce = (func, delay) => {
  let timer;
  return function() {
    clearTimeout(timer);
    timer = setTimeout(() => {
      func.apply(this, arguments);
    }, delay);
  };
};

function handleMousemove() {
  // Code to handle mousemove event
}

const debouncedMousemove = debounce(handleMousemove, 300);

document.addEventListener('mousemove', debouncedMousemove);
```

This example debounces the `handleMousemove` function for mousemove events, ensuring it is executed with a delay of 300ms after the last mouse movement.

5. Debouncing AJAX Requests:

```javascript
const debounce = (func, delay) => {
  let timer;
  return function() {
    const context = this;
    const args = arguments;
    clearTimeout(timer);
    timer = setTimeout(() => {
      func.apply(context, args);
    }, delay);
  };
};

function fetchData(searchTerm) {
  // Code to make an AJAX request and display results
}

const debouncedFetchData = debounce(fetchData, 500);

const searchInput = document.getElementById('searchInput');
searchInput.addEventListener('input', function() {
  debouncedFetchData(this.value);
});
```

