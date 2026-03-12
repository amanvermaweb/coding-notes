# Functions in TypeScript

## Function Basics
Functions in TypeScript work like JavaScript functions but with **type safety**.  
You can specify the **types of parameters** and the **return type**.

```ts
function greet(name: string): string {
  return `Hello, ${name}`;
}

greet("Aman"); // OK
greet(10); // Error
```

Syntax breakdown:

```
function functionName(parameter: type): returnType {
  // code
}
```

---

## Function Parameters

### Typed Parameters
Each parameter should have a defined type.

```ts
function add(a: number, b: number): number {
  return a + b;
}
```

---

### Optional Parameters
Use `?` to make parameters optional.

```ts
function greet(name: string, age?: number) {
  if (age) {
    return `Hello ${name}, age ${age}`;
  }
  return `Hello ${name}`;
}

greet("Aman");
greet("Aman", 16);
```

Rules:
- Optional parameters must come **after required parameters**.

---

### Default Parameters
You can set default values.

```ts
function greet(name: string, greeting: string = "Hello") {
  return `${greeting}, ${name}`;
}

greet("Aman");
greet("Aman", "Hi");
```

---

### Rest Parameters
Allows passing multiple arguments.

```ts
function sum(...numbers: number[]): number {
  return numbers.reduce((total, num) => total + num, 0);
}

sum(1, 2, 3, 4);
```

---

## Function Return Types

TypeScript can **infer return types**, but explicitly defining them is recommended.

```ts
function multiply(a: number, b: number): number {
  return a * b;
}
```

---

### Void Return Type
Used when a function does not return anything.

```ts
function logMessage(message: string): void {
  console.log(message);
}
```

---

## Arrow Functions

Arrow functions work the same but with modern syntax.

```ts
const add = (a: number, b: number): number => {
  return a + b;
};
```

Short version:

```ts
const add = (a: number, b: number): number => a + b;
```

---

## Function Type

You can define a variable with a function type.

```ts
let add: (a: number, b: number) => number;

add = (x, y) => x + y;
```

---

## Anonymous Functions

Functions without a name.

```ts
const greet = function(name: string): string {
  return `Hello ${name}`;
};
```

---

## Union Types in Functions

Parameters can accept multiple types.

```ts
function printId(id: number | string) {
  console.log("ID:", id);
}

printId(101);
printId("A101");
```

---

## Function Overloads

TypeScript allows defining multiple function signatures.

```ts
function combine(a: number, b: number): number;
function combine(a: string, b: string): string;

function combine(a: any, b: any) {
  return a + b;
}

combine(1, 2);
combine("Hello ", "World");
```

---

## Callback Functions

Functions passed as arguments.

```ts
function processUserInput(callback: (name: string) => void) {
  const name = "Aman";
  callback(name);
}

processUserInput((name) => {
  console.log("Hello", name);
});
```

---

## Best Practices

1. Always define **parameter types**.
2. Prefer **explicit return types** in large projects.
3. Use **arrow functions** for short functions.
4. Use **function types** when passing functions around.
5. Avoid `any` unless absolutely necessary.