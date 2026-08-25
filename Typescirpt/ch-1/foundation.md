# Chapter 1 — TypeScript Fundamentals

> **লক্ষ্য:** TypeScript-এর Basic Types ও Type System-এর ভিত্তি শেখা।

---

# 1.1 Variable

TypeScript-এ Variable ঘোষণা করার জন্য `let`, `const`, `var` ব্যবহার করা হয়।

```ts
let name = "Asif";
const age = 21;
```

> **Best Practice:** সবসময় `const` ব্যবহার করো। পরিবর্তন দরকার হলে `let`।

---

# 1.2 Type Annotation

Variable-এর Type নিজে লিখে দেওয়াকে **Type Annotation** বলে।

```ts
let age: number = 20;
let name: string = "Asif";
let isAdmin: boolean = false;
```

Syntax

```ts
variableName: Type
```

---

# 1.3 Type Inference

Type না লিখলেও TypeScript নিজে Type বুঝে নেয়।

```ts
let age = 20;      // number
let name = "Asif"; // string
```

> **Best Practice:** TypeScript বুঝতে পারলে Annotation না দিলেও চলে।

---

# 1.4 Primitive Types

| Type | Example |
|------|---------|
| string | `"Hello"` |
| number | `100` |
| boolean | `true` |
| bigint | `100n` |
| symbol | `Symbol()` |

```ts
let name: string = "Asif";
let age: number = 21;
let active: boolean = true;
```

---

# 1.5 Array

একই Type-এর একাধিক Value রাখে।

```ts
let numbers: number[] = [1, 2, 3];

let names: string[] = ["A", "B"];
```

Generic Syntax

```ts
let numbers: Array<number> = [1, 2, 3];
```

---

# 1.6 Tuple

Fixed Length + Fixed Type Array।

```ts
let user: [string, number] = ["Asif", 21];
```

✔ Position অনুযায়ী Type ঠিক থাকে।

---

# 1.7 Object

```ts
let user: {
  name: string;
  age: number;
} = {
  name: "Asif",
  age: 21,
};
```

---

# 1.8 any

সব ধরনের Value রাখা যায়।

```ts
let value: any = 10;

value = "Hello";

value = true;
```

❌ Type Checking বন্ধ হয়ে যায়।

> **Best Practice:** যতটা সম্ভব Avoid করো।

---

# 1.9 unknown

সব Value রাখা যায়, কিন্তু ব্যবহার করার আগে Type Check করতে হবে।

```ts
let value: unknown = "Hello";

if (typeof value === "string") {
  console.log(value.toUpperCase());
}
```

✅ `any` এর Safe Version।

---

# 1.10 void

কোনো Value Return না করলে।

```ts
function greet(): void {
  console.log("Hello");
}
```

---

# 1.11 never

যে Function কখনো Return করে না।

```ts
function error(): never {
  throw new Error("Error");
}
```

---

# 1.12 null & undefined

```ts
let a: null = null;

let b: undefined = undefined;
```

Strict Mode-এ এদের আলাদা Type ধরা হয়।

---

# 1.13 Literal Types

একটি নির্দিষ্ট Value-ই Type।

```ts
let status: "success" = "success";
```

আর কিছু Assign করলে Error।

---

# 1.14 Type Widening

TypeScript Type বড় করে ফেলে।

```ts
let name = "Asif";
```

➡️ Type = `string`

না যে `"Asif"`।

---

# 1.15 Type Narrowing

Type ছোট করে নির্দিষ্ট করা।

```ts
let value: string | number = "Hello";

if (typeof value === "string") {
  console.log(value.toUpperCase());
}
```

`typeof` এর পরে Type = `string`

---

# 🔥 Best Practices

- `const` বেশি ব্যবহার করো
- `any` Avoid করো
- `unknown` Prefer করো
- TypeScript Inference পারলে Annotation লিখতে হবে না
- Strict Mode ব্যবহার করো

---

# 📝 Quick Revision

- Variable → `let`, `const`
- Type Annotation → নিজে Type লিখি
- Type Inference → TS নিজে Type বুঝে
- Primitive → `string`, `number`, `boolean`, `bigint`, `symbol`
- Array → `number[]`
- Tuple → Fixed Length + Fixed Type
- Object → Key + Type
- `any` → Type Checking Off
- `unknown` → Safe `any`
- `void` → কিছু Return করে না
- `never` → কখনো Return করে না
- `null`, `undefined` → আলাদা Type
- Literal Type → নির্দিষ্ট Value-ই Type
- Widening → Type বড় হয়
- Narrowing → Type ছোট/নির্দিষ্ট হয়

