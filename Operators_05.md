# Operators in TypeScript

Operators are symbols used to perform operations on variables and values.

---

# Types of Operators in TypeScript

1. Arithmetic Operators  
2. Assignment Operators  
3. Comparison Operators  
4. Logical Operators  
5. Increment and Decrement Operators  
6. Ternary Operator  

---

# 1. Arithmetic Operators

Used for mathematical calculations.

| Operator | Description |
|---|---|
| + | Addition |
| - | Subtraction |
| * | Multiplication |
| / | Division |
| % | Modulus (Remainder) |
| ** | Exponentiation (Power) |

---

## Example

```ts
let a: number = 10;
let b: number = 5;

console.log(a + b);
console.log(a - b);
console.log(a * b);
console.log(a / b);
console.log(a % b);
console.log(a ** b);
```
---

# 2. Assignment Operators

Used to assign values to variables.

| Operator | Name | Example |
|---|---|---|
| = | Simple Assignment Operator | x = 10 |
| += | Addition Assignment Operator | x += 5 |
| -= | Subtraction Assignment Operator | x -= 5 |
| *= | Multiplication Assignment Operator | x *= 5 |
| /= | Division Assignment Operator | x /= 5 |
| %= | Modulus Assignment Operator | x %= 5 |
| **= | Exponentiation Assignment Operator | x **= 2 |

---

# 3. Comparison Operators

Used to compare values.

Always returns `true` or `false`.

| Operator | Description |
|---|---|
| == | Equal to |
| === | Strict equal to |
| != | Not equal to |
| > | Greater than |
| < | Less than |
| >= | Greater than or equal to |
| <= | Less than or equal to |

---

# 4. Logical Operators

Used to combine conditions.

| Operator | Description |
|---|---|
| && | Logical AND |
| \|\| | Logical OR |
| ! | Logical NOT |

---

# 5. Increment and Decrement Operators

Used to increase or decrease values.

| Operator | Description |
|---|---|
| ++ | Increment |
| -- | Decrement |

---

## Post Increment Example

```ts
let count = 50;

let res = count++;

console.log(res);

console.log(count);
```

### Output

```text
50
51
```

### Explanation

- First assigns current value to `res`
- Then increments `count`

---

## Pre Increment Example

```ts
let x = 45;

let res2 = ++x;

console.log(res2);

console.log(x);
```

### Output

```text
46
46
```

### Explanation

- First increments value
- Then assigns updated value to `res2`

---

# Difference Between Post and Pre Increment

| Type | Operation Order |
|---|---|
| count++ | Use value first, then increment |
| ++count | Increment first, then use value |

---

# 6. Ternary Operator

Short form of `if-else`.

## Syntax

```ts
condition ? trueValue : falseValue
```

---

## Example

```ts
let age: number = 20;

let result = age >= 18 ? "Eligible" : "Not Eligible";

console.log(result);
```

---

# Interview Points

- `===` is preferred over `==`
- `++x` is Pre Increment
- `x++` is Post Increment
- Arithmetic operators perform mathematical operations
- Logical operators are used in conditions
- Ternary operator is shorthand for `if-else`

---

# Operators in TypeScript - Interview Questions

---

## Q1. What are operators in TypeScript?

### Answer:

Operators are symbols used to perform operations on variables and values.

Examples:

- Arithmetic operations
- Value comparison
- Logical conditions
- Assignment operations

Example:

```typescript
let a = 10;
let b = 5;

console.log(a + b);
```

---

### Interview Answer (Short)

> "Operators are symbols used to perform operations like calculation, comparison, assignment, and logical conditions on values."

---

# Q2. What are the different types of operators in TypeScript?

### Answer:

Common operators:

1. Arithmetic Operators
2. Assignment Operators
3. Comparison Operators
4. Logical Operators
5. Increment/Decrement Operators
6. Ternary Operator

---

### Interview Answer (Short)

> "TypeScript supports arithmetic, assignment, comparison, logical, increment/decrement, and ternary operators."

---

# Q3. What is the difference between `==` and `===`?

### Answer:

`==` checks only value.

`===` checks:
- Value
- Data type

Example:

```typescript
console.log(5 == "5"); 
// true

console.log(5 === "5"); 
// false
```

---

### Why prefer `===`?

Because it avoids unexpected type conversion.

---

### Interview Answer (Short)

> "`==` compares only values after type conversion, while `===` compares both value and data type. In automation code, I prefer `===` because it is safer."

---

# Q4. What is the difference between `&&` and `||` operators?

### Answer:

### AND (`&&`)

Returns true only when all conditions are true.

Example:

```typescript
username && password
```

Both values are required.

---

### OR (`||`)

Returns true when at least one condition is true.

Example:

```typescript
browser === "Chrome" || browser === "Edge"
```

---

### Interview Answer (Short)

> "`&&` requires all conditions to be true, whereas `||` requires at least one condition to be true."

---

# Q5. Difference between pre-increment and post-increment?

### Answer:

### Post Increment (`x++`)

First uses the value, then increments.

Example:

```typescript
let x = 5;

let y = x++;
```

Result:

```text
y = 5
x = 6
```

---

### Pre Increment (`++x`)

First increments, then uses the value.

Example:

```typescript
let x = 5;

let y = ++x;
```

Result:

```text
y = 6
x = 6
```

---

### Interview Answer (Short)

> "Post increment uses the current value first and then increases it. Pre increment increases the value first and then uses it."

---

# Q6. Why do we prefer `===` over `==` in automation frameworks?

### Answer:

Because automation frameworks deal with:

- User inputs
- API responses
- Test data
- Application values

Unexpected type conversion can create false results.

Example:

```typescript
if(status === "200"){
    
}
```

is safer than:

```typescript
if(status == 200){

}
```

---

### Interview Answer (Short)

> "I prefer `===` because it performs strict comparison and avoids unexpected type conversion during test execution."

---

# Q7. Where do you use logical operators in Playwright automation?

### Answer:

Logical operators are commonly used for conditions.

Example:

```typescript
if(username && password){

   await login();

}
```

Meaning:

Execute login only when both values exist.

---

Another example:

```typescript
if(browser === "Chrome" || browser === "Firefox"){

}
```

---

### Interview Answer (Short)

> "In Playwright, I use logical operators for conditions like validating test data, browser checks, and execution flow."

---

# Q8. What is the ternary operator? Why use it?

### Answer:

Ternary operator is a short form of `if-else`.

Syntax:

```typescript
condition ? trueValue : falseValue
```

Example:

```typescript
let result = age >= 18 
             ? "Eligible" 
             : "Not Eligible";
```

---

### Interview Answer (Short)

> "The ternary operator is a shorter way of writing simple if-else conditions. It improves readability for small conditions."

---

# Q9. Can you give a real Playwright example of assignment operators?

### Answer:

Example:

```typescript
let retryCount = 0;

retryCount += 1;
```

Instead of:

```typescript
retryCount = retryCount + 1;
```

Common usage:

- Retry counters
- Loop counters
- Test execution counts

---

### Interview Answer (Short)

> "I use assignment operators for updating counters, flags, and values during test execution."

---

# Q10. Which operators do you use most in your Playwright framework?

### Answer:

Commonly used:

- `===` for validation checks
- `&&` for multiple conditions
- `||` for alternative conditions
- `+=` for counters
- Ternary operators for simple conditions

Example:

```typescript
if(browser === "Chrome" || browser === "Edge"){

}
```

---

### Interview Answer (Short)

> "In Playwright automation, I mostly use strict comparison (`===`), logical operators for conditions, and assignment operators for counters and variables."
