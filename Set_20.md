# Set in TypeScript

A **Set** is a collection that stores **only unique values**.

If you try to add a duplicate value, it is automatically ignored.

---

# Why Use Set?

Without Set:

```ts
let browsers = ["Chrome", "Firefox", "Chrome", "Edge", "Firefox"];

console.log(browsers);
```

Output

```text
["Chrome", "Firefox", "Chrome", "Edge", "Firefox"]
```

With Set:

```ts
let browsers = new Set(["Chrome", "Firefox", "Chrome", "Edge", "Firefox"]);

console.log(browsers);
```

Output

```text
Set(3) { 'Chrome', 'Firefox', 'Edge' }
```

Duplicates are automatically removed.

---

# Creating a Set

## Empty Set

```ts
let browsers = new Set<string>();
```

---

## Set with Initial Values

```ts
let browsers = new Set(["Chrome", "Firefox", "Edge"]);
```

---

# add()

Adds a new value to the Set.

## Syntax

```ts
set.add(value);
```

## Example

```ts
let browsers = new Set<string>();

browsers.add("Chrome");
browsers.add("Firefox");
browsers.add("Edge");

console.log(browsers);
```

Output

```text
Set(3) { 'Chrome', 'Firefox', 'Edge' }
```

---

# Duplicate Values

```ts
let browsers = new Set<string>();

browsers.add("Chrome");
browsers.add("Chrome");
browsers.add("Chrome");

console.log(browsers);
```

Output

```text
Set(1) { 'Chrome' }
```

---

# has()

Checks whether a value exists.

Returns:

* true
* false

## Syntax

```ts
set.has(value);
```

## Example

```ts
let browsers = new Set(["Chrome","Firefox"]);

console.log(browsers.has("Chrome"));
console.log(browsers.has("Edge"));
```

Output

```text
true
false
```

---

# delete()

Removes a value.

## Syntax

```ts
set.delete(value);
```

## Example

```ts
let browsers = new Set(["Chrome","Firefox","Edge"]);

browsers.delete("Firefox");

console.log(browsers);
```

Output

```text
Set(2) { 'Chrome', 'Edge' }
```

---

# size

Returns the total number of unique values.

```ts
let browsers = new Set(["Chrome","Firefox","Chrome"]);

console.log(browsers.size);
```

Output

```text
2
```

---

# clear()

Removes all values.

```ts
let browsers = new Set(["Chrome","Firefox"]);

browsers.clear();

console.log(browsers);
```

Output

```text
Set(0) {}
```

---

# Iterating a Set

```ts
let browsers = new Set(["Chrome","Firefox","Edge"]);

for (let browser of browsers) {

    console.log(browser);

}
```

Output

```text
Chrome
Firefox
Edge
```

---

# Convert Array → Set

```ts
let browsers = [
    "Chrome",
    "Firefox",
    "Chrome",
    "Edge"
];

let uniqueBrowsers = new Set(browsers);

console.log(uniqueBrowsers);
```

---

# Convert Set → Array

```ts
let browsers = new Set([
    "Chrome",
    "Firefox",
    "Edge"
]);

let browserArray = [...browsers];

console.log(browserArray);
```

Output

```text
["Chrome","Firefox","Edge"]
```

---

# Remove Duplicates from Array ⭐⭐⭐⭐⭐

This is the most commonly asked interview use case.

```ts
let browsers = [
    "Chrome",
    "Firefox",
    "Chrome",
    "Edge",
    "Firefox"
];

let uniqueBrowsers = [...new Set(browsers)];

console.log(uniqueBrowsers);
```

Output

```text
["Chrome","Firefox","Edge"]
```

---

# Playwright Examples

## Remove Duplicate Browser Names

```ts
let browsers = [
    "Chrome",
    "Firefox",
    "Chrome",
    "Edge"
];

let uniqueBrowsers = [...new Set(browsers)];
```

---

## Validate Unique Test IDs

```ts
let testIds = [
    101,
    102,
    103,
    101
];

let uniqueTestIds = new Set(testIds);

console.log(uniqueTestIds.size);
```

---

## Unique Dropdown Values

```ts
let countries = [
    "India",
    "India",
    "USA",
    "UK"
];

let uniqueCountries = [...new Set(countries)];
```

---

# Array vs Set

| Array              | Set                       |
| ------------------ | ------------------------- |
| Allows duplicates  | Stores only unique values |
| Access by index    | No index access           |
| Ordered collection | Ordered unique collection |
| Uses `length`      | Uses `size`               |

---

# Interview Notes

* Set stores only **unique values**.
* Duplicate values are ignored automatically.
* Set does not support index-based access.
* Use `add()` to insert values.
* Use `has()` to check existence.
* Use `delete()` to remove values.
* Use `clear()` to remove all values.
* Use `size` to count elements.
* A Set can be converted to an array using the spread operator (`...`).

---

# Interview Questions

### Q1. What is a Set?

A Set is a collection that stores only unique values.

---

### Q2. Can Set store duplicate values?

No. Duplicate values are ignored automatically.

---

### Q3. How do you remove duplicates from an array?

```ts
let unique = [...new Set(array)];
```

---

### Q4. Difference between Array and Set?

| Array              | Set                |
| ------------------ | ------------------ |
| Allows duplicates  | Unique values only |
| Uses `length`      | Uses `size`        |
| Index-based access | No index access    |

---

### Q5. When have you used Set in automation?

* Removing duplicate browser names
* Removing duplicate URLs
* Validating unique dropdown values
* Removing duplicate test IDs
* Comparing unique values

---

# Interview Priority

⭐⭐⭐⭐⭐ **Very High**

Set is much more commonly discussed than Tuple or Enum, especially the question:

> **"How do you remove duplicate values from an array in JavaScript/TypeScript?"**

Expected answer:

```ts
let uniqueArray = [...new Set(array)];
```
