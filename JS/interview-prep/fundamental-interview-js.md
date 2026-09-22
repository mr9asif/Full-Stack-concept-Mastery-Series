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
