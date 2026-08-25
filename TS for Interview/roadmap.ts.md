# TypeScript Interview Preparation Roadmap

> Goal:
> Prepare for TypeScript interviews from beginner to advanced level.
>
> Focus:
>
> - Conceptual questions
> - Follow-up questions
> - Tricky questions
> - Coding questions
> - Real-world project questions
> - Advanced TypeScript questions

---

# PHASE 1 — TypeScript Fundamentals Interview Questions

## 1. Introduction to TypeScript

Questions:

- What is TypeScript?
- Why do we use TypeScript?
- What problems does TypeScript solve?
- What is the difference between TypeScript and JavaScript?
- Is TypeScript a programming language?
- Is TypeScript compiled or interpreted?
- What is transpilation?
- What is the TypeScript compiler?
- What does `tsc` do?
- Can browsers run TypeScript directly?
- Why can't browsers understand TypeScript?
- Does TypeScript exist at runtime?
- What is type erasure?
- Does TypeScript improve runtime performance?
- Can TypeScript prevent all bugs?

Important Concepts:

- Superset of JavaScript
- Static type checking
- Compile time
- Runtime
- Transpilation
- Type erasure
- JavaScript output

---

# PHASE 2 — Type System Fundamentals

## 2. Type Annotation vs Type Inference

Questions:

- What is type annotation?
- What is type inference?
- What is the difference between annotation and inference?
- How does TypeScript infer a type?
- When should you explicitly define a type?
- When should you rely on type inference?
- Can TypeScript infer function return types?
- What is contextual typing?
- What happens when inference cannot determine a type?

Important Concepts:

- Explicit types
- Inferred types
- Contextual typing
- Type widening
- Literal widening

---

## 3. TypeScript Basic Types

Questions:

- What are the basic types in TypeScript?
- What is the difference between `null` and `undefined`?
- What is `bigint`?
- What is `symbol`?
- What is the difference between primitive and reference types?

Important Concepts:

- string
- number
- boolean
- bigint
- symbol
- null
- undefined
- object

---

# PHASE 3 — Special Types

## 4. `any`

Questions:

- What is `any`?
- Why is `any` dangerous?
- How does `any` affect type safety?
- Does TypeScript perform type checking on `any`?
- When should you use `any`?
- What are alternatives to `any`?
- What is implicit `any`?
- How can you prevent implicit `any`?

Important Concepts:

- Type safety
- Escape hatch
- noImplicitAny
- Type propagation

---

## 5. `unknown`

Questions:

- What is `unknown`?
- What is the difference between `unknown` and `any`?
- Why is `unknown` safer?
- Can you access properties on `unknown`?
- Can you assign `unknown` to another type?
- How do you use an `unknown` value safely?

Important Concepts:

- Type narrowing
- Type guards
- Safe top type

---

## 6. `never`

Questions:

- What is `never`?
- What is the difference between `never` and `void`?
- When does a function return `never`?
- Why is `never` useful?
- How is `never` used for exhaustive checking?
- Why does TypeScript infer `never` in some situations?

Important Concepts:

- Impossible values
- Functions that never return
- Exhaustive checking
- Discriminated unions

---

## 7. `void`

Questions:

- What is `void`?
- What is the difference between `void` and `undefined`?
- When should you use `void`?
- Can a function returning `void` return a value?

Important Concepts:

- Function return types
- Callback behavior

---

# PHASE 4 — Object Types

## 8. Object Typing

Questions:

- How do you define an object type?
- What are optional properties?
- What are readonly properties?
- What is excess property checking?
- What happens when an object has extra properties?
- What is structural typing?

Important Concepts:

- Object types
- Optional properties
- readonly
- Excess property checking
- Structural compatibility

---

## 9. Index Signatures

Questions:

- What is an index signature?
- When should you use an index signature?
- What is the difference between an index signature and `Record`?
- What limitations do index signatures have?

Important Concepts:

- Dynamic keys
- `[key: string]`
- Record

---

# PHASE 5 — Type vs Interface

## 10. `type` vs `interface`

Very Important Interview Topic.

Questions:

- What is the difference between `type` and `interface`?
- When should you use `type`?
- When should you use `interface`?
- Can interfaces extend types?
- Can types create unions?
- Can interfaces create unions?
- What is declaration merging?
- Why do interfaces support declaration merging?
- Which one do you prefer in a real project and why?

Follow-up Questions:

- Can you extend an interface?
- Can you extend a type?
- Can a class implement both?
- Which is better for library development?

Important Concepts:

- Declaration merging
- Extension
- Intersection
- Union
- Object contracts

---

# PHASE 6 — Union & Intersection

## 11. Union Types

Questions:

