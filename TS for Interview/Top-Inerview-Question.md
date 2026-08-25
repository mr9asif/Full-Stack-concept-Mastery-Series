## 🚀 Top 70 TypeScript Interview Questions & Answers

### 🟢 Part 1: TypeScript Fundamentals

### 1. What is TypeScript?

Answer:

TypeScript is a programming language developed by Microsoft that is a superset of JavaScript. It adds a static type system and other developer features to JavaScript. TypeScript code is transpiled into JavaScript before execution.

### 2. Why do we use TypeScript?

Answer:

We use TypeScript to catch type-related errors during development, improve code readability, provide better IDE support, make refactoring safer, and improve maintainability in large applications.

### 3. What is the difference between TypeScript and JavaScript?

Answer:

JavaScript is dynamically typed and runs directly in JavaScript runtimes. TypeScript adds static type checking and must generally be transpiled into JavaScript before execution.

The key point is:

TypeScript improves development-time safety, while JavaScript is what normally executes at runtime.

### 4. What does it mean that TypeScript is a superset of JavaScript?

Answer:

It means valid JavaScript is generally valid TypeScript, while TypeScript adds additional syntax such as type annotations, interfaces, generics, and advanced type features.

// TypeScript-specific syntax
const age: number = 25; 5. Does TypeScript exist at runtime?

Answer:

Most TypeScript type information does not exist at runtime. Types, interfaces, and many other TypeScript-only constructs are removed when the code is converted to JavaScript.

This is called type erasure.

### 6. What is transpilation?

Answer:

Transpilation is the process of converting source code from one language or language version into another while preserving its behavior.

For TypeScript:

TypeScript → JavaScript

### 7. What does tsc do?

Answer:

tsc is the TypeScript compiler. It performs type checking and can emit JavaScript based on TypeScript files and compiler configuration.

### 8. Can TypeScript prevent all bugs?

Answer:

No. TypeScript mainly prevents many type-related mistakes during development. It cannot automatically prevent logical errors, network failures, database failures, or invalid external data.

## 🟢 Part 2: Type System Basics

### 9. What is type annotation?

Answer:

Type annotation means explicitly specifying a type.

const name: string = "Asif";

Here, string is the type annotation.

### 10. What is type inference?

Answer:

Type inference is TypeScript's ability to automatically determine a type from the value or surrounding context.

const age = 25;

TypeScript infers age as number.

### 11. Type annotation vs type inference?

Answer:

Type annotation is explicitly written by the developer, while type inference is automatically determined by TypeScript.

const name: string = "Asif"; // Annotation
const age = 25; // Inference 12. What is type widening?

Answer:

Type widening happens when TypeScript converts a specific literal type into a broader type when mutation or flexibility is expected.

let status = "success";

The type is generally string, not "success".

### 13. What is contextual typing?

Answer:

Contextual typing means TypeScript determines the type of an expression based on where or how it is used.

```
const numbers = [1, 2, 3];

numbers.map((value) => value \* 2);
```

TypeScript knows value is a number from the array context.

### 🟡 Part 3: Important Types

### 14. What is any?

Answer:

any disables most type checking for that value.

let value: any = 10;

value.foo.bar();
value();

TypeScript allows these operations, which can lead to runtime errors.

### 15. Why is any dangerous?

Answer:

Because it removes type safety and allows invalid operations to spread through the application without compiler errors.

It should generally be avoided unless there is a specific reason.

### 16. What is unknown?

Answer:

unknown represents a value whose type is not yet known. Unlike any, you must narrow or validate it before using it.

let value: unknown = "Hello";

if (typeof value === "string") {
console.log(value.toUpperCase());
}

### 17. any vs unknown?

Answer:

any allows you to perform almost any operation without checking.

unknown requires type narrowing before the value can be used safely.

unknown is the safer alternative to any when the type is genuinely unknown.

### 18. What is never?

Answer:

never represents a value that should never occur.

It is commonly used for:

Functions that never return
Exhaustive checking
Impossible states
function fail(message: string): never {
throw new Error(message);
}

### 19. never vs void?

Answer:

void means a function's return value is not intended to be used.

never means the function never successfully completes normally.

function log(): void {
console.log("Hello");
}

function fail(): never {
throw new Error();
}

### 20. null vs undefined?

Answer:

undefined usually means a value was not assigned or is missing.

null is typically an explicit value representing intentional absence.

### 🟡 Part 4: Object Types

### 21. What is an interface?

Answer:

An interface defines the structure or contract of an object.

```
interface User {
id: string;
name: string;
}
```

### 22. What is a type alias?

Answer:

A type alias gives a name to a type.

```
type User = {
id: string;
name: string;
};
```

Unlike interfaces, type aliases can also represent unions, primitives, tuples, and other type expressions.

### 23. type vs interface?

Answer:

Both can describe object shapes.

Use interface when defining object contracts that may be extended or declaration-merged.

