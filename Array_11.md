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

# Arrays in TypeScript - Practice Question List

1. Extract specific information from array values.

2. Find maximum value from an array.

3. Find minimum value from an array.

4. Calculate average value of array elements.

5. Remove duplicate values from an array.

6. Find duplicate values present in an array.

7. Find second largest number from an array.

8. Find missing number from an array.

9. Count frequency of elements in an array.

10. Reverse an array without using reverse() method.

11. Find common elements between two arrays.

12. Move specific values (example: zeros) to the end of an array.

13. Search whether a specific value exists in an array.

14. Count elements based on a condition.

15. Compare two arrays and find missing values.

16. Execute same test scenario for multiple browsers using array data.

17. Execute same test scenario for multiple environments using array data.

18. Handle multiple users/test data using arrays.

19. Validate browser support using array values.

20. Store and process test execution results using arrays.

21. Iterate through array data and perform actions on each value.

22. Find failed/passed test cases from execution result array.

23. Filter required test data from an array (basic loop logic).

24. Handle multiple combinations using nested arrays.

25. Use arrays for data-driven testing scenarios in Playwright.

26. Store API response data and validate array values.

27. Compare expected and actual test data arrays.

28. Process multiple test cases dynamically using arrays.

29. Find highest/lowest execution time from test result data.

30. Convert raw test data array into required test execution format.
