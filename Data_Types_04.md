# TypeScript Primitive Data Types

Primitive data types are the basic built-in data types in TypeScript.

---

# 1. Number

Used to store numeric values.

## Example

```ts
let age: number = 25;

let salary: number = 50000;

console.log(age);
console.log(salary);
```

---

# 2. String

Used to store text values.

## Example

```ts
let testerName: string = "Aniket";

let company: string = "Google";

console.log(testerName);
console.log(company);
```

---

# 3. Boolean

Used to store `true` or `false` values.

## Example

```ts
let isSelected: boolean = true;

let isAutomationTester: boolean = false;

console.log(isSelected);
console.log(isAutomationTester);
```

---

# 4. Null

Represents an intentional empty value.

## Example

```ts
let data: null = null;

console.log(data);
```

---

# 5. Undefined

Represents a variable that has been declared but not assigned a value.

## Example

```ts
let value: undefined = undefined;

console.log(value);
```

---

# 6. Any

`any` allows storing any type of value.

## Example

```ts
let data: any = 25;

console.log(data);

data = "Aniket";

console.log(data);

data = true;

console.log(data);
```

---

# Important Point About any

- Type checking is disabled for `any`
- Can store multiple data types
- Should be avoided when possible
- Reduces Type Safety

---

# 7. Union Type

Union allows multiple data types for a variable.

Uses `|` operator.

## Example

```ts
let id: string | number;

id = 101;

console.log(id);

id = "EMP101";

console.log(id);
```

---

# Why Union Type is Useful?

Union types provide flexibility while still maintaining type safety.

---

# Interview Points

| Data Type | Purpose |
|---|---|
| number | Stores numeric values |
| string | Stores text values |
| boolean | Stores true/false |
| null | Represents empty value |
| undefined | Variable declared but not assigned |
| any | Accepts any data type |
| union | Allows multiple specific data types |

---

# Important Notes

- TypeScript is a statically typed language.
- Primitive data types improve Type Safety.
- `any` should be used carefully.
- Union types are preferred over `any` in many cases.
