# Arrays in TypeScript

An array is used to store multiple values in a single variable.

---

# Array Syntax

```ts
let arrayName:dataType[] = [values];
```

---

# Example

```ts
let numbers:number[] = [10,20,30,40];

console.log(numbers);
```

---

# Output

```text
[10,20,30,40]
```

---

# Access Array Elements

Array elements are accessed using index.

Index starts from:
```text
0
```

---

## Example

```ts
let names:string[] = ["Aniket","Rahul","Amit"];

console.log(names[0]);

console.log(names[2]);
```

---

# Output

```text
Aniket
Amit
```

---

# Array Length

```ts
array.length
```

returns total elements.

---

## Example

```ts
let nums:number[] = [10,20,30];

console.log(nums.length);
```

---

# Output

```text
3
```

---

# Loop Through Array

```ts
let nums:number[] = [10,20,30];

for(let i = 0; i < nums.length; i++){

    console.log(nums[i]);
}
```

---

# Common Array Methods

| Method | Purpose |
|---|---|
| `push()` | Add element |
| `pop()` | Remove last element |
| `shift()` | Remove first element |
| `unshift()` | Add element at beginning |
| `length` | Total elements |

---

# Example — push()

```ts
let nums:number[] = [10,20];

nums.push(30);

console.log(nums);
```

---

# Output

```text
[10,20,30]
```

---

# Important Points

- Arrays store multiple values
- Index starts from `0`
- Arrays can contain:
    - numbers
    - strings
    - booleans
- TypeScript provides type safety for arrays

---

# Interview Point

Arrays are heavily used in:
- loops
- data handling
- API responses
- Playwright automation scripting
