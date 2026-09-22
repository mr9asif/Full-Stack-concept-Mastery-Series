### Q1. What is the difference between var, let, and const in JavaScript?

### 🎤 How to answer

“Var, let, and const are used to declare variables in JavaScript. let and const were introduced in ES6. The main difference is their scope and how they behave with hoisting. var is function-scoped, while let and const are block-scoped. All three are hoisted, but var is initialized with undefined, so we can access it before its declaration and get undefined. let and const are also hoisted, but they remain in the Temporal Dead Zone until their declaration is reached, so accessing them before declaration results in a ReferenceError.”

### Q2. Explain the concept of hoisting in JavaScript.

### 🎤 How to answer

"Hoisting is JavaScript's behavior where declarations are processed before the code is executed. Because of this, some variables and functions can be accessed before their declaration appears in the code. Function declarations are fully hoisted, while var is hoisted and initialized with undefined. let and const are also hoisted internally, but they cannot be accessed before initialization because of the Temporal Dead Zone."

### Q3. What are the primitive data types in JavaScript?

### 🎤 How to answer

"JavaScript has seven primitive data types: string, number, bigint, boolean, undefined, symbol, and null. Primitive values are immutable and are not objects."

### 🔄 Counter question

Q: Is null a primitive?

Yes, null is a primitive value, although typeof null returns "object" because of a historical JavaScript behavior.

### Q4. What is the difference between == and ===?

### 🎤 How to answer

"== is loose equality. It can perform type conversion before comparing values. === is strict equality, so it compares both value and type without implicit type conversion. In most cases, I prefer === because it gives more predictable results."

### 🔄 Counter question

Q: Which one do you usually prefer?

I usually prefer === because it avoids unexpected type coercion.

### Q5. Explain closures in JavaScript with an example.

### 🎤 How to answer

"A closure happens when an inner function remembers and can access variables from its outer function even after the outer function has finished executing."

### Example

```js
function counter() {
  let count = 0;

  return function () {
    count++;
    return count;
  };
}

const increment = counter();

console.log(increment()); // 1
console.log(increment()); // 2
console.log(increment()); // 3
```

### 🔄 Counter questions

Q: Why are closures useful?

They are useful for data privacy, maintaining state, callbacks, event handlers, and creating function factories.

Q: Does the count variable disappear after counter() finishes?

Normally the outer function's execution is finished, but because the returned function still references count, JavaScript keeps that variable available through the closure.

### Q7. What are arrow functions and how do they differ from regular functions?

### 🎤 How to answer

"Arrow functions provide a shorter syntax for writing functions. The biggest difference is that arrow functions don't have their own this; they inherit this from their surrounding lexical scope. They also don't have their own arguments object and cannot be used as constructors with new."

### 💻 Example

Regular function:

```
function add(a, b) {
  return a + b;
}

Arrow function:

const add = (a, b) => a + b;
```

### 🔄 Counter question

Q: Does an arrow function have its own this?

No. It inherits this from its surrounding scope.

### Q8. What is the scope chain in JavaScript?

🎤 How to answer

"The scope chain is the mechanism JavaScript uses to find variables. When JavaScript can't find a variable in the current scope, it looks in the outer scope, and then continues toward the global scope."

### 💻 Example

```
let name = "Asif";

function outer() {
  let age = 22;

  function inner() {
    console.log(name);
    console.log(age);
  }

  inner();
}

outer();
```

Inside inner(), JavaScript searches:

inner scope
↓
outer scope
↓
global scope

### 🔄 Counter question

Q: What happens if JavaScript can't find the variable anywhere?

It throws a ReferenceError.

### Q9. Explain the Temporal Dead Zone.

### 🎤 How to answer

"The Temporal Dead Zone, or TDZ, is the period between entering a block scope and the point where a let or const variable is initialized. During this period, accessing the variable causes a ReferenceError."
"Temporal Dead Zone means we cannot access a let or const variable before its declaration is reached. If we try to access it before that point, JavaScript gives a ReferenceError."

### 🔄 If interviewer asks: "Why does TDZ exist?"

You can say:

"It helps prevent us from accidentally using a variable before it has been properly initialized."

### 💻 Example

```
console.log(age); // ❌ ReferenceError

let age = 22;

You can think of it like:

Block starts
    ↓
TDZ
    ↓
let age = 22
    ↓
Variable can be accessed
```

### 🔄 Counter question

Q: Does var have a Temporal Dead Zone?

