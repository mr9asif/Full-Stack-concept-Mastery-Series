### Q1. What is the difference between var, let, and const in JavaScript?

### 🎤 How to answer

"var, let, and const are used to declare variables in JavaScript. The main differences are in scope, redeclaration, and reassignment. var is function-scoped, while let and const are block-scoped. let can be reassigned, but const cannot be reassigned. Generally, I prefer const by default and use let when the value needs to change."

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
