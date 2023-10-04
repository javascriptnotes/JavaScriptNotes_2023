# Contents to be covered in this session.

## 1. JavaScript DOM Manipulation.

## 2. JavaScript DOM Model. (Same as Point No. 1)

## 3. JavaScript DOM Selectors.

## 4. JavaScript DOM Creating and Adding HTML elements to page.

## 5. DOM Project - To-do-List Application - Refer Session:- (Sep, 30 2023 - Oct, 01 2023)

# JavaScript DOM Manipulation.

JavaScript DOM manipulation refers to the process of using JavaScript to interact with the Document Object Model (DOM) of a web page. The DOM represents the structure of an HTML document and allows you to access and modify its elements and content dynamically, without requiring a page reload. DOM manipulation is a fundamental part of front-end web development and is used to create interactive and dynamic web applications.

Here are some common tasks and techniques for JavaScript DOM manipulation:

1. **Accessing DOM Elements:**

   - You can access DOM elements using methods like `getElementById`, `getElementsByClassName`, `getElementsByTagName`, and `querySelector`.

   ```javascript
   // Example: Get an element by its ID
   const element = document.getElementById("myElement");
   ```

2. **Modifying Element Properties:**

   - You can change element properties like `innerHTML`, `textContent`, `style`, and more to update the content and appearance of elements.

   ```javascript
   // Example: Change the text content of an element
   const element = document.getElementById("myElement");
   element.textContent = "New Text";
   ```

3. **Adding and Removing Elements:**

   - You can create new elements using `document.createElement` and add them to the DOM with `appendChild`. Conversely, you can remove elements using `removeChild`.

   ```javascript
   // Example: Create a new paragraph element and append it to the body
   const paragraph = document.createElement("p");
   paragraph.textContent = "New paragraph";
   document.body.appendChild(paragraph);
   ```

4. **Event Handling:**

   - You can attach event listeners to DOM elements to respond to user interactions such as clicks, mouse movements, and keyboard input.

   ```javascript
   // Example: Add a click event listener to a button element
   const button = document.getElementById("myButton");
   button.addEventListener("click", function () {
     alert("Button clicked!");
   });
   ```

5. **Modifying CSS Styles:**

   - You can change CSS styles dynamically using JavaScript by accessing the `style` property of an element.

   ```javascript
   // Example: Change the background color of an element
   const element = document.getElementById("myElement");
   element.style.backgroundColor = "blue";
   ```

6. **DOM Traversal:**

   - You can navigate through the DOM using properties like `parentNode`, `childNodes`, `nextSibling`, and `previousSibling` to find and manipulate related elements.

   ```javascript
   // Example: Traverse the DOM to find a sibling element
   const element = document.getElementById("myElement");
   const sibling = element.nextElementSibling;
   ```

7. **Manipulating Classes:**

   - You can add, remove, or toggle CSS classes on elements using the `classList` property.

   ```javascript
   // Example: Add a class to an element
   const element = document.getElementById("myElement");
   element.classList.add("active");
   ```

# JavaScript DOM Selectors.

JavaScript DOM (Document Object Model) selectors are methods or properties that allow you to access and manipulate HTML elements within a web page. These selectors are crucial for dynamically interacting with the content of a web page using JavaScript. There are several ways to select HTML elements in the DOM:

1. **getElementById**: This method allows you to select an element by its unique `id` attribute.

   ```javascript
   const element = document.getElementById("elementId");
   ```

2. **getElementsByClassName**: This method selects elements by their `class` attribute and returns a collection (HTMLCollection) of elements with the specified class.

   ```javascript
   const elements = document.getElementsByClassName("className");
   ```

3. **getElementsByTagName**: This method selects elements by their HTML tag name and returns a collection of elements with the specified tag.

   ```javascript
   const elements = document.getElementsByTagName("tagname");
   ```

4. **querySelector**: This method allows you to select the first matching element using CSS-style selectors.

   ```javascript
   const element = document.querySelector("selector");
   ```

5. **querySelectorAll**: This method selects all matching elements using CSS-style selectors and returns a NodeList (which is similar to an array).

   ```javascript
   const elements = document.querySelectorAll("selector");
   ```

6. **parentNode, children, nextSibling, previousSibling**: You can navigate the DOM tree using these properties to access related elements.

   ```javascript
   const parentElement = element.parentNode;
   const childrenElements = element.children;
   const nextSiblingElement = element.nextSibling;
   const prevSiblingElement = element.previousSibling;
   ```

7. **closest**: This method allows you to find the nearest ancestor that matches a selector.

   ```javascript
   const closestElement = element.closest("selector");
   ```

8. **getAttribute**: You can use this method to get the value of an attribute of an element.

   ```javascript
   const attributeValue = element.getAttribute("attributeName");
   ```

9. **querySelector and querySelectorAll with data attributes**: You can also use these methods to select elements based on custom data attributes.

   ```javascript
   const elementsWithCustomDataAttribute = document.querySelectorAll(
     '[data-custom-attribute="value"]'
   );
   ```

10. **Document properties**: You can access some commonly used elements directly from the `document` object, such as `document.body` for the `<body>` element and `document.head` for the `<head>` element.

```javascript
const bodyElement = document.body;
const headElement = document.head;
```

# JavaScript DOM Creating and Adding HTML elements to page.

In JavaScript, you can manipulate the Document Object Model (DOM) to create and add HTML elements to a web page dynamically. Here's a step-by-step guide on how to do it:

1. **Create a New HTML Element**:
   To create a new HTML element, you can use the `document.createElement()` method. This method takes the name of the HTML element you want to create as an argument and returns a new element object. For example, to create a new `div` element:

   ```javascript
   const newDiv = document.createElement("div");
   ```

2. **Set Element Properties and Attributes**:
   You can set properties and attributes of the newly created element using JavaScript. For instance, you can set the `id`, `class`, `textContent`, or other attributes:

   ```javascript
   newDiv.id = "myDiv";
   newDiv.className = "custom-class";
   newDiv.textContent = "This is a dynamically created div element.";
   ```

3. **Append the Element to the DOM**:
   To add the newly created element to the web page, you need to append it to an existing element in the DOM. You can use methods like `appendChild()`, `insertBefore()`, or `insertAdjacentElement()` to do this.

   ```javascript
   // Append to an existing element with id "container"
   const container = document.getElementById("container");
   container.appendChild(newDiv);
   ```

4. **Example**: Putting it all together:

   ```javascript
   // Create a new div element
   const newDiv = document.createElement("div");

   // Set properties and attributes
   newDiv.id = "myDiv";
   newDiv.className = "custom-class";
   newDiv.textContent = "This is a dynamically created div element.";

   // Append to an existing element with id "container"
   const container = document.getElementById("container");
   container.appendChild(newDiv);
   ```

5. **Complete HTML Example**:
   Here's a complete HTML example that demonstrates creating and adding elements to a page:

   ```html
   <!DOCTYPE html>
   <html>
     <head>
       <title>Dynamic Element Creation</title>
     </head>
     <body>
       <div id="container">
         <!-- Existing content -->
       </div>

       <script>
         // JavaScript code to create and add an element
         const newDiv = document.createElement("div");
         newDiv.id = "myDiv";
         newDiv.className = "custom-class";
         newDiv.textContent = "This is a dynamically created div element.";

         const container = document.getElementById("container");
         container.appendChild(newDiv);
       </script>
     </body>
   </html>
   ```
