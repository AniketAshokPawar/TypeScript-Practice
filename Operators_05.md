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
