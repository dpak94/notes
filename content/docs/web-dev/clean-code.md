---
type: "docs"
title: Clean Code for JS
draft: false
---

# Clean Code Norms For JavaScript

```js
// Example A : Bad Code
const x = function (z) {
  const w = "Hello";
  return w + z;
};

// Example B : Good Code
const generateUserGreeting = function (name) {
  const greeting = "Hello";
  return greeting + name;
};
```

Of the above two examples, code B is:

1. Easy to read.
2. Assigns names to functions and variables that convey their task/nature instead of single letters, resultin in less confusion.
3. Assigned names follow _camelCase_ naming convention.

---

## Naming Functions and Variables

### 1. A good name is descriptive

Variables should always begin with a noun or an adjective (that is, a noun phrase) and functions with a verb. The only exception would be constants, which must be declared with all caps.

```js
let getName = "Alex"; // Bad variable name 👎🏽👎🏽👎🏽
let userName = "Alex"; // Good variable name 👍👍👍
```

```js
const MILLISECONDS_PER_HOUR = 60 * 60 * 1000;
```

### 2. Use consistent vocabulary

Do not use threee different verbs for the same kind of task when assigning names to variables.

In the below bad example, 3 different verbs (_get, fetch & retrieve_) are used

```js
let sumArray; 👍
let array1; 👎
```

```js
// Good
function getPlayerScore();
function getPlayerName();
function getPlayerTag();

// Bad
function getUserScore();
function fetchPlayerName();
function retrievePlayerOneTag();
```

### 3. Use searchable and easily understandable names

Instead of

```js
setTimeout(stopTimer, 3600000);
```

implement

```js
const MILLISECONDS_PER_HOUR = 60 * 60 * 1000; // 3,600,000;

setTimeout(stopTimer, MILLISECONDS_PER_HOUR);
```

---

## Other rules for clean code

1. Don't comment where you're supposed to use Git.
2. Don't comment _how_, comment _why_. The viewer reads the code to find _how_.
3. Semicolons are optional, JS Compiler takes care of it by adding semicoloms automatically.
4. When employing a formula in a function, it would be a good idea to put a brief comment explaining the formula.
5. Use correct indentation.
6. Avoid abusive comments.
7. Avoid extremely large function. Break them into smaller ones.
8. Treat changes with caution.
9. Avoid indiscriminate mixing of coding languages
10. Summarize the imported files, packages etc.

---

## More Info

- [AirBnB Style Guide for JavaScript Styling](https://github.com/airbnb/javascript)
- [Beautiful JavaScript: Easily Create Chainable (Cascading) Methods for Expressiveness](https://web.archive.org/web/20190211152543/https://javascriptissexy.com/beautiful-javascript-easily-create-chainable-cascading-methods-for-expressiveness/)