No. var is initialized with undefined during hoisting.

### Q10. What is a pure function?

### 🎤 How to answer

"A pure function is a function that always produces the same output for the same input and does not cause side effects or modify external state."

### 💻 Example

```
function add(a, b) {
  return a + b;
}

console.log(add(2, 3)); // 5

Same inputs → same output.

❌ Not pure
let total = 0;

function addToTotal(value) {
  total += value;
}
```

It modifies external state.

### 🔄 Counter question

Q: Why are pure functions useful?

They are easier to test, debug, reuse, and reason about.

### Q11. Difference between function declaration and function expression?

### 🎤 How to answer

"A function declaration defines a function directly using the function keyword, while a function expression assigns a function to a variable. Function declarations are fully hoisted, so they can be called before they appear in the code. Function expressions generally cannot be used before the variable is initialized."

### 💻 Example

```
Function declaration
sayHello();

function sayHello() {
  console.log("Hello");
}
Function expression
const sayHello = function () {
  console.log("Hello");
};

sayHello();
```

### 🔄 Counter question

Q: Which one is hoisted?

Function declarations are fully hoisted. Function expressions follow the hoisting behavior of the variable they're assigned to.

### Q12. What are default parameters?

### 🎤 How to answer

"Default parameters allow us to provide a default value for a function parameter when the caller doesn't provide a value or passes undefined."

### 💻 Example

```
function greet(name = "Guest") {
  return `Hello ${name}`;
}

console.log(greet("Asif"));
// Hello Asif

console.log(greet());
// Hello Guest
```

### 🔄 Counter question

### Q: What happens if I pass null?

greet(null);

The default value is not used because null is an actual value.

### Q13. What is the typeof operator?

### 🎤 How to answer

"typeof is an operator used to determine the type of a value. It returns a string representing the type."

### 💻 Examples

typeof "Hello"; // "string"
typeof 10; // "number"
typeof true; // "boolean"
typeof undefined; // "undefined"
typeof 10n; // "bigint"
typeof Symbol(); // "symbol"
typeof {}; // "object"
typeof function(){}; // "function"
typeof null; // "object"

### 🔄 Counter question

Q: Is typeof null correct?

It returns "object", which is a historical JavaScript quirk.

### Q14. Explain type coercion in JavaScript.

### 🎤 How to answer

"Type coercion is the process of converting a value from one type to another. JavaScript can perform this conversion automatically, which is called implicit coercion, or we can do it manually, which is explicit coercion."

### 💻 Implicit coercion

```
console.log("5" + 2);
// "52"

JavaScript converts 2 to a string.

Another example:

console.log("5" - 2);
// 3

Here JavaScript converts "5" to a number.

Explicit coercion
Number("10");   // 10
String(10);     // "10"
Boolean(1);     // true
```

### 🔄 Counter question

Q: Why can type coercion cause bugs?

Because JavaScript sometimes converts types automatically, which can produce unexpected results. That's one reason I prefer strict equality ===.

### Q15. What is an IIFE?

### IIFE = Immediately Invoked Function Expression

### 🎤 How to answer

"An IIFE is a function expression that is defined and immediately executed. It is mainly used to create a private scope and avoid polluting the global scope."

### 💻 Example

```
(function () {
  console.log("Hello");
})();

It executes immediately.

You can also use an arrow function:

(() => {
  console.log("Hello");
})();
```

### 🔄 Counter questions

Q: Why would you use an IIFE?

"Historically, IIFEs were commonly used to create private variables and avoid global namespace pollution. With modern JavaScript, modules are generally preferred for this purpose."

Example:

(function () {
const secret = "12345";
console.log(secret);
})();

// secret is not accessible here

Q: Is an IIFE still commonly used in modern JavaScript?

"Not as much as before. ES modules provide a cleaner way to create module scope, but IIFEs are still useful in some situations."

JavaScript Fundamentals II

### Q16. What is destructuring in JavaScript?

### 🎤 How to answer

"Destructuring is a JavaScript feature that allows us to extract values from arrays or properties from objects and store them directly into variables. It makes the code shorter and more readable."

### 💻 Example — Array Destructuring

```
const colors = ["red", "green", "blue"];

const [first, second, third] = colors;

console.log(first);  // red
console.log(second); // green
```

### 💻 Example — Object Destructuring

```
const user = {
  name: "Asif",
  age: 22
};

const { name, age } = user;

console.log(name); // Asif
console.log(age);  // 22
```

