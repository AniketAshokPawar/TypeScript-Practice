# Array Methods in TypeScript

---

# 1. push()

Used to add one or more elements at the end of an array.

## Syntax

```ts
array.push(value);
```

## Example

```ts
let nums:number[] = [10,20];

nums.push(30);

console.log(nums);
```

### Output

```text
[10,20,30]
```

---

# 2. pop()

Used to remove the last element from an array.

Returns removed element.

## Syntax

```ts
array.pop();
```

## Example

```ts
let nums:number[] = [10,20,30];

let removed = nums.pop();

console.log(nums);

console.log(removed);
```

### Output

```text
[10,20]

30
```

---

# 3. shift()

Used to remove the first element from an array.

Returns removed element.

## Syntax

```ts
array.shift();
```

## Example

```ts
let nums:number[] = [10,20,30];

let removed = nums.shift();

console.log(nums);

console.log(removed);
```

### Output

```text
[20,30]

10
```

---

# 4. unshift()

Used to add one or more elements at the beginning of an array.

## Syntax

```ts
array.unshift(value);
```

## Example

```ts
let nums:number[] = [20,30];

nums.unshift(10);

console.log(nums);
```

### Output

```text
[10,20,30]
```

---

# 5. concat()

Used to merge two or more arrays.

Does NOT modify original arrays.

## Syntax

```ts
array1.concat(array2);
```

## Example

```ts
let arr1:number[] = [10,20];

let arr2:number[] = [30,40];

let result = arr1.concat(arr2);

console.log(result);
```

### Output

```text
[10,20,30,40]
```

---

# 6. slice()

Used to extract a portion of an array.

Does NOT modify original array.

## Syntax

```ts
array.slice(startIndex,endIndex);
```

## Example

```ts
let nums:number[] = [10,20,30,40,50];

let result = nums.slice(1,4);

console.log(result);
```

### Output

```text
[20,30,40]
```

---

# 7. splice()

Used to:
- add elements
- remove elements
- replace elements

Modifies original array.

## Syntax

```ts
array.splice(startIndex,deleteCount,newValue);
```

## Example

```ts
let nums:number[] = [10,20,30,40];

nums.splice(2,1,300);

console.log(nums);
```

### Output

```text
[10,20,300,40]
```

---

# 8. indexOf()

Used to find index of an element.

Returns:
- index if found
- -1 if not found

## Syntax

```ts
array.indexOf(value);
```

## Example

```ts
let nums:number[] = [10,20,30,40];

console.log(nums.indexOf(30));
```

### Output

```text
2
```

---

# 9. includes()

Used to check whether an element exists in array.

Returns:
- true
- false

## Syntax

```ts
array.includes(value);
```

## Example

```ts
let nums:number[] = [10,20,30];

console.log(nums.includes(20));
```

### Output

```text
true
```

---

# 10. toString()

Converts array into comma-separated string.

## Syntax

```ts
array.toString();
```

## Example

```ts
let nums:number[] = [10,20,30];

let result = nums.toString();

console.log(result);

console.log(typeof result);
```

### Output

```text
10,20,30

string
```

---

# Interview Revision Table

| Method | Purpose | Original Array Modified? |
|----------|----------|----------|
| `push()` | Add at end | ✅ Yes |
| `pop()` | Remove last element | ✅ Yes |
| `shift()` | Remove first element | ✅ Yes |
| `unshift()` | Add at beginning | ✅ Yes |
| `concat()` | Merge arrays | ❌ No |
| `slice()` | Extract elements | ❌ No |
| `splice()` | Add/Remove/Replace | ✅ Yes |
| `indexOf()` | Find index | ❌ No |
| `includes()` | Check existence | ❌ No |
| `toString()` | Convert to string | ❌ No |

---

# Most Important Interview Question

## Difference Between slice() and splice()

| slice() | splice() |
|----------|----------|
| Extracts elements | Adds/Removes/Replaces elements |
| Does not modify original array | Modifies original array |
| Returns extracted array | Returns removed elements |

---

Q1. Difference between `push()` and `unshift()`?
================================================

Answer:
-------

Both methods add elements to an array, but position is different.

| Method | Adds Element At |
| --- | --- |
| `push()` | End of array |
| `unshift()` | Beginning of array |

Example:

```
let browsers:string[] = ["Chrome","Firefox"];

browsers.push("Edge");

console.log(browsers);
```

Output:

```
[
"Chrome",
"Firefox",
"Edge"
]
```

* * * * *

```
let browsers:string[] = ["Firefox","Edge"];

browsers.unshift("Chrome");

console.log(browsers);
```

Output:

```
[
"Chrome",
"Firefox",
"Edge"
]
```

* * * * *

Q2. Difference between `pop()` and `shift()`?
=============================================

Answer:
-------

Both remove elements from an array.

| Method | Removes |
| --- | --- |
| `pop()` | Last element |
| `shift()` | First element |

Example:

```
let numbers:number[]=[10,20,30];

let result=numbers.pop();

console.log(result);
console.log(numbers);
```

Output:

```
30

[10,20]
```

* * * * *

```
let numbers:number[]=[10,20,30];

let result=numbers.shift();

console.log(result);
console.log(numbers);
```

Output:

```
10

[20,30]
```

* * * * *

Q3. Difference between `slice()` and `splice()`? ⭐⭐⭐⭐⭐
======================================================

Answer:
-------

This is one of the most asked questions.