Use type when you need unions, intersections, mapped types, conditional types, or more complex type expressions.

### 24. What is declaration merging?

Answer:

Declaration merging allows multiple declarations of the same interface name to combine into one interface.

```
interface User {
name: string;
}

interface User {
age: number;
}
```

The resulting interface contains both properties.

### 25. What are optional properties?

Answer:

Optional properties may or may not exist.

```
interface User {
name: string;
age?: number;
}
```

### 26. What is readonly?

Answer:

readonly prevents reassignment through that TypeScript type.

interface User {
readonly id: string;
}

It is primarily a compile-time restriction unless paired with runtime immutability.

### 27. What is structural typing?

Answer:

TypeScript uses structural typing, meaning compatibility is mainly determined by the structure of a value rather than its explicit name.

If two types have compatible structures, they can often be assigned to each other.

🟠 Part 5: Union, Intersection & Narrowing 28. What is a union type?

Answer:

A union allows a value to be one of several possible types.

let id: string | number;

id can be either string or number.

29. What is an intersection type?

Answer:

An intersection combines multiple types into one.

type User = {
name: string;
};

type Admin = {
permissions: string[];
};

type AdminUser = User & Admin; 30. Union vs intersection?

Answer:

A union represents one of several possible types:

A | B

An intersection combines requirements from multiple types:

A & B 31. What is type narrowing?

Answer:

Type narrowing is the process where TypeScript reduces a broader type to a more specific type based on runtime checks and control flow.

function print(value: string | number) {
if (typeof value === "string") {
console.log(value.toUpperCase());
}
} 32. What are type guards?

Answer:

Type guards are runtime checks that help TypeScript narrow a value's type.

Common examples:

typeof
instanceof
in
Equality checks
Custom type guards 33. What is a custom type guard?

Answer:

A custom type guard is a function that returns a type predicate.

function isString(value: unknown): value is string {
return typeof value === "string";
}

After calling it, TypeScript can safely treat the value as a string.

34. What is a discriminated union?

Answer:

A discriminated union is a union where each member has a common property with a unique literal value.

type Success = {
status: "success";
data: string;
};

type ErrorResponse = {
status: "error";
message: string;
};

type Response = Success | ErrorResponse;

Checking status allows TypeScript to narrow the type safely.

35. How is never used for exhaustive checking?

Answer:

never can ensure all members of a union are handled.

function handleStatus(status: "loading" | "success" | "error") {
switch (status) {
case "loading":
break;
case "success":
break;
case "error":
break;
default: {
const exhaustive: never = status;
return exhaustive;
}
}
}

If a new union member is added and not handled, TypeScript can report an error.

🔵 Part 6: Generics 36. What are generics?

Answer:

Generics allow us to write reusable, type-safe code while preserving the relationship between input and output types.

function identity<T>(value: T): T {
return value;
} 37. Generics vs any?

Answer:

any removes type information.

Generics preserve type information.

function identity<T>(value: T): T {
return value;
}

If you pass a string, TypeScript knows the result is a string. With any, that information is lost.

38. What are generic constraints?

Answer:

Generic constraints restrict which types can be used.

function getLength<T extends { length: number }>(value: T) {
return value.length;
}

Only values with a length property are allowed.

39. What does keyof do?

Answer:

keyof produces a union of the property keys of a type.

type User = {
id: string;
name: string;
};

type UserKeys = keyof User;

Result:

"id" | "name" 40. What does K extends keyof T mean?

Answer:

It means K must be a valid property key of T.

function getProperty<T, K extends keyof T>(
obj: T,
key: K
) {
return obj[key];
}

This creates a type-safe property accessor.

41. What is T[K]?

Answer:

T[K] is an indexed access type that gets the type of property K from type T.

type User = {
name: string;
};

type Name = User["name"];

Name is string.

🔵 Part 7: Advanced Type System 42. What is a utility type?

Answer:

Utility types are built-in TypeScript types that transform or derive existing types.

Examples:

Partial<T>
Pick<T, K>
Omit<T, K>
Required<T>
Readonly<T>
Record<K, T> 43. What does Partial<T> do?

Answer:

It makes all properties optional.

interface User {
name: string;
email: string;
}

type UpdateUser = Partial<User>;

Useful for update operations.

44. What is Pick<T, K>?

Answer:

It creates a new type containing only selected properties.

type UserPreview = Pick<User, "name" | "email">; 45. What is Omit<T, K>?

Answer:

It creates a new type by removing selected properties.

type PublicUser = Omit<User, "password">; 46. What is Record<K, T>?

Answer:

It creates an object type with specified keys and value types.

type Roles = Record<string, boolean>; 47. What is a mapped type?

Answer:

A mapped type creates a new type by iterating over the keys of another type.

type Optional<T> = {
[K in keyof T]?: T[K];
};

This is conceptually similar to how Partial<T> works.

48. What is a conditional type?

Answer:

A conditional type chooses one type or another based on a type relationship.

