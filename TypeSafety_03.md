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

---

# Type Safety in TypeScript - Interview Questions

## Q1. What is Type Safety in TypeScript?

### Answer

Type Safety means a variable can store only the type of value it is declared for.

TypeScript checks data types during development and prevents invalid assignments.

Example:

```typescript
let age: number = 25;

// age = "Twenty Five"; ❌ Error
```

---

### Interview Answer (Short)

> "Type Safety means variables can store only their declared data type. TypeScript checks this during development, helping catch errors before execution."

---

## Q2. Why is Type Safety important?

### Answer

Type Safety helps to:

- Catch errors early.
- Reduce debugging time.
- Improve code quality.
- Make automation frameworks easier to maintain.

---

### Interview Answer (Short)

> "Type Safety catches type-related mistakes before execution, reducing runtime errors and making automation code more reliable."

---

## Q3. How does TypeScript provide Type Safety?

### Answer

TypeScript uses **static typing**.

When a variable is declared with a type, TypeScript ensures only values of that type can be assigned.

Example:

```typescript
let browser: string = "Chromium";

// browser = 100; ❌ Error
```

---

### Interview Answer (Short)

> "TypeScript provides Type Safety through static typing by checking variable types during compilation."

---

## Q4. How is Type Safety different in JavaScript and TypeScript?

### Answer

| JavaScript | TypeScript |
|------------|------------|
| Dynamically typed | Statically typed |
| Type checked at runtime | Type checked during development |
| Variable types can change | Variable types are enforced |

Example:

**JavaScript**

```javascript
let age = 25;

age = "Twenty Five";   // ✅ Allowed
```

**TypeScript**

```typescript
let age: number = 25;

// age = "Twenty Five"; ❌ Error
```

---

### Interview Answer (Short)

> "JavaScript allows variables to change their type at runtime, whereas TypeScript enforces the declared type and reports errors during development."

---

## Q5. How does Type Safety help in a Playwright automation framework?

### Answer

Type Safety helps by:

- Catching incorrect data types while writing tests.
- Preventing invalid function arguments.
- Reducing runtime failures.
- Making large automation frameworks easier to maintain.

Example:

```typescript
async function launchBrowser(browser: string) {

}

launchBrowser("Chromium");   // ✅

// launchBrowser(10);        ❌ Error
```

---

### Interview Answer (Short)

> "In Playwright, Type Safety helps catch mistakes while writing automation scripts, reducing debugging time and improving framework maintainability."

---

## Q6. Does Type Safety remove all runtime errors?

### Answer

No.

Type Safety only catches **type-related errors**.

Runtime issues such as:

- Incorrect locators
- Network failures
- API failures
- Application bugs

can still occur while the automation test is running.

---

### Interview Answer (Short)

> "No. Type Safety only prevents type-related mistakes. Runtime issues like locator failures or application bugs can still occur."

---

## Q7. Can TypeScript code run directly in the browser?

### Answer

No.

Browsers understand only JavaScript.

TypeScript must first be **compiled into JavaScript**, and then the JavaScript code is executed.

---

### Interview Answer (Short)

> "No. TypeScript cannot run directly. It is compiled into JavaScript, which is then executed by the browser or Node.js."