### 🔄 Counter question

Q: Can we give default values while destructuring?

Yes.

```
const { name, country = "Bangladesh" } = user;

console.log(country); // Bangladesh
```

Q: Can we rename a property while destructuring?

Yes.

```
const { name: userName } = user;

console.log(userName); // Asif
```

### Q17. What are the spread and rest operators?

### 🎤 How to answer

"Both spread and rest use the three-dot syntax ..., but they have different purposes. Spread expands or copies values, while rest collects multiple values into a single variable."

### 💻 Spread Example

```
const numbers = [1, 2, 3];

const newNumbers = [...numbers, 4, 5];

console.log(newNumbers);
// [1, 2, 3, 4, 5]

Object example:

const user = {
  name: "Asif",
  age: 22
};

const updatedUser = {
  ...user,
  city: "Dinajpur"
};
```

### 💻 Rest Example

```
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3, 4));
// 10
```

Here ...numbers collects all arguments into an array.

### 🔄 Counter question

Q: How do you know whether ... is spread or rest?

"It depends on where it is used. When it expands values, it's spread. When it collects multiple values into one variable, it's rest."

Q: Does spread create a deep copy?

"No. Spread creates a shallow copy."

### Q18. What is the difference between map(), filter(), and reduce()?

### 🎤 How to answer

"map() transforms every element and returns a new array. filter() selects elements based on a condition and returns a new array. reduce() processes all elements and combines them into a single result."

### 💻 Example

```
const numbers = [1, 2, 3, 4, 5];

const doubled = numbers.map(num => num * 2);

const even = numbers.filter(num => num % 2 === 0);

const sum = numbers.reduce((total, num) => total + num, 0);

console.log(doubled);
// [2, 4, 6, 8, 10]

console.log(even);
// [2, 4]

console.log(sum);
// 15
```

### 🔄 Counter question

Q: Does map() modify the original array?

"No. map() returns a new array."

Q: Can filter() return a single value?

"Normally, filter() always returns an array, even if there is only one matching element or no matching elements."

Q: When would you use reduce() instead of map()?

"When I need to transform each item, I use map(). When I need to combine the items into one result, such as a sum, object, or grouped data, I can use reduce()."

### Q19. What is the difference between for...in and for...of?

### 🎤 How to answer

"for...in is mainly used to iterate over the enumerable keys or property names of an object. for...of is used to iterate over the values of iterable objects such as arrays, strings, Maps, and Sets."

### 💻 Example

```
const user = {
  name: "Asif",
  age: 22
};

for (const key in user) {
  console.log(key);
}

Output:

name
age

With an array:

const numbers = [10, 20, 30];

for (const value of numbers) {
  console.log(value);
}

Output:

10
20
30
```

### 🔄 Counter question

Q: What happens if you use for...in on an array?

"It iterates over the array's enumerable keys, usually the indexes, rather than directly giving the values."

Q: Can for...of work with a normal object?

"Not by default, because a normal object is not iterable. We can use something like Object.entries() to iterate over its data."

### Q20. What are template literals and tagged templates?

### 🎤 How to answer

"Template literals are strings written using backticks. They allow us to easily insert variables using ${} and also support multiline strings."

### 💻 Example

```
const name = "Asif";
const age = 22;

const message = `My name is ${name} and I am ${age} years old.`;

console.log(message);

They also support multiline strings:

const text = `
Hello Asif,
Welcome to JavaScript.
`;
```

### 🔄 Counter question

Q: What are tagged templates?

"A tagged template allows a function to process a template literal before the final string is created."

```
function tag(strings, name) {
  console.log(strings);
  console.log(name);
}

const name = "Asif";

tag`Hello ${name}`;
```

Q: Where can tagged templates be useful?

"They can be useful for things like custom formatting, localization, sanitization, or building specialized template-processing functions."

### Q21. What is the event loop in JavaScript?

### 🎤 How to answer

"The event loop is a mechanism that allows JavaScript to handle asynchronous operations even though JavaScript runs code on a single main thread. It checks whether the call stack is empty and then moves eligible callbacks from queues into the call stack for execution."

### 💻 Example

```
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

console.log("End");

Output:

Start
End
Timeout
```

Even though the timeout is 0, its callback doesn't execute immediately. It waits until the current synchronous code finishes.

### 🔄 Counter question

Q: Which runs first: Promise callbacks or setTimeout() callbacks?

