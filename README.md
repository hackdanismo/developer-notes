# Developer notes
A collection of developer notes, code snippets and coding examples to improve the development experience and sharing of knowledge.

+ [JavaScript](#javascript)
    + [Variables](#variables)
    + [Functions](#functions)
+ [Express](#express)

## JavaScript

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