- What is a union type?
- How does TypeScript handle union types?
- Why can't you access every property of a union?
- How do you narrow a union?

---

## 12. Intersection Types

Questions:

- What is an intersection type?
- What is the difference between union and intersection?
- What happens when properties conflict?

---

# PHASE 7 — Type Narrowing

## 13. Type Narrowing

Very Important.

Questions:

- What is type narrowing?
- Why do we need narrowing?
- What are the different ways to narrow a type?

Must Know:

- `typeof`
- `instanceof`
- `in`
- Equality narrowing
- Truthiness narrowing
- Discriminated unions
- Custom type guards
- Control flow analysis

---

## 14. Type Guards

Questions:

- What is a type guard?
- What is a custom type guard?
- What is a type predicate?
- What does `value is Type` mean?
- What is the difference between runtime checking and TypeScript narrowing?

---

## 15. Discriminated Unions

Questions:

- What is a discriminated union?
- What is a discriminant property?
- Why are discriminated unions useful?
- Where would you use them in real projects?

Real-world Examples:

- API response states
- Payment states
- Authentication states
- Async request states

---

## 16. Exhaustive Checking

Questions:

- What is exhaustive checking?
- How do you use `never` for exhaustive checking?
- Why is exhaustive checking useful?

---

# PHASE 8 — Generics

## 17. Generic Fundamentals

Extremely Important.

Questions:

- What are generics?
- Why do we need generics?
- Generics vs `any`?
- What problem do generics solve?
- What does `<T>` mean?
- How does generic inference work?
- When should you explicitly provide a generic type?

---

## 18. Generic Constraints

Questions:

- What are generic constraints?
- What does `T extends Something` mean?
- Why use constraints?
- How do you restrict a generic type?

---

## 19. `keyof` + Generics

Very Important.

Questions:

- What does `keyof` do?
- What does `K extends keyof T` mean?
- What is `T[K]`?
- How do you create a type-safe property accessor?

Concepts:

- Generic constraints
- Key relationships
- Indexed access types

---

## 20. Generic Interview Coding

Practice:

- Generic identity function
- Generic API response
- Generic pagination
- Generic repository
- Type-safe property getter
- Generic array function
- Generic constraints

---

# PHASE 9 — Type Operators

## 21. `keyof`

Questions:

- What does `keyof` do?
- What does `keyof typeof` do?
- How is `keyof` useful with generics?

---

## 22. `typeof`

Questions:

- What is the difference between JavaScript `typeof` and TypeScript `typeof`?
- How can you derive a type from a value?

---

## 23. Indexed Access Types

Questions:

- What is `T[K]`?
- How do indexed access types work?
- Why are they useful?

---

# PHASE 10 — Utility Types

## 24. Built-in Utility Types

Must Know:

- Partial
- Required
- Readonly
- Pick
- Omit
- Record
- Exclude
- Extract
- NonNullable
- Parameters
- ReturnType
- Awaited

For Each Utility Type:

- What does it do?
- How does it work?
- Real-world use case
- Can you implement it yourself?

---

## 25. Utility Type Coding Questions

Practice implementing:

- MyPartial
- MyRequired
- MyReadonly
- MyPick
- MyOmit
- MyExclude
- MyExtract
- MyReturnType

---

# PHASE 11 — Mapped Types

## 26. Mapped Types

Questions:

- What is a mapped type?
- How does `[K in keyof T]` work?
- How are utility types implemented using mapped types?
- What are mapping modifiers?

Concepts:

- `keyof`
- `[K in keyof T]`
- Optional modifier
- readonly modifier
- `-readonly`
- `-?`

---

## 27. Key Remapping

Questions:

- What is key remapping?
- What does `as` do inside mapped types?
- How can you rename or remove keys?

---

# PHASE 12 — Conditional Types

## 28. Conditional Types

Very Important for Advanced Interviews.

Questions:

- What is a conditional type?
- How does `T extends U ? X : Y` work?
- Is this runtime logic?
- What is distributive conditional type?

---

## 29. Distributive Conditional Types

Questions:

- What is distributive conditional type?
- Why does distribution happen?
- How do you prevent distribution?
- Why does `[T] extends [U]` behave differently?

---

# PHASE 13 — `infer`

## 30. `infer`

Advanced Topic.

Questions:

- What is `infer`?
- Where can you use `infer`?
- How does TypeScript infer a type inside a conditional type?

Practice:

- Custom ReturnType
- Extract Promise type
- Extract array element
- Extract function parameters

---

# PHASE 14 — Template Literal Types

## 31. Template Literal Types

Questions:

- What are template literal types?
- How do they work with unions?
- Where are they useful?

Concepts:

- String composition
- Dynamic event names
- Type-safe paths

---

# PHASE 15 — Modern TypeScript Features

## 32. `as const`

Questions:

- What does `as const` do?
- What is literal widening?
- What is readonly inference?
- Why is `as const` useful?

---

## 33. `satisfies`

Very Important Modern TypeScript Topic.

Questions:

- What is `satisfies`?
- What problem does it solve?
- Difference between:
  - Type annotation
  - Type assertion
  - `satisfies`
- How does `satisfies` preserve inferred types?

---

# PHASE 16 — Type Assertions

## 34. Type Assertions

Questions:

- What is type assertion?
- Does type assertion perform runtime conversion?
- What is the difference between assertion and validation?
- Why can type assertions be dangerous?

Concepts:

- `as`
- Double assertion
- `as unknown as`
- Non-null assertion `!`

---

# PHASE 17 — Classes & OOP

## 35. Classes

Questions:

- How does TypeScript support classes?
- What are access modifiers?
- Difference between `public`, `private`, and `protected`?
- What is an abstract class?
- What is `implements`?
- Difference between `extends` and `implements`?
- What are static members?

---

## 36. TypeScript `private` vs JavaScript `#private`

Questions:

- What is the difference between TypeScript private and JavaScript private fields?
- Which exists at runtime?

---

# PHASE 18 — Structural Typing & Assignability

## 37. Structural Typing

Very Important Concept.

Questions:

- What is structural typing?
- What is nominal typing?
- How does TypeScript determine compatibility?
- Why can two different types be compatible?

---

## 38. Type Compatibility

Questions:

- What is assignability?
- What is type compatibility?
- What is excess property checking?
- What is type widening?
- What is narrowing?

---

# PHASE 19 — `tsconfig.json`

## 39. Important Compiler Options

Questions:

- What is `tsconfig.json`?
- What does `strict` do?
- What is `strictNullChecks`?
- What is `noImplicitAny`?
- What is `noUncheckedIndexedAccess`?
- What is `exactOptionalPropertyTypes`?
- What is `target`?
- What is `module`?
- What is `moduleResolution`?
- What is `esModuleInterop`?
- What is `rootDir`?
- What is `outDir`?

---

# PHASE 20 — Modules

## 40. Modules

Questions:

- ESM vs CommonJS?
- `import` vs `require`?
- `export` vs `module.exports`?
- What is `import type`?
- What is `export type`?
- What is module resolution?
- What is NodeNext?
- What is bundler module resolution?

---

# PHASE 21 — Declaration Files

## 41. `.d.ts`

Questions:

- What is a declaration file?
- What is `.d.ts` used for?
- What are ambient declarations?
- What does `declare` mean?
- How do you type a JavaScript library?

---

## 42. Module Augmentation

Questions:

- What is module augmentation?
- Why would you use it?
- How do you extend third-party types?

Real-world Example:

- Extending Express Request
- Adding authenticated user

---

# PHASE 22 — Async TypeScript

## 43. Promise Typing

Questions:

- What is `Promise<T>`?
- What type does an async function return?
- What is `Awaited<T>`?
- How do you type `Promise.all()`?
- How do you type async API functions?

---

# PHASE 23 — Error Handling

## 44. Type-Safe Error Handling

Questions:

- Why is an error sometimes `unknown`?
- What is `useUnknownInCatchVariables`?
- How do you safely handle an unknown error?
- Why should you use `instanceof Error`?

---

# PHASE 24 — Backend TypeScript Interview

## 45. Express + TypeScript

Questions:

- How do you type Request?
- How do you type Response?
- How do you type route parameters?
- How do you type query parameters?
- How do you type request body?
- How do you type middleware?
- How do you attach a user to Express Request?
- How do you avoid repeating types?

---

## 46. DTO & API Types

Questions:

- What is a DTO?
- Why shouldn't you expose database models directly?
- How do you design API response types?
- How do you create generic API responses?
- How do you type pagination?

---

## 47. Runtime Validation

Very Important.

Questions:

- Does TypeScript validate runtime data?
- Why isn't TypeScript enough for API validation?
- What is the difference between compile-time and runtime validation?
- How does Zod work with TypeScript?
- What is `z.infer`?

---

# PHASE 25 — Prisma + TypeScript

## 48. Prisma Type Safety

Questions:

- How does Prisma provide type safety?
- What are generated types?
- What is `select`?
- What is `include`?
- How do you infer the result type of a Prisma query?
- Should you manually recreate Prisma types?

---

# PHASE 26 — React + TypeScript

## 49. React TypeScript Questions

Questions:

