# Var, Let, Const in TypeScript

---

# 1. Scope

- `var` → Function Scope
- `let` and `const` → Block Scope

## Example

```ts
function variables(){

    if(true){

        var x = "Aniket";
        let y = "Ashok";
        const z = "Pawar";

        console.log(x);
        console.log(y);
        console.log(z);
    }

    console.log(x);

    // console.log(y);
    // Error:
    // Cannot access 'y' outside block scope

    // console.log(z);
    // Error:
    // Cannot access 'z' outside block scope
}

variables();
```

---

# 2. Declaration and Initialization

- `var` and `let` can be declared first and initialized later.
- `const` must be initialized during declaration.

## Example

```ts
var x;
x = 10;
console.log(x);

let y;
y = 20;
console.log(y);

// const z;
// Error:
// Const declarations must be initialized

// z = 30;
// console.log(z);
```

---

# 3. Re-Declaration

- Re-declaration is allowed only with `var`.

## Example

```ts
var Mname = "Aniket";
var Mname = "Annnniket";

console.log(Mname);
```

## Important Point

```ts
let city = "Mumbai";
// let city = "Pune"; // Error

const country = "India";
// const country = "USA"; // Error
```

---

# 4. Reassignment

- Reassignment is allowed for `var` and `let`.
- Reassignment is NOT allowed for `const`.

## Example

```ts
var age = 45;
age = 60;

console.log(age);

let ht = 45;
ht = 77;

console.log(ht);


// const salary = 50000;
// salary = 70000; // Error
```

---

# Interview Points

| Keyword | Scope | Re-Declaration | Reassignment |
|---|---|---|---|
| var | Function Scope | Allowed | Allowed |
| let | Block Scope | Not Allowed | Allowed |
| const | Block Scope | Not Allowed | Not Allowed |

---

# Best Practice

- Prefer using `const` by default.
- Use `let` when value needs to change.
- Avoid `var` in modern TypeScript/JavaScript.

---

# Var, Let, Const - Interview Questions

## Q1. What is the difference between `var`, `let`, and `const`?

### Answer

| Feature | var | let | const |
|---------|-----|-----|-------|
| Scope | Function | Block | Block |
| Re-declaration | ✅ Allowed | ❌ Not Allowed | ❌ Not Allowed |
| Reassignment | ✅ Allowed | ✅ Allowed | ❌ Not Allowed |

---

### Interview Answer (Short)

> "`var` has function scope and allows both re-declaration and reassignment. `let` has block scope and allows reassignment only. `const` has block scope and cannot be reassigned."

---

## Q2. Why should we avoid using `var` in modern TypeScript/JavaScript?

### Answer

Because:

- It has function scope instead of block scope.
- It allows re-declaration, which can introduce bugs.
- `let` and `const` provide better control over variable scope.

---

### Interview Answer (Short)

> "I avoid `var` because it allows re-declaration and has function scope, which can lead to unexpected behavior. I prefer `let` and `const`."

---

## Q3. When should you use `const` instead of `let`?

### Answer

Use `const` whenever the variable value will not change.

Use `let` only if the value needs to be updated later.

Example:

```typescript
const username = "admin";
let retryCount = 0;
```

---

### Interview Answer (Short)

> "I use `const` by default. If a variable needs to change later, I use `let`."

---

## Q4. Can a `const` object be modified?

### Answer

Yes.

You can modify the object's properties, but you cannot assign the variable to a different object.

Example:

```typescript
const user = {
    name: "Aniket"
};

user.name = "Pawar";   // ✅ Allowed
```

---

### Interview Answer (Short)

> "`const` protects the object reference, not the object's contents."

---

## Q5. What is variable shadowing?

### Answer

Variable shadowing occurs when an inner variable has the same name as an outer variable.

Example:

```typescript
let city = "Pune";

{
    let city = "Mumbai";
}
```

The inner variable temporarily hides the outer variable.

---

### Interview Answer (Short)

> "Variable shadowing means declaring a variable with the same name in an inner scope, which temporarily hides the outer variable."

---

## Q6. What is hoisting?

### Answer

Hoisting is JavaScript's behavior of moving variable declarations to the top of their scope before execution.

- `var` is hoisted and initialized with `undefined`.
- `let` and `const` are hoisted but remain in the Temporal Dead Zone until declaration.

---

### Interview Answer (Short)

> "Hoisting moves declarations to the top. `var` can be accessed as `undefined`, while `let` and `const` cannot be accessed before declaration."

---

## Q7. What is the Temporal Dead Zone (TDZ)?

### Answer

The Temporal Dead Zone is the period between entering a block and declaring a `let` or `const` variable.

Accessing the variable during this period throws a ReferenceError.

Example:

```typescript
console.log(age);

let age = 25;
```

---

### Interview Answer (Short)

> "The Temporal Dead Zone is the time before a `let` or `const` variable is initialized. Accessing it results in a ReferenceError."

---

## Q8. In Playwright automation, when would you use `const` and when would you use `let`?

### Answer

Use `const` for values that never change.

Use `let` for variables whose values change during execution.

Example:

```typescript
const username = "admin";
let retryCount = 0;
```

---

### Interview Answer (Short)

> "In Playwright, I use `const` for locators, URLs, and test data, while I use `let` for counters, flags, or variables whose values change."

---

## Q9. Why is `const` considered a best practice?

### Answer

Because it prevents accidental reassignment, making the code safer and easier to maintain.

If a value should never change, using `const` clearly communicates that intention.

---

### Interview Answer (Short)

> "Using `const` prevents accidental reassignment and makes the code easier to understand and maintain."

---

## Q10. Which keyword do you use most in your Playwright framework?

### Answer

Mostly `const`.

Examples:

- Locators
- Page objects
- Test data
- URLs
- Configuration values

Use `let` only when a variable must change during execution.

Avoid `var` in modern frameworks.

---

### Interview Answer (Short)

> "In our Playwright framework, I mostly use `const`. I use `let` only when a variable needs to change, and I avoid `var` because it can introduce scope-related issues."
