# TypeScript Map

A **Map** is a collection used to store data in **key-value pairs**.

```text
Key → Value
```

Example:

```ts
Chrome → 120
Firefox → 121
Edge → 122
```

---

# 1. Creating a Map

### Syntax

```ts
let mapName = new Map<keyType, valueType>();
```

### Example

```ts
let browsers = new Map<string, number>();
```

Here:

- `string` → type of key
- `number` → type of value

---

# 2. set()

Used to add a key-value pair to the Map.

### Syntax

```ts
map.set(key, value);
```

### Example

```ts
let browsers = new Map<string, number>();

browsers.set("Chrome", 120);
browsers.set("Firefox", 121);
browsers.set("Edge", 122);
```

---

# 3. get()

Used to retrieve a value using its key.

### Example

```ts
console.log(browsers.get("Chrome"));
```

Output:

```text
120
```

If the key does not exist:

```ts
console.log(browsers.get("Safari"));
```

Output:

```text
undefined
```

---

# 4. has()

Checks whether a key exists in the Map.

Returns:

- `true` → key exists
- `false` → key does not exist

### Example

```ts
console.log(browsers.has("Chrome"));
```

Output:

```text
true
```

```ts
console.log(browsers.has("Safari"));
```

Output:

```text
false
```

---

# 5. delete()

Removes a key-value pair.

### Example

```ts
browsers.delete("Firefox");
```

Firefox is removed from the Map.

---

# 6. clear()

Removes all key-value pairs.

### Example

```ts
browsers.clear();
```

The Map becomes empty.

---

# 7. size

Returns the number of key-value pairs in the Map.

### Example

```ts
console.log(browsers.size);
```

---

# 8. keys()

Returns all keys.

### Example

```ts
for (let key of browsers.keys()) {

    console.log(key);
}
```

Output:

```text
Chrome
Firefox
Edge
```

---

# 9. values()

Returns all values.

### Example

```ts
for (let value of browsers.values()) {

    console.log(value);
}
```

Output:

```text
120
121
122
```

---

# 10. entries()

Returns both key and value.

### Example

```ts
for (let entry of browsers.entries()) {

    console.log(entry);
}
```

Output:

```text
["Chrome", 120]
["Firefox", 121]
["Edge", 122]
```

---

# 11. Iterating Map using for...of

A Map can directly be iterated using `for...of`.

```ts
for (let [browser, version] of browsers) {

    console.log(`${browser} - ${version}`);
}
```

Output:

```text
Chrome - 120
Firefox - 121
Edge - 122
```

### Important

Map's default iteration is over its **key-value pairs (entries)**.

Therefore:

```ts
for (let [key, value] of map)
```

is very commonly used.

---

# 12. Updating an Existing Value

Using `set()` with an existing key updates its value.

```ts
let browsers = new Map<string, number>();

browsers.set("Chrome", 120);

browsers.set("Chrome", 125);

console.log(browsers.get("Chrome"));
```

Output:

```text
125
```

There is still only one `"Chrome"` key.

---

# 13. Map Can Use Different Key Types

Keys do not have to be strings.

### Example

```ts
let employees = new Map<number, string>();

employees.set(101, "Aniket");
employees.set(102, "Rahul");
employees.set(103, "Sachin");

console.log(employees.get(101));
```

Output:

```text
Aniket
```

---

# 14. Map vs Array

| Array | Map |
|---|---|
| Stores values | Stores key-value pairs |
| Access using index | Access using key |
| Uses `length` | Uses `size` |
| Allows duplicate values | Keys are unique |
| `array[0]` | `map.get(key)` |

---

# 15. Map vs Set

| Map | Set |
|---|---|
| Stores key-value pairs | Stores values |
| Uses `set()` | Uses `add()` |
| Uses `get()` | No `get()` |
| Keys are unique | Values are unique |
| Example: ID → Name | Example: unique browser names |

### Example

Map:

```ts
let employees = new Map<number, string>();

employees.set(101, "Aniket");
```

Set:

```ts
let browsers = new Set<string>();

browsers.add("Chrome");
```

---

# 16. Map vs Object

Both can store key-value data, but Map is specifically designed for key-value collections.

### Object

```ts
let employee = {
    id: 101,
    name: "Aniket"
};
```

### Map

```ts
let employee = new Map<number, string>();

employee.set(101, "Aniket");
```

Map provides built-in methods such as:

```ts
set()
get()
has()
delete()
clear()
```

and provides the `size` property.

---

# Real Automation Examples

## Environment → URL

```ts
let environmentUrls = new Map<string, string>();

environmentUrls.set(
    "QA",
    "https://qa.application.com"
);

environmentUrls.set(
    "UAT",
    "https://uat.application.com"
);

environmentUrls.set(
    "PROD",
    "https://application.com"
);

console.log(environmentUrls.get("QA"));
```

---

## Test Case ID → Status

```ts
let testStatus = new Map<string, string>();

testStatus.set("TC001", "Passed");
testStatus.set("TC002", "Failed");
testStatus.set("TC003", "Passed");
```

Print failed test cases:

```ts
for (let [id, status] of testStatus) {

    if (status === "Failed") {

        console.log(`${id} - ${status}`);
    }
}
```

---

# Quick Revision Table

| Method / Property | Purpose |
|---|---|
| `new Map()` | Creates a Map |
| `set()` | Adds/updates key-value pair |
| `get()` | Gets value using key |
| `has()` | Checks whether key exists |
| `delete()` | Removes key-value pair |
| `clear()` | Removes all entries |
| `size` | Number of entries |
| `keys()` | Returns keys |
| `values()` | Returns values |
| `entries()` | Returns key-value pairs |

---

# Interview Questions

## Q1. What is a Map in TypeScript?

A Map is a collection that stores data in **key-value pairs**.

---

## Q2. Difference between Map and Set?

- Map stores **key-value pairs**.
- Set stores **unique values**.
- Map uses `set()` and `get()`.
- Set uses `add()` and does not have `get()`.

---

## Q3. How do you remove duplicate values from an Array?

Using Set:

```ts
let uniqueArray = [...new Set(array)];
```

---

## Q4. How do you iterate through a Map?

```ts
for (let [key, value] of map) {

    console.log(key, value);
}
```

---

## Q5. What happens if you use `set()` with an existing Map key?

The existing value is **updated**.

```ts
map.set("Chrome", 120);
map.set("Chrome", 125);
```

The value becomes:

```text
Chrome → 125
```

---

# Important Interview Points

- Map stores **key-value pairs**.
- Map keys are **unique**.
- `set()` adds or updates a key-value pair.
- `get()` retrieves a value using a key.
- `has()` checks whether a key exists.
- `delete()` removes an entry.
- `clear()` removes all entries.
- `size` returns the number of entries.
- `keys()` returns keys.
- `values()` returns values.
- `entries()` returns key-value pairs.
- `for...of` directly iterates Map entries.
- Map can use different data types for keys.
- Map is useful when data naturally follows a **key → value** relationship.
