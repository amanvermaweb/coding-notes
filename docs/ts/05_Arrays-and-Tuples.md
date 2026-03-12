# Arrays and Tuples in TypeScript

## Arrays

Arrays store multiple values of the **same type**.

### Syntax

```ts
let numbers: number[] = [1, 2, 3, 4]

let names: string[] = ["Aman", "Rahul", "Priya"]
```

Alternative syntax:

```ts
let numbers: Array<number> = [1, 2, 3]
```

### Accessing Elements

```ts
let nums: number[] = [10, 20, 30]

console.log(nums[0]) // 10
console.log(nums[2]) // 30
```

### Array Methods

TypeScript supports normal JavaScript array methods but enforces type safety.

```ts
let numbers: number[] = [1, 2, 3]

numbers.push(4)      // valid
numbers.push(5)

numbers.push("6")    // error
```

### Iterating Arrays

```ts
let fruits: string[] = ["apple", "banana", "mango"]

for (let fruit of fruits) {
  console.log(fruit)
}
```

### Readonly Arrays

Prevents modification.

```ts
let nums: readonly number[] = [1, 2, 3]

nums.push(4)   // error
nums[0] = 10   // error
```

Alternative:

```ts
let nums: ReadonlyArray<number> = [1, 2, 3]
```

---

# Tuples

Tuples are arrays with **fixed length and specific types at each position**.

Example: a user with id, name, and active status.

### Syntax

```ts
let user: [number, string, boolean] = [1, "Aman", true]
```

Index meaning:

| Index | Type | Meaning |
|-----|-----|-----|
| 0 | number | id |
| 1 | string | name |
| 2 | boolean | active |

### Accessing Tuple Elements

```ts
let user: [number, string] = [101, "Aman"]

console.log(user[0]) // 101
console.log(user[1]) // Aman
```

### Tuple with Optional Elements

```ts
let user: [number, string, boolean?]

user = [1, "Aman"]
user = [1, "Aman", true]
```

### Tuple with Rest Elements

```ts
let data: [number, ...string[]]

data = [1, "a", "b", "c"]
```

First element must be a number, remaining must be strings.

### Named Tuples (Readable)

```ts
let user: [id: number, name: string]

user = [1, "Aman"]
```

---

# Difference Between Arrays and Tuples

| Feature | Array | Tuple |
|---|---|---|
| Length | Variable | Fixed |
| Types | Same type | Different types allowed |
| Use case | List of similar items | Structured data |
| Example | `number[]` | `[number, string]` |

Example comparison:

```ts
let scores: number[] = [90, 85, 88]

let student: [number, string] = [1, "Aman"]
```

---

# Real World Examples

### Coordinates

```ts
let point: [number, number] = [10, 20]
```

### API Response

```ts
let response: [number, string] = [200, "Success"]
```

### RGB Color

```ts
let color: [number, number, number] = [255, 0, 0]
```