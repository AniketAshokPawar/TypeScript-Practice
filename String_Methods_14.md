# String Methods in TypeScript

A string is a sequence of characters enclosed in:
- Single quotes: `'Aniket'`
- Double quotes: `"Aniket"`
- Backticks: `` `Aniket` ``

```ts
let name: string = "Aniket";
```

---

## 1. length

Used to get the total number of characters in a string.

### Syntax

```ts
string.length
```

### Example

```ts
let name: string = "Aniket";

console.log(name.length);
```

**Output**

```text
6
```

---

## 2. indexOf()

Used to find the index position of a character or substring.

Returns:
- Index if found
- `-1` if not found

### Syntax

```ts
string.indexOf(value);
```

### Example

```ts
let name: string = "Aniket";

console.log(name.indexOf("k"));
```

**Output**

```text
3
```

---

## 3. charAt()

Used to get the character at a specific index.

### Syntax

```ts
string.charAt(index);
```

### Example

```ts
let name: string = "Aniket";

console.log(name.charAt(2));
```

**Output**

```text
i
```

---

## 4. substring()

Used to extract part of a string.

### Syntax

```ts
string.substring(start, end);
```

### Example

```ts
let text: string = "Automation";

console.log(text.substring(0, 4));
```

**Output**

```text
Auto
```

---

## 5. toUpperCase()

Converts a string to uppercase.

### Syntax

```ts
string.toUpperCase();
```

### Example

```ts
let name: string = "aniket";

console.log(name.toUpperCase());
```

**Output**

```text
ANIKET
```

---

## 6. toLowerCase()

Converts a string to lowercase.

### Syntax

```ts
string.toLowerCase();
```

### Example

```ts
let name: string = "ANIKET";

console.log(name.toLowerCase());
```

**Output**

```text
aniket
```

---

## 7. includes()

Checks whether a string contains specified text.

### Syntax

```ts
string.includes(value);
```

### Example

```ts
let text: string = "Automation Testing";

console.log(text.includes("Testing"));
```

**Output**

```text
true
```

---

## 8. startsWith()

Checks whether a string starts with specified text.

### Syntax

```ts
string.startsWith(value);
```

### Example

```ts
let text: string = "Playwright";

console.log(text.startsWith("Play"));
```

**Output**

```text
true
```

---

## 9. endsWith()

Checks whether a string ends with specified text.

### Syntax

```ts
string.endsWith(value);
```

### Example

```ts
let text: string = "Playwright";

console.log(text.endsWith("right"));
```

**Output**

```text
true
```

---

## 10. replace()

Used to replace text in a string.

### Syntax

```ts
string.replace(oldValue, newValue);
```

### Example

```ts
let text: string = "Hello Aniket";

console.log(text.replace("Aniket", "Rahul"));
```

**Output**

```text
Hello Rahul
```

---

## 11. split()

Converts a string into an array.

### Syntax

```ts
string.split(separator);
```

### Example

```ts
let text: string = "Apple,Banana,Mango";

console.log(text.split(","));
```

**Output**

```text
["Apple", "Banana", "Mango"]
```

---

## 12. trim()

Removes spaces from both beginning and end.

### Syntax

```ts
string.trim();
```

### Example

```ts
let text: string = "   Aniket   ";

console.log(text.trim());
```

**Output**

```text
Aniket
```

---

## 13. trimStart()

Removes spaces from the beginning only.

### Syntax

```ts
string.trimStart();
```

### Example

```ts
let text: string = "   Aniket";

console.log(text.trimStart());
```

**Output**

```text
Aniket
```

---

## 14. trimEnd()

Removes spaces from the end only.

### Syntax

```ts
string.trimEnd();
```

### Example

```ts
let text: string = "Aniket   ";

console.log(text.trimEnd());
```

**Output**

```text
Aniket
```

---

## 15. concat()

Used to join two or more strings.

### Syntax

```ts
string1.concat(string2);
```

### Example

```ts
let fname: string = "Aniket";
let lname: string = " Pawar";

console.log(fname.concat(lname));
```

**Output**

```text
Aniket Pawar
```

---

# Quick Revision Table

| Method | Purpose | Return Type |
|----------|----------|----------|
| length | Count characters | number |
| indexOf() | Find index position | number |
| charAt() | Get character at index | string |
| substring() | Extract part of string | string |
| toUpperCase() | Convert to uppercase | string |
| toLowerCase() | Convert to lowercase | string |
| includes() | Check existence | boolean |
| startsWith() | Check starting text | boolean |
| endsWith() | Check ending text | boolean |
| replace() | Replace text | string |
| split() | Convert string to array | string[] |
| trim() | Remove spaces from both sides | string |
| trimStart() | Remove spaces from start | string |
| trimEnd() | Remove spaces from end | string |
| concat() | Join strings | string |

---

# Interview Notes

- Strings are immutable (original string does not change).
- Most string methods return a new string.
- `indexOf()` returns `-1` when the value is not found.
- `includes()`, `startsWith()`, and `endsWith()` return boolean values.
- `split()` converts a string into an array.
- `trim()`, `trimStart()`, and `trimEnd()` are useful when handling user input.
- String methods are frequently used in Playwright for text validation and assertions.