| slice() | splice() |
| --- | --- |
| Used to extract elements | Used to add/remove/replace elements |
| Does not modify original array | Modifies original array |
| Returns copied array | Returns removed elements |

Example:

### slice()

```
let arr=[10,20,30,40];

let result=arr.slice(1,3);

console.log(result);
console.log(arr);
```

Output:

```
[20,30]

[10,20,30,40]
```

Original array unchanged.

* * * * *

### splice()

```
let arr=[10,20,30,40];

let result=arr.splice(1,2);

console.log(result);
console.log(arr);
```

Output:

```
[20,30]

[10,40]
```

Original array modified.

* * * * *

Q4. Does `concat()` modify the original array?
==============================================

Answer:
-------

No.

`concat()` creates a new array.

Example:

```
let smoke=[
"Login",
"Search"
];

let regression=[
"Payment",
"Checkout"
];

let allTests=smoke.concat(regression);

console.log(allTests);
console.log(smoke);
```

Output:

```
[
"Login",
"Search",
"Payment",
"Checkout"
]

[
"Login",
"Search"
]
```

* * * * *

Q5. How to remove duplicate values from an array?
=================================================

Answer:
-------

Using loop:

```
let users=[
"admin",
"tester",
"admin",
"guest"
];

let unique:string[]=[];

for(let user of users){

    if(!unique.includes(user)){

        unique.push(user);
    }
}

console.log(unique);
```

Output:

```
[
"admin",
"tester",
"guest"
]
```

* * * * *

Modern approach:

```
let unique=[...new Set(users)];
```

* * * * *

Q6. How to find duplicate values from an array?
===============================================

Answer:
-------

```
let users=[
"admin",
"tester",
"admin",
"guest",
"tester"
];

let unique:string[]=[];
let duplicate:string[]=[];

for(let user of users){

    if(unique.includes(user)){

        if(!duplicate.includes(user)){

            duplicate.push(user);
        }

    }
    else{

        unique.push(user);
    }
}

console.log(duplicate);
```

Output:

```
[
"admin",
"tester"
]
```

* * * * *

Q7. Difference between `indexOf()` and `includes()`?
====================================================

Answer:
-------

| indexOf() | includes() |
| --- | --- |
| Returns index position | Returns true/false |
| Returns -1 if not found | Returns false if not found |

Example:

```
let browsers=[
"Chrome",
"Firefox",
"Edge"
];

console.log(browsers.indexOf("Firefox"));
```

Output:

```
1
```

* * * * *

```
console.log(browsers.includes("Firefox"));
```

Output:

```
true
```

* * * * *

Q8. How to check if an element exists in an array?
==================================================

Answer:
-------

Use `includes()`.

Example:

```
let browsers=[
"Chrome",
"Firefox"
];

if(browsers.includes("Chrome")){

    console.log("Browser available");
}
```

Output:

```
Browser available
```

* * * * *

Q9. How to merge two arrays?
============================

Answer:
-------

Using `concat()`.

Example:

```
let arr1=[1,2,3];

let arr2=[4,5,6];

let result=arr1.concat(arr2);

console.log(result);
```

Output:

```
[1,2,3,4,5,6]
```

* * * * *

Q10. How to replace an element in an array?
===========================================

Answer:
-------

Using `splice()`.

Example:

```
let browsers=[
"Chrome",
"Firefox",
"Edge"
];

browsers.splice(1,1,"Safari");

console.log(browsers);
```

Output:

```
[
"Chrome",
"Safari",
"Edge"
]
```

Explanation:

```
1 → starting index

1 → delete one element

Safari → new value
```

* * * * *

Q11. How to remove a specific element from an array?
====================================================

Answer:
-------

Find index using `indexOf()` and remove using `splice()`.

Example:

```
let browsers=[
"Chrome",
"Firefox",
"Edge"
];

let index=browsers.indexOf("Firefox");

if(index!=-1){

    browsers.splice(index,1);
}

console.log(browsers);
```

Output:

```
[
"Chrome",
"Edge"
]
```

* * * * *

Q12. Difference between `delete` operator and `splice()`?
=========================================================

Answer:
-------

`delete` removes value but keeps empty position.

Example:

```
let arr=[10,20,30];

delete arr[1];

console.log(arr);
```

Output:

```
[10,empty,30]
```

* * * * *

`splice()` removes completely.

```
arr.splice(1,1);
```

Output:

```
[10,30]
```

* * * * *

Q13. How to convert array into string?
======================================

Answer:
-------

Using `toString()`.

Example:

```
let browsers=[
"Chrome",
"Firefox"
];

let result=browsers.toString();

console.log(result);
```

Output:

```
Chrome,Firefox
```

* * * * *

Q14. How to find the length of an array?
========================================

Answer:
-------

Using `.length`.

Example:

```
let tests=[
"Login",
"Search",
"Payment"
];

console.log(tests.length);
```

Output:

```
3
```

* * * * *

Q15. In Playwright automation, where are arrays commonly used?
==============================================================

Answer:
-------

Arrays are commonly used for:

### 1\. Data Driven Testing

```
let users=[
"admin",
"tester",
"guest"
];
```

Running same test with multiple data.

### 2\. Browser Testing

```
let browsers=[
"Chrome",
"Firefox",
"Edge"
];
```

Execute tests on multiple browsers.

### 3\. API Response Handling

Example:

```
let responseUsers=[];
```

Store and validate multiple API objects.

### 4\. Multiple Test Scenarios

```
let testCases=[
"Login",
"Search",
"Checkout"
];
```
