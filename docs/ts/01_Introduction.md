# ![ ](../assets/typescript.svg) Introduction to TypeScript

## What is TypeScript

**TypeScript** is a statically typed superset of JavaScript developed by Microsoft. It adds **static typing**, **type checking**, and modern language features on top of JavaScript.

TypeScript code is compiled into regular JavaScript so it can run anywhere JavaScript runs (browsers, Node.js, etc).

Key idea:

```text
TypeScript → Compiled → JavaScript → Executed by browser / Node.js
```

Example:

```ts
let message: string = "Hello TypeScript";
console.log(message);
```

Compiled JavaScript:

```js
let message = "Hello TypeScript";
console.log(message);
```

## Why TypeScript Exists

JavaScript is dynamically typed, which means errors often appear **only at runtime**.

Example problem in JavaScript:

```js
function add(a, b) {
  return a + b;
}

add(5, "10");
```

Result:

```bash
"510"
```

No error, but incorrect logic.

TypeScript fixes this using **static typing**.

```ts
function add(a: number, b: number): number {
  return a + b;
}

add(5, 10); // correct
add(5, "10"); // error
```

Error is caught **during development**, not runtime.

## Key Features of TypeScript

### 1. Static Typing

You can define the type of variables.

```ts
let age: number = 16;
let username: string = "Aman";
let isStudent: boolean = true;
```

Benefits:

- Detect bugs early
- Better code reliability
- Easier collaboration

### 2. Type Inference

TypeScript can automatically detect types.

```ts
let count = 10;
```

TypeScript infers:

```bash
count: number
```

You don't always need to write types manually.

### 3. Interfaces

Interfaces define the **structure of objects**.

```ts
interface User {
  name: string;
  age: number;
}

const user: User = {
  name: "Aman",
  age: 16,
};
```

Benefits:

- Strong structure for data
- Easier large-scale development

### 4. Modern JavaScript Support

TypeScript supports the latest JavaScript features before browsers fully support them.

Examples:

- ES6 modules
- async/await
- decorators
- optional chaining

Example:

```ts
const user = {
  name: "Aman",
};

console.log(user?.name);
```

### 5. Better IDE Support

TypeScript greatly improves developer experience.

Features:

- Autocomplete
- Error highlighting
- Refactoring tools
- Intelligent suggestions

Editors like:

- Visual Studio Code
- WebStorm

work extremely well with TypeScript.

## TypeScript vs JavaScript

| Feature         | JavaScript           | TypeScript              |
| --------------- | -------------------- | ----------------------- |
| Typing          | Dynamic              | Static                  |
| Error Detection | Runtime              | Compile Time            |
| Scalability     | Harder in large apps | Designed for large apps |
| Tooling         | Basic                | Advanced                |
| Compilation     | Not required         | Required                |

Example comparison:

JavaScript:

```js
let price = 100;
price = "cheap";
```

TypeScript:

```ts
let price: number = 100;
price = "cheap"; // Error
```

## Installing TypeScript

Install globally using **npm**:

```bash
npm install -g typescript
```

Check installation:

```bash
tsc --version
```

## Your First TypeScript Program

Create a file:

```bash
app.ts
```

Code:

```ts
function greet(name: string): string {
  return "Hello " + name;
}

console.log(greet("Aman"));
```

Compile:

```bash
tsc app.ts
```

Generated file:

```bash
app.js
```

Run:

```bash
node app.js
```

## When TypeScript is Used

TypeScript is widely used in modern frameworks and large-scale applications.

Common examples:

- Angular (built with TypeScript)
- Next.js
- React
- NestJS

Most large production codebases now prefer TypeScript over plain JavaScript.

## When You Should Use TypeScript

TypeScript is ideal for:

- Large projects
- Team development
- Scalable applications
- Long-term codebases

Examples:

- SaaS products
- enterprise applications
- full-stack web apps
- complex frontend projects

For small scripts, plain JavaScript may be sufficient.

## Summary

TypeScript is JavaScript with types.

Main advantages:

- Static type checking
- Better tooling
- Improved maintainability
- Fewer runtime bugs
- Strong support for large applications

In modern web development, TypeScript has become the **standard for serious projects**.
