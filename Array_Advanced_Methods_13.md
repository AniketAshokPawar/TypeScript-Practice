# Array Iteration Methods in TypeScript

These methods are commonly used to traverse and process arrays.

---

# 1. forEach()

Used to perform an action on each array element.

Returns:
```text
Nothing (void)
```

---

## Syntax

```ts
array.forEach((value,index) => {

});
```

---

## Example

```ts
let nums:number[] = [10,20,30];

nums.forEach((num,index)=>{

    console.log(`Index: ${index}, Value: ${num}`);
});
```

### Output

```text
Index: 0, Value: 10
Index: 1, Value: 20
Index: 2, Value: 30
```

---

# 2. map()

Used to transform each element and create a new array.

Returns:
```text
New Array
```

---

## Syntax

```ts
array.map((value,index)=>{

});
```

---

## Example

```ts
let nums:number[] = [10,20,30];

let doubled = nums.map(num => num*2);

console.log(doubled);
```

### Output

```text
[20,40,60]
```

---

# 3. filter()

Used to select elements matching a condition.

Returns:
```text
New Filtered Array
```

---

## Syntax

```ts
array.filter((value,index)=>{

});
```

---

## Example

```ts
let nums:number[] = [10,15,20,25,30];

let even = nums.filter(num => num%2==0);

console.log(even);
```

### Output

```text
[10,20,30]
```

---

# 4. some()

Checks whether at least one element satisfies a condition.

Returns:
```text
true / false
```

---

## Syntax

```ts
array.some((value,index)=>{

});
```

---

## Example

```ts
let nums:number[] = [10,20,30];

let result = nums.some(num => num>25);

console.log(result);
```

### Output

```text
true
```

Because:

```text
30 > 25
```

---

# 5. every()

Checks whether all elements satisfy a condition.

Returns:
```text
true / false
```

---

## Syntax

```ts
array.every((value,index)=>{

});
```

---

## Example

```ts
let nums:number[] = [10,20,30];

let result = nums.every(num => num>5);

console.log(result);
```

### Output

```text
true
```

Because all numbers are greater than 5.

---

# 6. reduce()

Used to reduce an array into a single value.

Returns:
```text
Single Value
```

---

## Syntax

```ts
array.reduce((accumulator,currentValue)=>{

},initialValue);
```

---

## Example

```ts
let nums:number[] = [10,20,30];

let sum = nums.reduce((acc,num)=>{

    return acc + num;

},0);

console.log(sum);
```

### Output

```text
60
```

---

# Difference Between Methods

| Method | Purpose | Return Type |
|----------|----------|----------|
| `forEach()` | Perform action on each element | `void` |
| `map()` | Transform elements | New Array |
| `filter()` | Select matching elements | New Array |
| `some()` | At least one matches? | Boolean |
| `every()` | All match? | Boolean |
| `reduce()` | Convert array into single value | Single Value |

---

# Quick Memory Trick

```text
forEach() → Do something

map() → Modify every element

filter() → Select elements

some() → At least one?

every() → Everyone?

reduce() → One final value
```

---

# Visual Example

```ts
let nums = [10,15,20,25,30];
```

```text
forEach()
↓
10
15
20
25
30

--------------------

map(num=>num*2)
↓
[20,30,40,50,60]

--------------------

filter(num=>num%2==0)
↓
[10,20,30]

--------------------

some(num=>num>25)
↓
true

--------------------

every(num=>num>5)
↓
true

--------------------

reduce((acc,num)=>acc+num,0)
↓
100
```

# Interview Priority (Playwright)

```text
1. forEach() ⭐⭐⭐⭐⭐
2. filter()  ⭐⭐⭐⭐⭐
3. map()     ⭐⭐⭐⭐
4. some()    ⭐⭐⭐
5. every()   ⭐⭐⭐
6. reduce()  ⭐⭐
```


# Interview VVIP Questions --- Array Iteration Methods in TypeScript

## (for 0--2.5 Years Automation Tester / Playwright Developer)

---

## Q1. Difference between forEach() and map() in TypeScript?

### Answer:

`forEach()` and `map()` both iterate over arrays, but their purpose is different.

### forEach()

- Used to perform an action on each element.

- Does not return a new array.

- Returns `undefined`.

- Mostly used for logging, updating external variables, performing actions.

Example:

```ts

let numbers:number[] = [1,2,3];

let result = numbers.forEach(num => {

    console.log(num);

});

console.log(result);

```

Output:

```

1

2

3

undefined

```

* * * * *

### map()

-   Used to transform array elements.

-   Returns a new array.

-   Original array remains unchanged.

Example:

```

let numbers:number[] = [1,2,3];

let result = numbers.map(num => num*2);

console.log(result);

```

Output:

```

[2,4,6]

```

### Interview Point:

Use:

```

forEach() → Execute something

map() → Create modified array

```

* * * * *

Q2. When will you use map() in Playwright automation?

=====================================================

### Answer:

`map()` is commonly used when extracting data from multiple UI elements.

Example:

Suppose we have multiple product names:

```

let products = [

    "Laptop",

    "Mobile",

    "Camera"

];

```

We can transform data:

```

let upperProducts = products.map(product => {

    return product.toUpperCase();

});

console.log(upperProducts);

```

Output:

```

[

"LAPTOP",

"MOBILE",

"CAMERA"

]

```

### Automation Example:

Extract text from multiple locators:

```

let texts = await page.locator(".product").allTextContents();

let formatted = texts.map(text => text.trim());

```

* * * * *

Q3. Difference between filter() and find()?

===========================================

### Answer:

Both are used for searching elements, but output is different.

| filter() | find() |

| --- | --- |

| Returns multiple elements | Returns first matching element |

