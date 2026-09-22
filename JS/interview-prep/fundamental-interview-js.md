### Q1. What is the difference between var, let, and const in JavaScript?

### 🎤 How to answer

"var, let, and const are used to declare variables in JavaScript. The main differences are in scope, redeclaration, and reassignment. var is function-scoped, while let and const are block-scoped. let can be reassigned, but const cannot be reassigned. Generally, I prefer const by default and use let when the value needs to change."

### Q2. Explain the concept of hoisting in JavaScript.

### 🎤 How to answer

"Hoisting is JavaScript's behavior where declarations are processed before the code is executed. Because of this, some variables and functions can be accessed before their declaration appears in the code. Function declarations are fully hoisted, while var is hoisted and initialized with undefined. let and const are also hoisted internally, but they cannot be accessed before initialization because of the Temporal Dead Zone."

### Q3. What are the primitive data types in JavaScript?

### 🎤 How to answer

"JavaScript has seven primitive data types: string, number, bigint, boolean, undefined, symbol, and null. Primitive values are immutable and are not objects."

### Q4. What is the difference between == and ===?

### 🎤 How to answer

"== is loose equality. It can perform type conversion before comparing values. === is strict equality, so it compares both value and type without implicit type conversion. In most cases, I prefer === because it gives more predictable results."