---

```
# String Methods in TypeScript - Interview VVIP Questions & Answers

These are commonly asked string-related interview questions for
0--2.5 years Automation Tester / SDET candidates.

Focus areas:
- String manipulation
- Test data handling
- API response validation
- Playwright automation scenarios

---
* * * * *

# Q1. What is the difference between substring() and slice()?

## Answer

Both are used to extract parts of a string.

### substring()

- Does not support negative indexes
- If start index is greater than end index, it swaps them

Example:

```ts
let text = "Automation";

console.log(text.substring(5,2));
```

Output:

```
oma
```

Because:

```
substring(2,5)
```

is internally considered.

* * * * *

### slice()

-   Supports negative indexes
-   Does not swap indexes

Example:

```
let text = "Automation";

console.log(text.slice(-3));
```

Output:

```
ion
```

* * * * *

Q2. What happens when indexOf() does not find a value?
======================================================

Answer
------

`indexOf()` returns `-1`.

Example:

```
let browser = "Chrome";

console.log(browser.indexOf("Firefox"));
```

Output:

```
-1
```

* * * * *

Q3. Difference between includes() and indexOf()
===============================================

Answer
------

Both check whether a value exists.

### includes()

Returns boolean:

```
true / false
```

Example:

```
let text = "Playwright";

console.log(text.includes("wright"));
```

Output:

```
true
```

* * * * *

### indexOf()

Returns position:

```
let text = "Playwright";

console.log(text.indexOf("wright"));
```

Output:

```
5
```

* * * * *

Q4. Why are strings called immutable in JavaScript/TypeScript?
==============================================================

Answer
------

Strings cannot be modified directly.

Any string operation creates a new string.

Example:

```
let name = "aniket";

name.toUpperCase();

console.log(name);
```

Output:

```
aniket
```

Correct way:

```
name = name.toUpperCase();

console.log(name);
```

Output:

```
ANIKET
```

* * * * *

Q5. How do you reverse a string?
================================

Answer
------

Using split(), reverse(), and join().

Example:

```
let text = "Playwright";

let reverse = text.split("")
                  .reverse()
                  .join("");

console.log(reverse);
```

Output:

```
thgirwylP
```

* * * * *

Q6. How do you check whether a string is palindrome?
====================================================

Answer
------

Compare original string with reversed string.

Example:

```
let text = "madam";

let reverse = text.split("")
                  .reverse()
                  .join("");

if(text === reverse){

    console.log("Palindrome");

}
else{

    console.log("Not Palindrome");

}
```

Output:

```
Palindrome
```

* * * * *

Q7. How do you remove duplicate characters from a string?
=========================================================

Answer
------

Convert string into array and use Set.

Example:

```
let text = "automation";

let result = [...new Set(text)];

console.log(result.join(""));
```

Output:

```
automn
```

* * * * *

Q8. How do you count occurrence of a character in a string?
===========================================================

Answer
------

Example:

```
let text = "automation";

let count = 0;

for(let char of text){

    if(char === "o"){

        count++;

    }
}

console.log(count);
```

Output:

```
2
```

* * * * *

Q9. How do you extract username from email?
===========================================

Answer
------

Using indexOf() and substring().

Example:

```
let email = "aniket@gmail.com";

let username = email.substring(
    0,
    email.indexOf("@")
);

console.log(username);
```

Output:

```
aniket
```

* * * * *

Q10. How do you validate API response message contains expected text?
=====================================================================

Answer
------

Using includes().

Example:

```
let response = "User created successfully";

if(response.includes("successfully")){

    console.log("Validation Passed");

}
```

Output:

```
Validation Passed
```

* * * * *

Q11. Difference between replace() and replaceAll()
==================================================

Answer
------

### replace()

Replaces only first occurrence.

Example:

```
let text = "test test";

console.log(text.replace("test","pass"));
```

Output:

```
pass test
```

* * * * *

### replaceAll()

Replaces all occurrences.

Example:

```
let text = "test test";

console.log(text.replaceAll("test","pass"));
```

Output:

```
pass pass
```

* * * * *

Q12. How do you convert a string into an array?
===============================================

Answer
------

Using split().

Example:

```
let browsers = "Chrome,Firefox,Edge";

let arr = browsers.split(",");

console.log(arr);
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

Q13. How do you remove spaces from user input?
==============================================

Answer
------

Using trim().

Example:

```
let username = "   admin   ";

console.log(username.trim());
```

Output:

```
admin
```

* * * * *

Q14. Difference between trim(), trimStart(), and trimEnd()
==========================================================

Answer
------

| Method | Purpose |
| --- | --- |
| trim() | Removes spaces from both sides |
| trimStart() | Removes spaces from beginning |
| trimEnd() | Removes spaces from end |

Example:

```
let text = "  Aniket  ";

console.log(text.trim());
```

Output:

```
Aniket
```

* * * * *

Q15. Real Playwright Scenario
=============================

Question
--------

How will you validate that a button text contains expected value?

Example:

```
let actualText = "Submit Order";
```

Expected:

```
Submit
```

Answer
------

```
if(actualText.includes("Submit")){

    console.log("Text validation passed");

}
else{

    console.log("Text validation failed");

}
```