"Promise callbacks, such as .then(), are handled through the microtask queue, while setTimeout() callbacks are handled through the task or macrotask queue. After the current synchronous code finishes, microtasks are processed before the next task."

Example:

```
console.log("A");

setTimeout(() => console.log("B"), 0);

Promise.resolve().then(() => console.log("C"));

console.log("D");

Output:

A
D
C
B
```

Q: Is JavaScript completely single-threaded?

"The JavaScript execution model has a single main call stack, but the runtime environment, such as the browser or Node.js, can provide background capabilities for asynchronous operations."

### Q22. Explain how Promises work in JavaScript.

### 🎤 How to answer

"A Promise represents the eventual result of an asynchronous operation. It can be in three states: pending, fulfilled, or rejected. We can handle the result using .then() and errors using .catch()."

### 💻 Example

```
const promise = new Promise((resolve, reject) => {
  const success = true;

  if (success) {
    resolve("Operation successful");
  } else {
    reject("Operation failed");
  }
});

promise
  .then(result => {
    console.log(result);
  })
  .catch(error => {
    console.log(error);
  });
```

### 🔄 Counter question

Q: Can a Promise change from fulfilled back to pending?

"No. Once a Promise is fulfilled or rejected, its state is settled and cannot change again."

Q: What is the difference between .then() and .catch()?

".then() handles a successful result, while .catch() handles rejection or errors in the Promise chain."

Q: What does .finally() do?

"It runs after the Promise is settled, whether it was fulfilled or rejected. It's useful for cleanup."

### Q23. What is async/await and how does it improve upon Promises?

### 🎤 How to answer

"async/await is syntax built on top of Promises that makes asynchronous code easier to read and write. An async function always returns a Promise, and await pauses that function until the Promise settles."

### 💻 Example

```
async function getUser() {
  const response = await fetch("/api/user");

  const data = await response.json();

  console.log(data);
}

With error handling:

async function getUser() {
  try {
    const response = await fetch("/api/user");
    const data = await response.json();

    console.log(data);
  } catch (error) {
    console.log(error);
  }
}
```

### 🔄 Counter question

Q: Does await block the entire JavaScript thread?

"No. It pauses the execution of the current async function, but it does not block the entire JavaScript runtime."

Q: What does an async function return?

"An async function always returns a Promise."

```
async function test() {
  return 10;
}

console.log(test());
// Promise
```

### Q24. What is the difference between call(), apply(), and bind()?

### 🎤 How to answer

"call(), apply(), and bind() are used to control the value of this when calling a function. The main difference is how they pass arguments and when the function executes. call() takes arguments individually, apply() takes them as an array, and bind() returns a new function that can be called later."

### 💻 Example

```
const user = {
  name: "Asif"
};

function greet(age, city) {
  console.log(this.name, age, city);
}

greet.call(user, 22, "Dinajpur");

greet.apply(user, [22, "Dinajpur"]);

const boundGreet = greet.bind(user, 22, "Dinajpur");

boundGreet();
```

### 🔄 Counter question

Q: Does bind() immediately execute the function?

"No. bind() returns a new function. We need to call that function separately."

Q: What is the main difference between call() and apply()?

"The main difference is how arguments are passed. call() takes them individually, while apply() takes them as an array or array-like object."

### Q25. What is prototypal inheritance in JavaScript?

### 🎤 How to answer

"Prototypal inheritance is JavaScript's mechanism for allowing objects to inherit properties and methods from another object through the prototype chain."

### 💻 Example

```
const person = {
  greet() {
    console.log("Hello");
  }
};

const user = Object.create(person);

user.greet();
```

Here user doesn't directly contain greet(). JavaScript looks at its prototype and finds the method there.

The chain looks like:

```
user
  ↓
person
  ↓
Object.prototype
  ↓
null
```

### 🔄 Counter question

Q: What happens when JavaScript can't find a property on the object itself?

"It searches up the prototype chain until it finds the property or reaches null."

Q: Is JavaScript class-based or prototype-based?

"JavaScript is fundamentally prototype-based. The class syntax provides a more convenient syntax for working with prototypes."

### Q26. Explain the concept of the this keyword in different contexts.

### 🎤 How to answer

"this refers to a value determined mainly by how a function is called. Its value can be different depending on the execution context."

### 💻 Object method

```
const user = {
  name: "Asif",

  greet() {
    console.log(this.name);
  }
};

user.greet();
// Asif
```

Here this refers to user.

### 💻 Regular function