- How do you type props?
- How do you type children?
- How do you type useState?
- How do you type useRef?
- How do you type useReducer?
- How do you type events?
- What is the difference between `React.FC` and a normal function component?
- How do you create a generic React component?
- How do you type a custom hook?

---

# PHASE 27 — Real-World Type Design

## 50. Type Design Questions

Questions:

- How do you design types for a large project?
- Where should types live?
- How do you avoid duplicate types?
- When should you derive a type instead of manually creating one?
- How do you model API states?
- How do you make illegal states impossible?

---

## 51. Discriminated Union in Real Projects

Practice:

- Authentication state
- API response
- Payment status
- Order status
- Loading/error/success state

---

# PHASE 28 — Advanced Type-Level Programming

## 52. Advanced Concepts

Questions:

- What is type-level programming?
- What are mapped types?
- What are conditional types?
- What is `infer`?
- What are recursive types?
- What are recursive conditional types?
- What are template literal types?

---

# PHASE 29 — TypeScript Coding Interview Questions

## 53. Basic Coding

- Create a typed function
- Type an object
- Create optional properties
- Create readonly properties
- Create union types
- Create intersection types

---

## 54. Intermediate Coding

- Create a custom type guard
- Create a discriminated union
- Create an exhaustive switch
- Create a generic function
- Create a generic constraint
- Create a type-safe property getter

---

## 55. Advanced Coding

- Implement Partial
- Implement Pick
- Implement Omit
- Implement ReturnType
- Implement DeepReadonly
- Extract Promise value type
- Extract array element type
- Create a type-safe event emitter
- Create nested object paths

---

# PHASE 30 — TypeScript Project-Based Interview

## 56. Questions About Your Own Project

Be ready to explain:

- Why did you choose TypeScript?
- How did TypeScript help your project?
- How do you organize your types?
- How do you type API responses?
- How do you validate request data?
- How do you handle unknown data?
- How do you avoid `any`?
- Where did you use generics?
- Where did you use unions?
- Where did you use discriminated unions?
- Where did you use utility types?
- How do you handle API errors?
- How do Prisma types help you?
- How do you share types between frontend and backend?
- How do you prevent type duplication?

---

# PHASE 31 — Tricky TypeScript Interview Topics

## 57. Must Master Deeply

- `any` vs `unknown`
- `unknown` vs `never`
- `void` vs `undefined`
- `type` vs `interface`
- Union vs Intersection
- `extends` in generics vs classes
- `keyof`
- `typeof`
- `keyof typeof`
- `T[K]`
- `K extends keyof T`
- Generics vs any
- Structural typing
- Excess property checking
- Type narrowing
- Type guards
- Discriminated unions
- `never` exhaustive checking
- Mapped types
- Conditional types
- Distributive conditional types
- `infer`
- `as const`
- `satisfies`
- Type assertion vs runtime validation
- Compile time vs runtime
- Type erasure

---

# PHASE 32 — Mock Interview Preparation

## 58. Prepare Every Topic in This Format

For every important TypeScript concept:

### Level 1

- Define the concept.

### Level 2

- Explain why it exists.

### Level 3

- Explain how it works internally.

### Level 4

- Give a simple example.

### Level 5

- Give a real-world example.

### Level 6

- Compare it with similar concepts.

### Level 7

- Answer tricky follow-up questions.

---

# FINAL PRIORITY ORDER

## 🔥 MUST MASTER

1. TypeScript vs JavaScript
2. Compile Time vs Runtime
3. Type Annotation vs Type Inference
4. any vs unknown
5. void vs never
6. type vs interface
7. Union vs Intersection
8. Type Narrowing
9. Type Guards
10. Discriminated Unions
11. Generics
12. Generic Constraints
13. keyof
14. typeof
15. T[K]
16. K extends keyof T
17. Utility Types
18. Mapped Types
19. Conditional Types
20. infer
21. Structural Typing
22. Excess Property Checking
23. as const
24. satisfies
25. Type Assertions
26. tsconfig strict options
27. ESM vs CommonJS
28. Declaration Files
29. Module Augmentation
30. Runtime Validation
31. Express + TypeScript
32. API Type Design
33. Zod + TypeScript
34. Prisma + TypeScript
35. React + TypeScript
36. Real-World Type Architecture

---

# 🎯 INTERVIEW GOAL

For every topic, you must be able to:

- Explain what it is
- Explain why it exists
- Explain how it works
- Write a code example
- Compare it with similar concepts
- Give a real-world use case
- Answer follow-up questions
- Solve a small coding problem

The goal is not:

"I know TypeScript syntax."

The goal is:

"If an interviewer asks me any important TypeScript concept, I can explain it deeply, write code for it, compare it with related concepts, and show where I used it in a real project."
