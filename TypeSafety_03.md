# Type Safety in TypeScript

---

# What is Type Safety?

Type Safety means:

> Variables should store only the type of value they are declared for.

TypeScript checks data types during development and prevents invalid assignments.

This helps reduce runtime errors.

---

# Example in TypeScript

```ts
let testerName: string = "Aniket";

testerName = "Pawar";

console.log(testerName);
```

## Valid

Because:
- `testerName` is declared as `string`
- assigning another string is allowed

---

# Invalid Example in TypeScript

```ts
let age: number = 25;

age = "Twenty Five";
```

## Error

```text
Type 'string' is not assignable to type 'number'
```

TypeScript prevents assigning a string value to a number variable.

---

# Same Example in JavaScript

```js
let age = 25;

age = "Twenty Five";

console.log(age);
```

## Output

```text
Twenty Five
```

JavaScript allows changing data types dynamically.

This may create bugs in large applications.

---

# Comparison: JavaScript vs TypeScript

| JavaScript | TypeScript |
|---|---|
| Dynamically Typed | Statically Typed |
| Errors found at runtime | Errors found during development |
| Less strict | More strict |
| Type checking not available | Type checking available |
| Easier for small scripts | Better for large applications |

---

# Why Type Safety is Important?

## Advantages

- Detects errors early
- Improves code quality
- Easier debugging
- Better readability
- Reduces runtime failures
- Helpful in automation frameworks like Playwright

---

# Example in Playwright Context

```ts
let browserName: string = "Chromium";

browserName = "Firefox";

console.log(browserName);
```

## Invalid Example

```ts
let waitTime: number = 5000;

waitTime = "Five Seconds";
```

## Error

```text
Type 'string' is not assignable to type 'number'
```

---

# Interview Points

- TypeScript provides type safety.
- Type safety prevents invalid data assignments.
- Errors are detected during development instead of runtime.
- Type safety improves maintainability of automation scripts.

---

# Important Note

TypeScript code finally converts into JavaScript.

Type checking exists only during development/compilation.