type IsString<T> = T extends string
? true
: false; 49. What is infer?

Answer:

infer allows TypeScript to capture and infer a type inside a conditional type.

Example:

type MyReturnType<T> =
T extends (...args: any[]) => infer R
? R
: never;

Here, R is inferred as the function's return type.

50. What is a distributive conditional type?

Answer:

When a conditional type operates on a naked type parameter that is a union, TypeScript applies the conditional type to each union member separately.

type ToArray<T> = T extends unknown ? T[] : never;

type Result = ToArray<string | number>;

Result:

string[] | number[]
🟣 Part 8: Modern TypeScript 51. What does as const do?

Answer:

as const preserves literal types and applies readonly behavior to object properties and tuple-like array elements.

const roles = ["admin", "user"] as const;

The type becomes approximately:

readonly ["admin", "user"] 52. What is satisfies?

Answer:

satisfies checks that a value conforms to a type while generally preserving the value's more specific inferred type.

type Config = {
port: number;
};

const config = {
port: 3000,
} satisfies Config;

It is useful when you want validation against a contract without simply replacing inference with the broader annotated type.

53. Type assertion vs type annotation?

Answer:

A type annotation declares the expected type.

const age: number = 25;

A type assertion tells TypeScript to treat a value as a particular type.

const value = something as User;

Assertions do not perform runtime conversion or validation.

54. What is the non-null assertion operator (!)?

Answer:

It tells TypeScript to treat a value as not null or undefined.

const element = document.getElementById("app")!;

It should be used carefully because it does not add a runtime check.

🔴 Part 9: Compiler & Modules 55. What is tsconfig.json?

Answer:

tsconfig.json is the configuration file for the TypeScript compiler. It defines compiler behavior such as strictness, target JavaScript version, module system, included files, and output options.

56. What does strict do?

Answer:

strict enables a family of stricter type-checking options that improve type safety. It includes important checks such as strict null checking and implicit any checking, subject to TypeScript's configuration behavior.

57. What is strictNullChecks?

Answer:

It makes null and undefined distinct types that cannot be assigned to other types unless explicitly allowed.

let name: string = null; // Error 58. What is noImplicitAny?

Answer:

It reports errors when TypeScript would otherwise implicitly assign any to something.

function greet(name) {
// Error with noImplicitAny
} 59. What is the difference between ESM and CommonJS?

Answer:

ESM uses:

import
export

CommonJS traditionally uses:

require()
module.exports

ESM is the modern standardized JavaScript module system.

60. What is import type?

Answer:

import type explicitly imports something only for type checking.

import type { User } from "./types";

It communicates that the import is type-only and should not be needed as a runtime value.

🔴 Part 10: Real-World TypeScript 61. Does TypeScript validate API data at runtime?

Answer:

No.

TypeScript only checks types during development and compilation. Data coming from an API, user input, environment variables, or other external sources should be validated at runtime.

Tools such as Zod can help perform runtime validation and derive TypeScript types.

62. Why is unknown useful for API or external data?

Answer:

Because external data should not automatically be trusted. unknown forces us to validate or narrow the data before using it.

function handleData(data: unknown) {
if (typeof data === "string") {
console.log(data.toUpperCase());
}
} 63. How do you type an API response?

Answer:

You can define a reusable generic response type.

type ApiResponse<T> = {
success: boolean;
message: string;
data: T;
};

Then:

type UserResponse = ApiResponse<User>; 64. How do you type Express request data?

Answer:

Express types can be parameterized for route parameters, response bodies, request bodies, and query values.

For example:

Request<Params, ResponseBody, RequestBody, Query>

The exact design depends on the application architecture and validation layer.

65. How should you handle errors in TypeScript?

Answer:

Treat unknown errors safely and narrow them before accessing properties.

try {
// code
} catch (error) {
if (error instanceof Error) {
console.log(error.message);
}
} 66. What is type-safe programming?

Answer:

Type-safe programming means using the type system to prevent invalid operations and represent valid relationships between data so mistakes can be caught before runtime where possible.

67. What is the difference between compile-time and runtime?

Answer:

Compile time is when TypeScript analyzes and checks the code.

Runtime is when the generated JavaScript actually executes in environments such as Node.js or a browser.

TypeScript
↓
Compile / Type Check
↓
JavaScript
↓
Runtime 68. What is type erasure?

Answer:

Type erasure means TypeScript-only type information is removed from the emitted JavaScript.

interface User {
name: string;
}

The interface does not normally exist as a runtime JavaScript value.

69. How do you avoid using too much any in a project?

Answer:

I prefer:

unknown for truly unknown values
Generics for reusable relationships
Union types for known alternatives
Type guards for narrowing
Proper interfaces or type aliases for data models
Runtime validation for external data 70. How would you explain TypeScript's biggest limitation?

Answer:

TypeScript provides compile-time type safety, but its type system does not automatically validate runtime data. Since types are generally erased, external input still needs runtime validation, and logical errors can still occur.
