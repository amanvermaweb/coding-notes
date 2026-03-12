# ![ ](../assets/typescript.svg) Basic Types in TypeScript

## Number

Represents both integer and floating point numbers.

```ts
let age: number = 16;
let price: number = 99.99;
let hex: number = 0xf00d;
```

JavaScript has only one number type, so TypeScript uses `number` for all numeric values.

## String

Represents textual data.

```ts
let username: string = "Aman";
let greeting: string = `Hello ${username}`;
```

Supports single quotes, double quotes, and template literals.

## Boolean

Represents `true` or `false`.

```ts
let isLoggedIn: boolean = true;
let isAdmin: boolean = false;
```

Commonly used for conditions and flags.

## Array

Represents a collection of values of the same type.

Two ways to define arrays.

### Method 1: Using `type[]`

```ts
let numbers: number[] = [1, 2, 3, 4];
let names: string[] = ["Aman", "Rahul", "Priya"];
```

### Method 2: Using Generic Syntax

```ts
let numbers: Array<number> = [1, 2, 3];
let names: Array<string> = ["Aman", "Rahul"];
```

Both are equivalent. The `type[]` syntax is used more often.

## Tuple

Tuple is a fixed-length array where each position has a specific type.

```ts
let user: [string, number];

user = ["Aman", 16];
```

Example with multiple types:

```ts
let rgb: [number, number, number] = [255, 0, 0];
```

Useful when structure and order matter.

## Enum

Enums allow defining a set of named constants.

```ts
enum Direction {
  Up,
  Down,
  Left,
  Right,
}

let move: Direction = Direction.Up;
```

Custom values:

```ts
enum Status {
  Success = 200,
  NotFound = 404,
  ServerError = 500,
}
```

## Any

`any` disables type checking.

```ts
let value: any = 5;
value = "hello";
value = true;
```

Avoid using `any` whenever possible because it removes TypeScript’s safety.

## Unknown

Safer alternative to `any`. You must check the type before using it.

```ts
let value: unknown = "hello";

if (typeof value === "string") {
  console.log(value.toUpperCase());
}
```

## Void

Represents the absence of a value, usually used for functions.

```ts
function logMessage(): void {
  console.log("Hello");
}
```

## Null and Undefined

Represent absence of a value.

```ts
let data: null = null;
let value: undefined = undefined;
```

Often used in union types:

```ts
let user: string | null = null;
```

## Never

Represents values that never occur.

Used for functions that never return.

```ts
function throwError(message: string): never {
  throw new Error(message);
}
```

Another example:

```ts
function infiniteLoop(): never {
  while (true) {}
}
```

## Object

Represents non-primitive values.

```ts
let user: object = {
  name: "Aman",
  age: 16,
};
```

Better approach is defining the exact structure:

```ts
let user: { name: string; age: number } = {
  name: "Aman",
  age: 16,
};
```
