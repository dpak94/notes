---
layout: post
title: JavaScript
permalink: /javascript/
---

- [JavaScript Notes](#javascript-notes)
  - [Variables in JS](#variables-in-js)
    - [Declaring constants in JavaScript](#declaring-constants-in-javascript)
  - [Functions](#Functions)
  - [Object Oriented Programming](#Object-Oriented-Programming)

JavaScript is a language used along with HTML and CSS to communicate with the user.

- `console.log("text")` is used to print something to the developer console in the browser
- Link a **JS** script file to the html file by using command `<script src="javascript.js"></script>`

---

## Variables in JS

`let message;`

Now, put some data into the variable by using assignment operator `=` :

```js
let message;

message = "Hello"; //store the string 'Hello' in the variable message
```

Access the stored variable **message** using the variable name :

`alert(message); // shows the variable content`

Variable declaration and printing its content in a more precise way as :

```js
let message = "Hello";
alert(message);
```

Declare multiple variables in single line (not recommended, use multi-lines or multiline style, where after comma each variable lies in a new line for readability) :

```js
let user = "John",
  age = 25,
  message = "Hello";
```

> [!NOTE]
> In older scripts, `var` is used inplace of `let`  
> **Eg:** `var message = 'Ciao';`

> [!IMPORTANT]
>
> 1. The name must only contain letters, digits or symbols **$** and **\_**.
> 2. The first character must not be digit.
> 3. Case matters. **apple** and **APPLE** are differnet variables.
> 4. Do not draw variables from [reserved words](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#reserved_words)

> When the name contains multiple words, <b>camelCase</b> is commonly used. That is: words go one after another, each word except first starting with a capital letter: **myVeryLongName**

### Declaring constants in JavaScript

`const myBirthday = '18.04.1982;`

Any attempt to reassign value would result in error.

1. We generally use upper case for constants that we "hard-coded" i.e., when the value is known prior to execution and directly written into the code.
   **Eg :** birthday, planet count etc.

---

## String Literals & Multi-line Strings

Use backtick (`) in place of ' ' or " "

```js
const firstName = "stranger";
const firstJob = "writer";
const birthYear = 1901;

desc = `I'm ${firstName} and my first job was ${firstJob}.`;
console.log(desc);
// I am stranger and I was born in 1901 and my first job was writer
```

**Multi-line Strings**

Strarting from 2015, thanks to ES6, multi-line strings can be written like below :

```js
console.log(`
I'm a party worker
from Sevastopol.
I came here yesterday.`);
```

**Note :** Don't forget to use backticks (`) instead of ' or " for the string.

---

## Type Conversion and Coercion

```js
const inputYear = "1991";
console.log(typeof inputYear); // 1991
console.log(Number(inputYear) + 18); // 2009
console.log(Number("Jonas")); //NaN
console.log(typeof NaN); // number

// Type Coercion
console.log("24" + 2); // 242
console.log("12" * "12"); // 144
```

---

## Truthy & Falsy Values

```js
// Truthy and Falsy Values

console.log(Boolean(0)); // false
console.log(Boolean(undefined)); // false
console.log(Boolean({})); //true
console.log(Boolean("")); // false

const money = 0;
if (money) {
  console.log("Don't spend it all!");
} else {
  console.log("Earn money First!");
} // Earn money First !!!

let height;
if (height) {
  console.log("Good! Height is defined!");
} else {
  console.log("Please define height!!!");
} // Please define Height!!!
```

---

## Operators

### Equality Operators

`===` and `==` are equality operators.

```js
// Equality Operators
const age = 18;

if (age === 18) console.log("You are an adult!!!! (strict)");
// You are an adult !!!! (strict) === > Comparison Operator
if (age == 18) console.log("You are an adult!!!! (strict)");
// You are an adult !!!! (loose) == > Comparison Operator

// Always use strict equality operator (===) over loose equality operator (==)
```

```js
const favNum = Number(prompt("What's your favorite Number ?"));
console.log(`Your favorite number is ${favNum}`);

if (favNum === 23) {
  console.log(`23 is a favorite number`);
}
//  === strictly treats the variable as a string.
// Thus the if condition is not true
else if (favNum === 16) {
  console.log(`16 is the second fav number`);
} else if (favNum !== 16) {
  console.log(`16 is not the second fav number`);
} else {
  console.log(`Not a favorite number`);
}
```

```js
// Boolean Logic Basics
let isIsland = false;
let isPeninsula = true;

console.log(`AND result for the statements : ${isIsland && isPeninsula}`); // false
console.log(`OR result for the statements : ${isIsland || isPeninsula}`); // true
console.log(`NOT result for the statements : ${!isIsland || !isPeninsula}`); //true
```

### Ternary (Conditional) Operator

```js
// Conditional Operator

const age = 25;
age >= 18
  ? console.log(`I like to drink wine 🍷 (❁´◡\`❁)`)
  : console.log(`I had to drink water 💧 
😒`); // `I had to drink water 💧 😒`
```

```js
// Conditional Operator
let age = 15;
const drink = age >= 18 ? "wine 🍷" : "water 💧";
console.log(drink); // water 💧

let drink2;
if (age >= 18) {
  drink2 = "wine 🍷";
} else {
  drink2 = "water 💧";
}
console.log(drink2); // water 💧
console.log(`I like to drink ${age >= 18 ? "wine 🍷" : "water 💧"}`); // water 💧
```

## Switch Statements

```js
// Switch Statements
const day = "thursday";

switch (day) {
  case "monday":
    console.log("Plan my course");
    console.log("Go to coding meetup");
    break;
  case "tuesday":
    console.log("Prepare course material");
    console.log("Sheen the roof");
    break;
  case "wednesday":
    console.log("Record Vids");
    break;
  case "thursday":
    console.log("Upload the vids");
    break;
  default:
    console.log("Not a valid day.");
}
```

## JavaScript Releases

**Brief History of JS:**

- Brendan Eich creates the first version of JavaScript in 10 days. Initially called **Mocha**

- EcmaScript 1 released in 1997

- **ES5** released in 2015 with lots of great new features.

- **ES6** brought biggest updates to the language. \*_ECMAScript_ \* changes to yearly releases.

- Modern JavaScript Engine is backwards compatible.

## Strict Mode

```js
"use strict"; // Activates strict mode for the entire script file
```

- Avoids accidental bugs and errors in the code.

- Prefer to turn on Strict Mode while coding.

---------------------------------------

## Functions

```js
// Functions
function logger() {
  // Function Definition
  console.log("My Name is John");
}
logger(); // Function Calling/ invoking / running

function fruitProcessor(apples, oranges) {
  console.log(apples, oranges);
  const juice = `Juice with ${apples} apples and ${oranges} oranges.`;
  return juice;
}

const appleJuice = fruitProcessor(5, 6);
console.log(appleJuice);
// My Name is John
// 5 6
// Juice with 5 appleas and 6 oranges
```

**Function Declaration and Expression**

```js
// JavaScript Function Declaration
function calcAge(birthYear) {
  return 2024 - birthYear;
}
const age = calcAge(1994);

// Function Expression
const calcAge2 = function (birthYear) {
  return 2024 - birthYear;
};
const age2 = calcAge2(1997);
console.log(age, age2); // 30 27
```

**Arrow Function**

```js
// Arrow Function
// Like Lambda Function in Python. Easy to write a function
const yearsUntilRetirement = (birthYear, firstName) => {
  const age = 2024 - birthYear;
  const retirement = 65 - age;
  // return retirement;
  return `Hello ${firstName}, you will retire in ${retirement} years.`;
};

console.log(yearsUntilRetirement(1994, "Jackson"));
// Hello Jackson, you will retire in 35 years.
```

**Functions Calling Other Functions**

```js
// Function(s) calling other function(s)
function cutFruitPieces(fruit) {
  return fruit * 4;
}

function FruitProcessor(apples, oranges) {
  applePieces = cutFruitPieces(apples);
  orangePieces = cutFruitPieces(oranges);
  const juice = `Juice made with ${applePieces} pieces from ${oranges} oranges & ${orangePieces} pieces from ${apples} apples`;
  return juice;
}

console.log(FruitProcessor(3, 3));
// Juice made with 12 pieces from 3 oranges & 12 pieces from 3 apples
```

## Arrays

- [Array MDN Docs Reference]([Array - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

```js
// Arrays
const friends = ["Mike", "Ike", "Jake", "Pike", "Kyle"];
console.log(friends[1]); // Ike
const years = new Array(1991, 1992, 1993, 1997);
console.log(years[2]); // 1993
console.log(friends[friends.length - 1]); // Access last element - Kyle
// Index starts from 0 (same as Python)
friends[2] = "Jim"; // Replacing an element in array
console.log(friends[2]); // Jim
const nome = "Tyler";
// Adding a variable as an array member
friends[5] = nome;
console.log(friends); // (6) ['Mike', 'Ike', 'Jim', 'Pike', 'Kyle', 'Tyler']
console.log(friends.length); // Length of the array - 6
```

**Array Methods**

```js
// Array Methods
const friends = ["Michael", "John", "Charles", "William", "George"];

friends.push("Jake"); // Adds elements to the end of the array
console.log(friends); // (6) ['Michael', 'John', 'Charles', 'William', 'George', 'Jake']

friends.unshift("Richard"); // Adds elements at the beginning of the array
console.log(friends); // (7) ['Richard', 'Michael', 'John', 'Charles', 'William', 'George', 'Jake']

friends.pop(); // Removes the last element
console.log(friends); // ['Richard', 'Michael', 'John', 'Charles', 'William', 'George']

friends.shift(); // Removes the first element
console.log(friends); //(5) ['Michael', 'John', 'Charles', 'William', 'George']

console.log(friends.indexOf("Charles")); // Gives the index of element => 2
console.log(friends.indexOf("William")); // Gives the index of element => 3
// ES6 Method to confirm the existence of element
console.log(friends.includes("William")); // Modern method
```

## Objects

- SImilar to dictionaries in Python

```js
// Objects (Dictionaries)
const myBio = {
  firstName: "Dpak",
  lastName: "94",
  age: 29,
  job: "Engineer",
  hobbies: ["gaming", "movies", "book reading"],
};
// Accessing the contents of the objects
console.log(myBio["firstName"]); // Dpak
console.log(myBio.age); //29
myBio.city = "Hyderabad";
console.log(myBio["city"]);

const query = prompt("What do you want to know about the user?");
console.log(myBio[query]);

if (myBio[query]) {
  console.log(myBio[query]);
} else {
  console.log("Please enter valid data query");
}
```

```js
// Best Friend Challenge. Print the No. of Jonas's friends and his best friend.
bioData = {
  name: "Jonas",
  friends: ["Mike", "Pike", "Richard", "Wilhelm"],
  age: 24,
  location: "Deutschland",
};

console.log(
  `${bioData.name} has ${bioData["friends"].length} friends. His best friend is ${bioData.friends[0]}.`
);
// Jonas has 4 friends. His best friend is Mike.
```

### Object Methods

```js
// this keyword - used to indicate the curent object
const jonas = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  job: "Engineer",
  friends: ["Rob", "Tom", "Dan", "Ulrich"],
  hasDriversLicense: false,
  birthYear: 1991,
  ageCalc: function () {
    this.age = 2024 - this.birthYear;
    return this.age;
    // "this" replacing the current object the element is a member of.
  },
};
console.log(jonas.ageCalc()); // 33 Use dot notation to access the function output i.e age
console.log(jonas.age); // 33 The age variable in the ageCalc function

// Challenge
// Jonas is a 46 year old teacher.....

getSumm = function () {
  return `${jonas.firstName} is a ${jonas.ageCalc()} years old programmer. He ${
    this.hasDriversLicense ? `has` : `does not have`
  } a Driver's License.`;
};
console.log(getSumm());
// Jonas is a 33 years old programmer. He does not have a Driver's License.
```

## Loops

### for loop

```js
const jonas = [
  "Jonas",
  "Schmedtmann",
  "Engineer",
  420,
  ["Rob", "Tom", "Dan", "Ulrich"],
];
const types = [];

for (let i = 0; i < jonas.length; i++) {
  console.log(jonas[i], typeof jonas[i]);
  types.push(typeof jonas[i]);
}
console.log(`New types array : ${types}`); //Outputs the new array.
```

```js
// Nested Loops
const players = ["Mark", "Peter", "Thomas"];
const sports = ["Cricket", "Wrestling", "Soccer"];

for (let player = 0; player < players.length; player++) {
  for (let sport = 0; sport < sports.length; sport++) {
    console.log(`${players[player]} plays ${sports[sport]}. `);
  }
}
```

```js
// While Loop
let rep = 1;
while (rep <= 10) {
  console.log(`While : Running instance ${rep}`);
  rep++;
}
```

--------------

## Object Oriented Programming

**Features of OOP:**

1. Encapsulation
2. Abstraction
3. Inheritance
4. Polymorphism

- OOP in JS uses Prototypal Inheritance

### 3 ways of Implementing Prototypal Inheritance in JS

1. Constructor Functions
   - Technique to create objects from a function
   - **Examples** - Arrays, Maps & Sets
2. ES6 Classes
   - Modern alternative to constructive function syntax
   - ES6 classes work exactly like **constructor classes**
   - ES6 Classes do not behave like classes in "classical OOP"
3. Object.create()
   - Easiest & most straight-forward way to create objects
   - Not commmonly used.

--------

### Constructor Functions

``` js
console.log(`${fatherName} is your father`);
let x = 6;
var y = 9;
console.log(x, y);
```

**Note** - Never create Functions inside constructor functions.

``` js
// Constructor Function
const Person = function (firstName, birthYear) {
  this.firstName = firstName;
  this.birthYear = birthYear;  
  this.calcAge = 2024 - this.birthYear;
};

console.log(new Person('Jonas', 1994));
// 1. New empty object is created
// 2. Function is called, this = empty object
// 3. The empty object is linked to a prototype
// 4. Function  automatically returns empty object

const matilda = new Person('matilda', 2017);
const jack = new Person('Jack', 1975);
console.log(matilda, jack);

console.log(jack instanceof Person); // Checking if an object is an isntance of the constructor function
```

``` txt
// Output
Person {firstName: 'Jonas', birthYear: 1994, calcAge: 30}
Person {firstName: 'matilda', birthYear: 2017, calcAge: 7} 
Person {firstName: 'Jack', birthYear: 1975, calcAge: 49}
true
```


### Prototypes

``` js



```

