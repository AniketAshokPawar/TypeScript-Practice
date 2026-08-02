# Tuple in TypeScript

A **Tuple** is a fixed-size array where each position has a predefined data type.

Unlike arrays, the order and type of each element are fixed.

---

# Syntax

```ts
let tupleName: [type1, type2, type3];
```

---

# Example

```ts
let employee: [number, string] = [101, "Aniket"];

console.log(employee[0]);
console.log(employee[1]);
```

**Output**

```text
101
Aniket
```

---

# Updating Tuple Values

```ts
let employee: [number, string] = [101, "Aniket"];

employee[1] = "Rahul";

console.log(employee);
```

**Output**

```text
[101, "Rahul"]
```

---

# Invalid Example

```ts
let employee: [number, string];

employee = ["Aniket", 101];
```

**Error**

```text
Type 'string' is not assignable to type 'number'.
```

The order of types in a tuple is mandatory.

---

# Tuple vs Array

| Array                         | Tuple                          |
| ----------------------------- | ------------------------------ |
| Dynamic size                  | Fixed size                     |
| Usually stores same data type | Can store different data types |
| Flexible structure            | Fixed order and structure      |

---

# Playwright Example

```ts
let browserInfo: [string, number] = ["Chrome", 138];

console.log(browserInfo);
```

```ts
let loginResult: [boolean, string] = [true, "Login Successful"];
```

---

# Interview Notes

* Tuple is a **TypeScript-only** feature.
* A tuple has a fixed number of elements.
* Each index has a predefined data type.
* The order of values is important.
* Useful for storing small groups of related values.

---

# Common Interview Questions

### Q1. What is a Tuple in TypeScript?

**Answer:**

A Tuple is a fixed-size array where each position has a predefined data type.

---

### Q2. What is the difference between an Array and a Tuple?

**Answer:**

| Array                  | Tuple                        |
| ---------------------- | ---------------------------- |
| Dynamic size           | Fixed size                   |
| Usually same data type | Different data types allowed |
| Flexible               | Strict order and types       |

---

### Q3. Does JavaScript support Tuples?

**Answer:**

No.

Tuples are a **TypeScript** feature only.

---

### Q4. Can a Tuple store different data types?

**Answer:**

Yes.

Example:

```ts
let employee: [number, string, boolean] = [101, "Aniket", true];
```

---

# Interview Priority

⭐⭐⭐☆☆ (Medium)

Generally only conceptual questions are asked; tuple-based coding questions are uncommon for Playwright Automation interviews.
