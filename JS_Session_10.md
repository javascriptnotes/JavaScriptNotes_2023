# Contents to be covered in this session.

## 1. JavaScript Recursion.

## 2. JavaScript Regex (Client side Validation).

## 3. JavaScript DOM Events.

## 4. JavaScript Event Bubbling, Capturing and Propagation.

## 5. JavaScript Value vs Reference types.


# JavaScript Recursion.

Recursion in JavaScript is a technique where a function calls itself to solve a problem. It's a powerful and elegant way to solve problems that can be broken down into smaller, similar subproblems. Here are some code examples demonstrating recursion in JavaScript:

1. Factorial Calculation:
   Calculating the factorial of a non-negative integer using recursion.

```javascript
function factorial(n) {
  // Base case: if n is 0 or 1, the factorial is 1
  if (n <= 1) {
    return 1;
  } else {
    // Recursive case: n! = n * (n-1)!
    return n * factorial(n - 1);
  }
}

console.log(factorial(5)); // Output: 120 (5 * 4 * 3 * 2 * 1)
```

2. Fibonacci Sequence:
   Generating the nth Fibonacci number using recursion.

```javascript
function fibonacci(n) {
  // Base cases: Fibonacci(0) = 0 and Fibonacci(1) = 1
  if (n <= 1) {
    return n;
  } else {
    // Recursive case: Fibonacci(n) = Fibonacci(n-1) + Fibonacci(n-2)
    return fibonacci(n - 1) + fibonacci(n - 2);
  }
}

console.log(fibonacci(7)); // Output: 13 (0, 1, 1, 2, 3, 5, 8, 13)
```

3. Recursive Countdown:
   A simple countdown using recursion.

```javascript
function countdown(n) {
  if (n <= 0) {
    console.log("Done!");
  } else {
    console.log(n);
    countdown(n - 1);
  }
}

countdown(5);
// Output:
// 5
// 4
// 3
// 2
// 1
// Done!
```


# JavaScript Regex (Client side Validation).

Learn and Practice from external resource:- https://regexr.com/


# JavaScript DOM Events - Handlers and Listeners.

JavaScript event handlers and event listeners are used to handle and respond to events (e.g., user interactions like clicks, mouse movements, keyboard input) in web applications. They allow you to define functions that are executed when a specific event occurs. Below are examples of both event handlers and event listeners in JavaScript:

### Event Handlers:

1. **Inline Event Handler:**
   Inline event handlers are defined directly in HTML elements.

   ```html
   <button onclick="myFunction()">Click Me</button>

   <script>
     function myFunction() {
       alert('Button clicked!');
     }
   </script>
   ```

2. **DOM Element Property Event Handler:**
   You can also assign event handlers using JavaScript by accessing the element's property.

   ```html
   <button id="myButton">Click Me</button>

   <script>
     document.getElementById('myButton').onclick = function() {
       alert('Button clicked!');
     };
   </script>
   ```

### Event Listeners:

Event listeners are a more flexible way to handle events, as they allow you to attach multiple event handlers to a single element and dynamically add or remove them.

1. **Using `addEventListener`:**

   ```html
   <button id="myButton">Click Me</button>

   <script>
     function handleClick() {
       alert('Button clicked!');
     }

     const button = document.getElementById('myButton');
     button.addEventListener('click', handleClick);
   </script>
   ```

2. **Removing Event Listeners:**

   You can also remove event listeners using the `removeEventListener` method.

   ```html
   <button id="myButton">Click Me</button>

   <script>
     function handleClick() {
       alert('Button clicked!');
     }

     const button = document.getElementById('myButton');
     button.addEventListener('click', handleClick);

     // Remove the event listener after the button is clicked once.
     button.removeEventListener('click', handleClick);
   </script>
   ```

3. **Using Event Object:**

   Event listeners often receive an event object that contains information about the event, such as the target element and event type.

   ```html
   <button id="myButton">Click Me</button>

   <script>
     function handleClick(event) {
       alert(`Button clicked! Target: ${event.target.id}`);
     }

     const button = document.getElementById('myButton');
     button.addEventListener('click', handleClick);
   </script>
   ```

