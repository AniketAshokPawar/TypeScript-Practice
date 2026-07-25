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

---

# Arrays in TypeScript - Most Asked Practice Question List

1. Find maximum value from an array.

2. Find minimum value from an array.

3. Find average of array elements.

4. Remove duplicate values from an array.

5. Find duplicate values in an array.

6. Find second largest number from an array.

7. Find missing number from an array.

8. Count frequency of elements in an array.

9. Reverse an array without using reverse() method.

10. Find common elements between two arrays.

11. Move all zero values to the end of an array.

12. Search whether a value exists in an array.

13. Compare two arrays and find missing/different values.

14. Count elements based on a condition (example: Passed/Failed test cases).

15. Find failed test cases from test execution result array.

16. Execute same test on multiple browsers using array data.

17. Execute same test on multiple environments using array data.

18. Handle multiple users/test data using arrays for data-driven testing.

19. Find highest and lowest test execution time from test results.

20. Process multiple test cases dynamically using array data.
