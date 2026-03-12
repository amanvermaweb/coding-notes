# Variables and Type Annotations in TypeScript

## Declaring Variables

TypeScript supports the same variable declarations as JavaScript.

```ts
let age = 18
const name = "Aman"
var score = 90
```

### `let`
Used for variables whose value may change.

```ts
let count = 0
count = 5
```

### `const`
Used for variables whose value will not change.

```ts
const pi = 3.14159
```

### `var` (not recommended)

`var` has function scope instead of block scope and can cause unexpected bugs.

```ts
var x = 10
```

Modern TypeScript code should prefer `let` and `const`.

---

## Type Annotations

Type annotations explicitly define the type of a variable.

```ts
let age: number = 16
let username: string = "Aman"
let isLoggedIn: boolean = true
```

Syntax:

```ts
let variableName: type = value
```

Example:

```ts
let score: number = 95
```

---

## Type Inference

TypeScript automatically detects types when possible.

```ts
let message = "Hello"
```

TypeScript infers:

```
string
```

So this is equivalent to:

```ts
let message: string = "Hello"
```

---

## When to Use Type Annotations

Use explicit annotations when:

### 1. Declaring variables without initial value

```ts
let age: number
age = 16
```

Without annotation TypeScript would treat it as `any`.

---

### 2. Function parameters

```ts
function greet(name: string) {
  console.log("Hello " + name)
}
```

---

### 3. Complex data structures

```ts
let user: { name: string; age: number } = {
  name: "Aman",
  age: 16
}
```

---

## Type Annotation with Arrays

```ts
let numbers: number[] = [1, 2, 3, 4]
let names: string[] = ["Aman", "Rahul", "Aryan"]
```

Alternative syntax:

```ts
let numbers: Array<number> = [1, 2, 3]
```

---

## Type Annotation with Objects

```ts
let user: {
  name: string
  age: number
} = {
  name: "Aman",
  age: 16
}
```

---

## Reassigning Variables

TypeScript enforces type safety.

```ts
let age: number = 16

age = 18      // valid
age = "18"    // error
```

Error:

```
Type 'string' is not assignable to type 'number'
```

---

## Best Practices

### Prefer `const`

```ts
const API_URL: string = "https://api.example.com"
```

### Avoid unnecessary annotations

Bad:

```ts
let name: string = "Aman"
```

Better:

```ts
let name = "Aman"
```

Use annotations when TypeScript cannot infer correctly.

---

## Quick Example

```ts
const username: string = "Aman"
let age: number = 16
let isStudent: boolean = true

let hobbies: string[] = ["coding", "music"]

let user: { name: string; age: number } = {
  name: "Aman",
  age: 16
}
```
