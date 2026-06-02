# TypeScript Notes: Interface vs Class vs Modules

## Interface

### What is an Interface?

An **Interface is a blueprint (contract)** that defines what properties and methods an object/class must have.

✅ Interface tells **WHAT should exist**

❌ Interface does NOT contain actual implementation

```ts
interface Person {
    name: string;
    age: number;

    display(): void;
}
```

---

## Class

### What is a Class?

A **Class is a blueprint + implementation**.

It contains:
- Properties
- Methods
- Constructor
- Logic

```ts
class Person {
    name: string;
    age: number;

    constructor(name: string, age: number) {
        this.name = name;
        this.age = age;
    }

    display() {
        console.log(this.name);
    }
}
```

---

# Interface vs Class

| Feature | Interface | Class |
|----------|----------|----------|
| Contains Properties | ✅ Yes | ✅ Yes |
| Contains Method Declaration | ✅ Yes | ✅ Yes |
| Contains Method Body | ❌ No | ✅ Yes |
| Contains Constructor | ❌ No | ✅ Yes |
| Object Creation | ❌ No | ✅ Yes |
| Used as Contract | ✅ Yes | ❌ No |
| Stores Data | ❌ No | ✅ Yes |

---

## Easy Way to Remember

### Interface = Rules

Imagine a company says:

> Every employee must have Name, ID, and Work() method.

This is an Interface.

```ts
interface Employee {
    name: string;
    id: number;

    work(): void;
}
```

Only rules are defined.

---

### Class = Actual Employee

```ts
class Developer implements Employee {
    constructor(
        public name: string,
        public id: number
    ) {}

    work() {
        console.log("Writing code");
    }
}
```

Class follows the rules and provides implementation.

---

## Why Interfaces are Used?

- Standardize object structure
- Ensure consistency
- Reduce mistakes
- Useful in large projects

Example:

```ts
interface User {
    name: string;
    age: number;
}

let user: User = {
    name: "Aniket",
    age: 25
};
```

If a required property is missing:

```ts
let user: User = {
    name: "Aniket"
};
```

❌ Error because `age` is missing.

---

# Modules

## What is a Module?

A **Module is simply a file that exports code and another file imports it.**

Used to organize code into multiple files.

---

### Without Modules

Everything in one file:

```ts
function add() {}
function subtract() {}
function multiply() {}
```

Large projects become difficult to manage.

---

### With Modules

**math.ts**

```ts
export function add(a: number, b: number) {
    return a + b;
}
```

**test.ts**

```ts
import { add } from "./math";

console.log(add(10, 20));
```

---

## export

Makes code available to other files.

```ts
export function add() {}
```

```ts
export class Student {}
```

```ts
export const PI = 3.14;
```

---

## import

Brings code from another file.

```ts
import { add } from "./math";
```

```ts
import { Student } from "./student";
```

---

# Interview Quick Answers

### What is an Interface?

An Interface defines a contract or structure that a class or object must follow. It contains only declarations and no implementation.

---

### Difference Between Interface and Class?

An Interface contains only declarations, while a Class contains both declarations and implementation. Interface cannot create objects, but a Class can.

---

### What is a Module?

A Module is a TypeScript file that exports code and allows other files to import and reuse that code.

---

### Why are Modules Used?

Modules help organize code, improve reusability, and make large automation frameworks easier to maintain.

---

# Revision (1-Minute)

## Interface

- Blueprint / Contract
- Defines structure
- No implementation
- Used with `implements`
- Cannot create objects

## Class

- Blueprint + Implementation
- Can have constructor
- Can create objects
- Contains actual logic

## Module

- `export` → Share code
- `import` → Use code
- Organizes code into multiple files
- Commonly used in Playwright frameworks
