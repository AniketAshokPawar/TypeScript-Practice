# Arrow Functions in TypeScript

Arrow functions provide a shorter and cleaner way to write functions.

Introduced in ES6.

---

# Syntax

```ts
let functionName = (parameters): returnType => {

    // code
}
```

---

# Example 1 — Arrow Function with No Parameter

```ts
let greet = ():void => {

    console.log("Welcome to TypeScript");
}

greet();
```

---

# Example 2 — Arrow Function with Parameter and Return Value

```ts
let square = (num:number):number => {

    return num * num;
}

console.log(square(5));
```

---

# Output

```text
25
```

---

# Example 3 — Arrow Function with Multiple Parameters

```ts
let add = (a:number, b:number):number => {

    return a + b;
}

console.log(add(10,20));
```

---

# Output

```text
30
```

---

# Short Form Arrow Function

If function contains only one statement:

```ts
let cube = (num:number):number => num ** 3;

console.log(cube(3));
```

---

# Output

```text
27
```

---

# Difference Between Normal Function and Arrow Function

| Normal Function | Arrow Function |
|---|---|
| Uses `function` keyword | Uses `=>` |
| Longer syntax | Shorter syntax |
| Traditional style | Modern ES6 style |

---

# Important Points

- Arrow functions are shorter and cleaner
- Mostly used in modern JavaScript and TypeScript
- Useful in callbacks and array methods
- Return type can be defined using `:`

---

# Best Practice

Use arrow functions for:
- small reusable functions
- callbacks
- cleaner code readability

---

# Arrow Functions in TypeScript

---

## Q1. What is an arrow function?

### Answer

An arrow function is a shorter and cleaner way to write a function.

It was introduced in ES6 and uses the `=>` operator.

### Example

```ts
const greet = (): void => {

    console.log("Welcome");

}
```

---

## Q2. Why do we use arrow functions?

### Answer

Arrow functions make code:

- Shorter
- Cleaner
- Easier to read

They are commonly used in modern JavaScript and TypeScript projects.

### Interview Answer (Short)

> "Arrow functions reduce boilerplate code and improve readability."

---

## Q3. What is the difference between a normal function and an arrow function?

| Normal Function | Arrow Function |
|-----------------|----------------|
| Uses `function` keyword | Uses `=>` |
| Longer syntax | Shorter syntax |
| Traditional style | Modern ES6 style |

### Example

Normal Function

```ts
function add(a:number,b:number):number{

    return a+b;

}
```

Arrow Function

```ts
const add = (a:number,b:number):number => {

    return a+b;

}
```

---

## Q4. Can an arrow function take parameters?

### Answer

Yes.

It can take:

- No parameters
- One parameter
- Multiple parameters

Example

```ts
const square = (num:number):number => {

    return num*num;

}
```

---

## Q5. Can an arrow function return a value?

### Answer

Yes.

If the function has only one statement, we can write it in short form.

Example

```ts
const cube = (num:number):number => num ** 3;
```

This automatically returns the result.

---

## Q6. Why are arrow functions popular in modern TypeScript?

### Answer

Because they:

- Reduce code
- Improve readability
- Are widely used in callbacks
- Work well with array methods like `forEach()`, `map()`, `filter()`, and `find()`.

**Note:** We'll learn these array methods in the Arrays topic.

---

## Q7. Where have you seen arrow functions in Playwright?

### Answer

Arrow functions are used in:

- Test blocks
- Hooks
- Helper functions
- Utility functions

Example

```ts
test("Login Test", async ({ page }) => {

    // Test steps

});
```

---

## Q8. Are arrow functions faster than normal functions?

### Answer

No.

The main advantage is cleaner and more readable code, not performance.

---

## Q9. When would you choose an arrow function over a normal function?

### Answer

I prefer arrow functions for:

- Small helper functions
- Utility methods
- Callback functions
- Modern TypeScript code

For larger functions, either style is acceptable depending on readability.

---

## Q10. Why do Playwright examples mostly use arrow functions?

### Answer

Because Playwright is built on modern JavaScript/TypeScript practices.

Arrow functions make test code shorter, cleaner, and easier to read, especially when writing tests and callbacks.
