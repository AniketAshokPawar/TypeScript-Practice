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

---

# TypeScript Primitive Data Types - Interview Questions

---

## Q1. What are primitive data types in TypeScript?

### Answer:

Primitive data types are the basic built-in data types used to store simple values.

Common primitive types:

- `number` → numeric values
- `string` → text values
- `boolean` → true/false values
- `null` → intentional empty value
- `undefined` → declared but not assigned value

---

### Interview Answer (Short)

> "Primitive data types are basic data types in TypeScript used to store simple values like numbers, strings, booleans, null, and undefined."

---

# Q2. What is the difference between `null` and `undefined`?

### Answer:

| null | undefined |
|---|---|
| Intentional empty value | Variable declared but value not assigned |
| Assigned manually | Usually assigned automatically |

Example:

```typescript
let data: null = null;

let value: undefined;
```

---

### Interview Answer (Short)

> "`null` represents an intentionally empty value, while `undefined` means a variable has been declared but no value has been assigned."

---

# Q3. What is `any` type in TypeScript?

### Answer:

`any` allows a variable to store any type of value.

Example:

```typescript
let data: any = 10;

data = "Playwright";

data = true;
```

All assignments are allowed.

---

### Interview Answer (Short)

> "`any` disables type checking and allows storing any data type. It provides flexibility but reduces Type Safety."

---

# Q4. Why should we avoid using `any`?

### Answer:

Because:

- It removes TypeScript's main advantage (Type Safety).
- Errors are not caught during development.
- It can create runtime issues.

Example:

```typescript
let timeout: any = 5000;

timeout = "Five seconds";
```

TypeScript will not complain.

---

### Interview Answer (Short)

> "I avoid `any` because it disables type checking. Instead, I prefer specific types or Union types to maintain Type Safety."

---

# Q5. What is a Union Type? Why do we use it?

### Answer:

Union Type allows a variable to store multiple specific types.

Syntax:

```typescript
|
```

Example:

```typescript
let employeeId: string | number;

employeeId = 101;

employeeId = "EMP101";
```

---

### Why use Union instead of any?

Because Union provides flexibility while maintaining Type Safety.

---

### Interview Answer (Short)

> "Union types allow multiple specific data types for a variable. They are safer than `any` because TypeScript still performs type checking."

---

# Q6. Difference between `any` and Union Type?

### Answer:

| any | Union |
|---|---|
| Allows any data type | Allows only defined types |
| No type checking | Type checking available |
| Less safe | More safe |

Example:

```typescript
let value: any;

value = 10;
value = "Hello";
value = true;
```

Allowed.

---

```typescript
let id: string | number;

id = 10;
id = "EMP101";

// id = true ❌
```

Not allowed.

---

### Interview Answer (Short)

> "`any` removes type checking, while Union allows only specific types, so Union is preferred when possible."

---

# Q7. What is Type Inference in TypeScript?

### Answer:

Type Inference means TypeScript automatically identifies the variable type based on the assigned value.

Example:

```typescript
let age = 25;
let name = "Aniket";
let status = true;
```

TypeScript automatically understands:

```text
age → number
name → string
status → boolean
```

---

### Interview Answer (Short)

> "Type Inference is TypeScript's ability to automatically determine variable types without explicitly writing the type."

---

# Q8. Where do you use primitive data types in a Playwright framework?

### Answer:

Examples:

```typescript
const url: string = "https://application.com";

let retryCount: number = 0;

let isLoggedIn: boolean = true;
```

Usage:

- `string` → URLs, usernames, locators
- `number` → timeout values, counters
- `boolean` → flags and conditions

---

### Interview Answer (Short)

> "In Playwright, I use strings for URLs and test data, numbers for timeouts and counters, and booleans for conditions or execution flags."