4. **Event Delegation:**

   Event delegation is a technique where you attach a single event listener to a parent element to handle events for its child elements. It's useful when you have many similar elements.

   ```html
   <ul id="myList">
     <li>Item 1</li>
     <li>Item 2</li>
     <li>Item 3</li>
   </ul>

   <script>
     function handleItemClick(event) {
       if (event.target.tagName === 'LI') {
         alert(`Clicked on ${event.target.textContent}`);
       }
     }

     const list = document.getElementById('myList');
     list.addEventListener('click', handleItemClick);
   </script>
   ```

## JavaScript DOM Events.

In JavaScript, the Document Object Model (DOM) allows you to interact with HTML elements and web pages dynamically. Events are a fundamental part of web development, as they allow you to respond to user interactions and trigger specific actions. Here is a list of some common DOM events with brief examples:

1. **click**: Triggered when a mouse click occurs on an element.

   ```javascript
   const button = document.querySelector('#myButton');
   button.addEventListener('click', () => {
     alert('Button clicked!');
   });
   ```
## Comprehensive list of DOM events in JavaScript:

1. **click**: Occurs when a mouse click is made on an element.

2. **dblclick**: Fired when a double mouse click (two quick consecutive clicks) is detected on an element.

3. **mousedown**: Triggered when the mouse button is pressed down over an element.

4. **mouseup**: Fired when the mouse button is released after a mousedown event.

5. **mousemove**: Occurs when the mouse pointer moves within an element.

6. **mouseover**: Triggered when the mouse pointer enters an element.

7. **mouseout**: Fired when the mouse pointer leaves an element.

8. **contextmenu**: Occurs when the right mouse button is clicked, typically used for context menus.

9. **keydown**: Fired when a keyboard key is pressed down.

10. **keyup**: Occurs when a keyboard key is released.

11. **keypress**: Fired when a keyboard key is pressed and released, useful for detecting character input.

12. **submit**: Occurs when a form is submitted, either by clicking a submit button or pressing Enter within a form field.

13. **reset**: Fired when a form's reset button is clicked, resetting form fields to their default values.

14. **change**: Triggered when the value of an input element (e.g., text input or select) changes.

15. **focus**: Occurs when an element gains focus, such as when clicking inside an input field.

16. **blur**: Fired when an element loses focus, often used for validation when a user leaves an input field.

17. **input**: Triggered when the content of an input element changes, including typing or pasting.

18. **invalid**: Occurs when an input element's value is invalid, often used for form validation.

19. **load**: Fired when an external resource (e.g., an image or script) finishes loading.

20. **unload**: Occurs when the document is about to be unloaded, typically when navigating away from a page.

21. **resize**: Triggered when the browser window is resized.

22. **scroll**: Fired when the user scrolls the page, either horizontally or vertically.

23. **DOMContentLoaded**: Occurs when the initial HTML document has been completely loaded and parsed.

24. **readystatechange**: Fired when the state of the document changes, indicating whether it's loading, interactive, or complete.

25. **focusin**: Similar to 'focus,' but bubbles up through the DOM tree.

26. **focusout**: Similar to 'blur,' but bubbles up through the DOM tree.

27. **copy**: Occurs when the user copies content (e.g., text) to the clipboard.

28. **cut**: Fired when the user cuts content to the clipboard (e.g., text in a text field).

29. **paste**: Triggered when the user pastes content from the clipboard into an element (e.g., a text input).

30. **dragstart**: Occurs when a draggable element is dragged.

31. **dragend**: Fired when a drag operation is completed (e.g., when releasing a draggable element).

32. **dragenter**: Triggered when a dragged element enters a drop target.

33. **dragleave**: Occurs when a dragged element leaves a drop target.

34. **dragover**: Fired when a dragged element is over a drop target.

35. **drop**: Triggered when a draggable element is dropped onto a drop target.



# JavaScript Event Bubbling, Capturing and Propagation.

