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
