### 1. What is Type Annotation?

Type annotation is the explicit declaration of a variable, parameter, property, or return value's type. It tells TypeScript what type of value is expected.

```
Example:

let name: string = "Asif";
let age: number = 25;
let isAdmin: boolean = true;

এখানে:

: string
: number
: boolean
```

এগুলো হলো type annotations।

### 2. What is Type Inference?

Short Interview Answer

Type inference is TypeScript's ability to automatically determine the type of a value based on the code and context without requiring an explicit type annotation.

```
Example:

let name = "Asif";

আমরা লিখিনি:

let name: string = "Asif";

কিন্তু TypeScript automatically বুঝে:

name → string
```

### 3. What is the difference between Type Annotation and Type Inference?

Type annotation is when the developer explicitly specifies a type, while type inference is when TypeScript automatically determines the type from the assigned value or surrounding context.