| Returns array | Returns object/value |

| Used when multiple matches possible | Used when only one match needed |

Example:

```

let users = [

 {id:1,name:"Admin"},

 {id:2,name:"Tester"},

 {id:3,name:"Admin"}

];

let result1 = users.filter(user=>user.name==="Admin");

let result2 = users.find(user=>user.name==="Admin");

```

Output:

```

filter()

[

{id:1,name:"Admin"},

{id:3,name:"Admin"}

]

find()

{id:1,name:"Admin"}

```

* * * * *

Q4. Explain filter() with a real automation scenario.

=====================================================

### Answer:

`filter()` is used when we need only specific data from an array.

Example:

API response:

```

let testResults = [

{

 testcase:"Login",

 status:"Passed"

},

{

 testcase:"Payment",

 status:"Failed"

}

];

```

Get failed tests:

```

let failedTests = testResults.filter(test=>{

    return test.status==="Failed";

});

```

Output:

```

[

{

 testcase:"Payment",

 status:"Failed"

}

]

```

* * * * *

Q5. Difference between some() and every()?

==========================================

### Answer:

| some() | every() |

| --- | --- |

| Checks if at least one element matches | Checks if all elements match |

| Returns true/false | Returns true/false |

Example:

```

let results = [

"Passed",

"Failed",

"Passed"

];

console.log(

results.some(status=>status==="Failed")

);

```

Output:

```

true

```

Because one test failed.

* * * * *

Example:

```

let results = [

"Passed",

"Passed",

"Passed"

];

console.log(

results.every(status=>status==="Passed")

);

```

Output:

```

true

```

Because all tests passed.

* * * * *

Q6. Explain reduce() with an example.

=====================================

### Answer:

`reduce()` converts an array into a single value.

Common uses:

-   sum calculation

-   counting

-   grouping data

Example:

```

let executionTime = [

100,

200,

300

];

let total = executionTime.reduce((sum,time)=>{

return sum + time;

},0);

console.log(total);

```

Output:

```

600

```

Explanation:

```

Initial accumulator = 0

0+100 =100

100+200=300

300+300=600

```

* * * * *

Q7. How will you count failed test cases using reduce()?

========================================================

### Answer:

Example:

```

let results = [

"Passed",

"Failed",

"Failed",

"Passed"

];

let failedCount = results.reduce((count,status)=>{

if(status==="Failed"){

count++;

}

return count;

},0);

console.log(failedCount);

```

Output:

```

2

```

* * * * *

Q8. How is forEach() different from a normal for loop?

======================================================

### Answer:

Both iterate arrays, but:

| for loop | forEach |

| --- | --- |

| More control | Less control |

| Can use break/continue | Cannot use break directly |

| Works with index easily | Callback based |

Example:

```

let browsers=[

"Chrome",

"Firefox",

"Edge"

];

browsers.forEach(browser=>{

console.log(browser);

});

```

* * * * *

Q9. Can we break a forEach() loop?

==================================

### Answer:

No.

`break` and `continue` cannot be directly used inside forEach().

Incorrect:

```

browsers.forEach(browser=>{

if(browser==="Firefox")

{

 break;

}

});

```

Error:

```

Illegal break statement

```

Alternative:

Use:

-   for loop

-   for...of loop

-   some()

Example:

```

for(let browser of browsers){

if(browser==="Firefox")

{

break;

}

}

```

* * * * *

Q10. Difference between map() and forEach() in terms of return value?

=====================================================================

### Answer:

Example:

```

let nums=[1,2,3];

let a = nums.forEach(num=>{

return num*2;

});

let b = nums.map(num=>{

return num*2;

});

```

Output:

```

a = undefined

b = [2,4,6]

```

Reason:

-   forEach ignores returned values.

-   map stores returned values into a new array.

* * * * *

Q11. How will you extract failed test names from an array of objects?

=====================================================================

### Answer:

Input:

```

[

{name:"Login",status:"Passed"},

{name:"Payment",status:"Failed"}

]

```

Solution:

```

let failedTests = tests

.filter(test=>test.status==="Failed")

.map(test=>test.name);

```

Output:

```

["Payment"]

```

* * * * *

Q12. Explain method chaining in array methods.

==============================================

### Answer:

Method chaining means using multiple array methods together.

Example:

```

let result = tests

.filter(test=>test.status==="Failed")

.map(test=>test.name);

```

Execution:

```

Array

 ↓

filter()

 ↓

map()

 ↓

Final Result

```

Used heavily in automation scripts.

* * * * *

Q13. Which array methods are commonly used in Playwright automation?

====================================================================

### Answer:

Most commonly:

1\.  `forEach()`

Used for performing actions on multiple values.

1\.  `map()`

Used for transforming extracted UI/API data.

1\.  `filter()`

Used for selecting required data.

1\.  `find()`

Used for finding specific test/user data.

1\.  `some()`

Used for checking existence.

1\.  `reduce()`

Used for calculations and grouping.

* * * * *

Q14. Difference between map() and filter()?

===========================================

### Answer:

| map() | filter() |

| --- | --- |

| Changes every element | Selects elements |

| Same array size usually | Size can decrease |

| Returns transformed array | Returns matching elements |

Example:

```

[1,2,3].map(x=>x*2)

Output:

[2,4,6]

[1,2,3].filter(x=>x>1)

Output:

[2,3]

```

* * * * *

Q15. Why are array iteration methods important for automation testers?

======================================================================

### Answer:

Because automation frameworks frequently handle collections:

Examples:

-   Multiple locators

-   API response arrays

-   Test data files

-   Browser lists

-   Test execution reports

-   User data

Methods like:

```

map()

filter()

forEach()

reduce()

```

help write cleaner, readable and maintainable automation code.