```
In strict mode:

"use strict";

function test() {
  console.log(this);
}

test();
// undefined
💻 Arrow function
const user = {
  name: "Asif",

  greet: () => {
    console.log(this.name);
  }
};
```

Arrow functions don't create their own this; they inherit it from their surrounding lexical scope.

### 🔄 Counter question

Q: Does this refer to the function itself?

"No. this usually refers to the context determined by how the function is called. It is not simply a reference to the function."

Q: How can you explicitly control this?

"We can use call(), apply(), or bind() for regular functions."

### Q27. What are JavaScript modules?

### 🎤 How to answer

"JavaScript modules allow us to split code into separate files and share functionality between them using export and import. This makes applications easier to organize and maintain."

### 💻 Example

```
math.js

export function add(a, b) {
  return a + b;
}

app.js

import { add } from "./math.js";

console.log(add(2, 3));
💻 Default export
export default function greet() {
  console.log("Hello");
}

Then:

import greet from "./greet.js";
```

### 🔄 Counter question

Q: What is the difference between named export and default export?

"Named exports can have multiple exports from a module and are imported using their exported names. A module can have one default export, and the importing code can choose its local name."

Q: Are ES modules automatically strict mode?

"Yes. JavaScript modules are always executed in strict mode."

### Q28. What is the difference between shallow copy and deep copy?

### 🎤 How to answer

"A shallow copy copies the top-level properties, but nested objects or arrays are still shared by reference. A deep copy creates an independent copy of nested data as well."

### 💻 Shallow copy

```
const user = {
  name: "Asif",
  address: {
    city: "Dinajpur"
  }
};

const copy = { ...user };

copy.address.city = "Dhaka";

console.log(user.address.city);
// Dhaka

The nested address object is still shared.

💻 Deep copy

A modern approach:

const copy = structuredClone(user);

copy.address.city = "Dhaka";

console.log(user.address.city);
// Dinajpur
```

### 🔄 Counter question

Q: Is { ...object } a deep copy?

"No. Object spread creates only a shallow copy."

Q: Is JSON.parse(JSON.stringify(object)) a reliable deep-copy solution for every object?

"No. It can lose or change certain values such as undefined, functions, Date, Map, Set, and some other types. structuredClone() is generally more appropriate when its supported data types meet the requirement."

### Q29. What are WeakMap and WeakSet?

### 🎤 How to answer

"WeakMap and WeakSet are special collections that hold weak references to objects. They allow objects to be garbage-collected when there are no other strong references to them. They are useful when we want to associate temporary metadata with objects without preventing garbage collection."

### 💻 WeakMap Example

```
const weakMap = new WeakMap();

let user = {
  name: "Asif"
};

weakMap.set(user, {
  loginTime: Date.now()
});

console.log(weakMap.get(user));
```

If the object becomes unreachable:

user = null;

The object can eventually be garbage-collected, and the WeakMap does not keep it alive.

### 🔄 Counter question

Q: Can we use primitive values as WeakMap keys?

"No. WeakMap keys must be objects or non-registered symbols."

Q: Why can't we normally iterate over a WeakMap?

"Because its keys are weakly held and may disappear through garbage collection. JavaScript therefore doesn't provide normal enumeration methods like keys() or entries() for WeakMap."

Q: What's one practical use of WeakMap?

"Associating private or temporary metadata with objects without preventing those objects from being garbage-collected."

### Q30. Explain memoization with an example.

### 🎤 How to answer

"Memoization is an optimization technique where we store the result of an expensive function call. If the function is called again with the same input, we return the cached result instead of calculating it again."

### 💻 Example

```
function memoize(fn) {
  const cache = new Map();

  return function (n) {
    if (cache.has(n)) {
      return cache.get(n);
    }

    const result = fn(n);

    cache.set(n, result);

    return result;
  };
}

function square(n) {
  console.log("Calculating...");
  return n * n;
}

const memoizedSquare = memoize(square);

console.log(memoizedSquare(5));
// Calculating...
// 25

console.log(memoizedSquare(5));
// 25
```

The second time, the cached result is returned.

### 🔄 Counter question

Q: When is memoization useful?

"It's useful when a function is expensive to execute and is called repeatedly with the same inputs."

Q: Is memoization always beneficial?

"No. Memoization uses extra memory for the cache, so if the function is cheap or the inputs rarely repeat, the memory overhead may not be worth it."

Q: What type of functions are good candidates for memoization?

"Pure functions are good candidates because the same input should consistently produce the same output."