JavaScript event bubbling, capturing, and propagation are fundamental concepts in web development that describe how events are handled in the Document Object Model (DOM) when multiple elements are nested within each other and an event occurs. Understanding these concepts is crucial for effective event handling in web applications.

1. Event Bubbling:
   - Event bubbling is the default behavior in which an event starts at the target element that triggered the event and then propagates up the DOM hierarchy to the root of the document (i.e., the `window` object). This means that when an event occurs on a nested element, it triggers event handlers on all of its ancestor elements.

   Example:
   ```html
   <div id="parent">
       <button id="child">Click Me</button>
   </div>

   <script>
       document.getElementById("parent").addEventListener("click", function() {
           console.log("Parent element clicked");
       });

       document.getElementById("child").addEventListener("click", function() {
           console.log("Child element clicked");
       });
   </script>
   ```
   If you click the "Click Me" button, both "Child element clicked" and "Parent element clicked" will be logged because the event bubbles up from the button to the parent `div`.

2. Event Capturing:
   - Event capturing is the reverse of event bubbling. It starts at the root of the document (the `window` object) and moves down the DOM hierarchy to the target element. This phase allows you to capture events before they reach their target element.

   Example:
   ```html
   <div id="parent">
       <button id="child">Click Me</button>
   </div>

   <script>
       document.getElementById("parent").addEventListener("click", function() {
           console.log("Parent element clicked (capturing)");
       }, true); // true enables capturing

       document.getElementById("child").addEventListener("click", function() {
           console.log("Child element clicked (bubbling)");
       });
   </script>
   ```
   In this example, the event listener on the parent element captures the event before it reaches the child button, so "Parent element clicked (capturing)" will be logged before "Child element clicked (bubbling)" when you click the button.

3. Event Propagation:
   - Event propagation refers to the process of an event traveling through the DOM hierarchy, either via bubbling or capturing, to reach its target and execute event handlers associated with it.

   You can use the `stopPropagation()` method to prevent further propagation of an event. For example:
   ```javascript
   document.getElementById("child").addEventListener("click", function(event) {
       console.log("Child element clicked");
       event.stopPropagation(); // Prevents the event from bubbling further
   });
   ```


# JavaScript Value vs Reference types.

In JavaScript, values can be categorized into two main types: primitive (value) types and reference (object) types. These categories determine how values are stored, copied, and compared in JavaScript.

**Primitive (Value) Types:**
Primitive types represent single values, and they are immutable, meaning their values cannot be changed after they are created.

1. **Number:**

   ```javascript
   let x = 5;
   let y = x; // y is a copy of the value 5
   x = 10;
   console.log(y); // Output: 5 (y remains unchanged)
   ```

2. **String:**

   ```javascript
   let str1 = "Hello";
   let str2 = str1; // str2 is a copy of the string "Hello"
   str1 = "Hi";
   console.log(str2); // Output: "Hello" (str2 remains unchanged)
   ```

3. **Boolean:**
   ```javascript
   let bool1 = true;
   let bool2 = bool1; // bool2 is a copy of the value true
   bool1 = false;
   console.log(bool2); // Output: true (bool2 remains unchanged)
   ```

**Reference (Object) Types:**
Reference types represent objects, and they are mutable, meaning their properties can be modified after they are created.

1. **Object:**

   ```javascript
   let person1 = { name: "John" };
   let person2 = person1; // person2 refers to the same object as person1
   person1.name = "Alice";
   console.log(person2.name); // Output: "Alice" (both variables reference the same object)
   ```

2. **Array:**

   ```javascript
   let arr1 = [1, 2, 3];
   let arr2 = arr1; // arr2 refers to the same array as arr1
   arr1.push(4);
   console.log(arr2); // Output: [1, 2, 3, 4] (both variables reference the same array)
   ```

3. **Function:**

   ```javascript
   function greet(name) {
     return "Hello, " + name + "!";
   }

   let sayHello = greet;
   console.log(sayHello("Alice")); // Output: "Hello, Alice!"
   ```

In each example of reference types, you can see that changes made to the original object or array through one reference affect the other reference as well because they both point to the same underlying data.
