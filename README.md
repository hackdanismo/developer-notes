# Developer notes
A collection of developer notes, code snippets and coding examples to improve the development experience and sharing of knowledge.

+ [JavaScript](#javascript)
    + [Scripts](#scripts)
    + [Comments](#comments)
    + [Variables](#variables)
    + [Functions](#functions)
    + [Select Elements](#select-elements)
    + [Events](#events)
    + [Array](#array)
    + [Objects](#objects)
+ [Express](#express)

## JavaScript

### Scripts
Adding `JavaScript` to `HTML` using a `<script>` tag before the closing `</body>` tag:

```html
    <!-- Rest of the HTML document, here -->

<script src="scripts/script.js"></script>
</body>
</html>
```

### Comments
`JavaScript` supports two types of comment. A `single-line` and a `multi-line` comment.

```javascript
// This is a single-line comment

/* This is also a comment */

/*
 * This is a multi-line comment.
 * The comment can be over multiple lines making it easier to read.
 */
```

### Variables
Variables are containers used to store data in JavaScript.

+ Use `const` by default. Cannot be redeclared or updated. Block-scoped, only exists inside `{` and `}`.
+ Use `let` if the value needs to change. lock-scoped, only exists inside `{` and `}`.
+ Try to avoid the use of `var` in modern JavaScript code.

```javascript
var name = "Dan";
let name = "Dan";
const name = "Dan";
```

Using variables:

```javascript
function testFunc() {
    let name = "Dan";
    console.log(name);    // This will output the variable
}

console.log(name);    // Error, not defined
```

### Functions
A simple `JavaScript` function:

```javascript
function testFunc() {
    console.log("This is a test function");
}

// This can also be rewritten using the later ES6 syntax:
const testFunc = () => {
    console.log("This is a test function");
}

// Call the function
testFunc();
```

Use a `parameter` to pass in a value - "Dan" - as an argument into the function when called. Use a `template literal` to output the value.

```javascript
const testFunc = name => {
    console.log(`Hello, ${name}`);
}

// Call the function
testFunc("Dan");
```

Default values for the `parameter` can also be set to avoid an `undefined` value being returned if no value is passed as an `argument`. This will return: `Hello, Guest`:

```javascript
const testFunc = (name = "Guest") => {
    console.log(`Hello, ${name}`);
}

// Call the function
testFunc();
```

**Example**: Convert Fahrenheit to Celsius:

```javascript
const fahrenheitToCelsius = fahrenheit => {
    return (fahrenheit - 32) * 5 / 9;
}

console.log(fahrenheitToCelsius(100));
```

### Select Elements
Elements in the `DOM (Document Object Model)`, can be selected using JavaScript.

To select by **ID**:

```html
<h1 id="title">Hello World</h1>
```

```javascript
const title = document.getElementById("title");
console.log(title.textContent);        // Hello World
```

To select by **class**:

```html
<p class="item">First</p>
<p class="item">Second</p>
```

```javascript
const items = document.getElementsByClassName("item");
console.log(items[0].textContent);        // First
```

To select by **tag name**:

```html
<li>One</li>
<li>Two</li>
```

```javascript
const listItems = document.getElementsByTagName("li");
console.log(listItems.length);        // 2
```

To select elements using the modern `querySelector` and `querySelectorAll` methods:

```html
<div class="card">Card A</div>
<div class="card">Card B</div>
```

```javascript
const firstCard = document.querySelector('.card'); // first match
console.log(firstCard.textContent); // "Card A"

const allCards = document.querySelectorAll('.card'); // NodeList of all
allCards.forEach(card => console.log(card.textContent));
```

Travese from a selected element:

```javascript
const list = document.querySelector('ul');

console.log(list.children);   // All <li> inside
console.log(list.parentNode); // The parent element
console.log(list.nextElementSibling); // The element after it
```

### Events
JavaScript code can be triggered based on events:

```javascript
const button = document.querySelector(".js-btn");

button.addEventListener("click", () => {
    alert("The button has been clicked");
});
```

Or looping over multiple elements with the same class/selector:

```javascript
const button = document.querySelectorAll(".js-button");

button.forEach(selectedButton => {
	selectedButton.addEventListener("click", () => {
		alert("A specific button has been clicked");
	});
});
```

### Array
There are a few ways to create an `array`:

```javascript
let empty = [];        // An array with no elements
let primes =[2, 3, 5, 7, 11];        // An array with 5 numeric elements
let misc = [1.1, true, "a"];        // 3 elements of various types
```

### Objects
When a function is defined inside of an object it is called a `method`. Prior to ES6, a method would be defined as an object literal.

```javascript
let square = {
    area: function() {
        return this.side * this.side
    },
    side: 10
};

square.area()    // 100
```

In ES6, has been extended to allow a shortcut where the `function` keyword no longer needs to be used along with the colon:

```javascript
let square = {
    area() {
        return this.side * this.side
    },
    side: 10
};

square.area()    // 100
```

## Express
`Express.js` (or just `Express`) is a minimal, unopinionated web framework for `Node.js`.

Think of it as a lightweight toolkit that makes it much easier to build: `web servers`, `APIs`, and `full-stack apps` with `Node`.

To install `Express`, `Node` needs to be installed/setup and we also need a `package.json` file in the root of the project folder. It is recommended to have a `.gitignore` file created in the project before installing packages to avoid the `node_modules` directory being added to version control (e.g. `GitHub`).

```shell
# Make a folder for the project
$ mkdir project
$ cd project
# Generate a package.json file
$ npm init -y

# Check the version of Node installed
$ node --version

# Install Express as a dependency package, creating the node_modules folder
$ npm install express
```

A simple `Express` example, within a file named `index.js`:

```javascript
const express = require('express');
const app = express();

// Middleware to parse JSON bodies
app.use(express.json());

// Route
app.get('/', (req, res) => {
    res.send("Hello, Express");
});

app.listen(3000, () => console.log("http://localhost:3000"));
```

To run this code, which can then be opened in: `http://localhost:3000` using port `3000`:

```shell
$ node index.js
```
