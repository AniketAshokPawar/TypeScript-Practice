# Conditional Statements in TypeScript

Conditional statements are used to execute different blocks of code based on conditions.

---

# Types of Conditional Statements

1. if Statement  
2. if-else Statement  
3. Nested if-else Statement  
4. switch Case Statement  

---

# 1. if Statement

Used when code should execute only if condition is true.

---

## Syntax

```ts
if(condition){

    // code
}
```

---

## Example

```ts
let age = 20;

if(age >= 18){

    console.log("Eligible for Voting");
}
```

---

## Explanation

- Condition is checked
- If condition is `true`, code executes
- If condition is `false`, block is skipped

---

# 2. if-else Statement

Used when there are two possible outcomes.

---

## Syntax

```ts
if(condition){

    // true block
}
else{

    // false block
}
```

---

## Example

```ts
let number = 10;

if(number > 0){

    console.log("Positive Number");
}
else{

    console.log("Negative Number");
}
```

---

# 3. Nested if-else Statement

An `if-else` statement inside another `if` block.

Used for multiple condition checking.

---

## Example

```ts
let user = "Aniket";
let pwd = "Aniket123#";

if(user === "Aniket"){

    console.log("Correct Username");

    if(pwd === "Aniket123#"){

        console.log("Login Successful");
    }
    else{

        console.log("Incorrect Password");
    }
}
else{

    console.log("Incorrect Username");
}
```

---

## Explanation

- First username is checked
- If username is correct:
    - password is checked
- Otherwise:
    - invalid username message shown

---

# 4. switch Case Statement

Used when there are multiple fixed conditions.

Better alternative to multiple `if-else` statements.

---

## Syntax

```ts
switch(variable){

    case value1:
        // code
        break;

    case value2:
        // code
        break;

    default:
        // code
}
```

---

## Example

```ts
let day = 3;

switch(day){

    case 1:
        console.log("Monday");
        break;

    case 2:
        console.log("Tuesday");
        break;

    case 3:
        console.log("Wednesday");
        break;

    default:
        console.log("Invalid Day");
}
```

---

## Explanation

- switch checks variable value
- matching case executes
- `break` stops further execution
- `default` runs when no case matches

---

# Difference Between if-else and switch

| if-else | switch |
|---|---|
| Used for ranges and conditions | Used for fixed values |
| More flexible | Cleaner for multiple exact matches |
| Complex for many conditions | More readable for menus/options |

---

# Important Interview Points

- `if` executes only when condition is true
- `if-else` handles two outcomes
- Nested if-else is used for multiple validations
- `switch` is useful for fixed multiple choices
- `break` prevents fall-through in switch case
- `default` works like else block

---

# Best Practices

- Use `===` instead of `==`
- Keep conditions simple and readable
- Avoid deeply nested conditions when possible
- Always use `break` in switch cases
- Add `default` case in switch statements

---

# Conditional Statements in TypeScript - Interview Questions

---

## Q1. What are conditional statements in TypeScript?

### Answer:

Conditional statements are used to execute different blocks of code based on a condition.

Common conditional statements are:

- `if`
- `if-else`
- Nested `if-else`
- `switch`

---

### Interview Answer (Short)

> "Conditional statements help us make decisions in code based on whether a condition is true or false."

---

## Q2. What is the difference between `if` and `if-else`?

### Answer:

- `if` executes code only when the condition is true.
- `if-else` provides two possible outcomes: one for true and one for false.

Example:

```typescript
if(age >= 18){
    console.log("Eligible");
}
else{
    console.log("Not Eligible");
}
```

---

### Interview Answer (Short)

> "`if` is used when only the true condition matters, while `if-else` is used when we need separate actions for both true and false conditions."

---

## Q3. What is Nested if-else? When do you use it?

### Answer:

Nested `if-else` means placing one `if` statement inside another.

It is useful when multiple conditions must be checked one after another.

Example:

```typescript
if(username === "admin"){

    if(password === "admin123"){

        console.log("Login Successful");

    }

}
```

---

### Interview Answer (Short)

> "Nested if-else is used when one condition depends on another, such as validating username first and then password."

---

## Q4. What is a switch statement? When should you use it?

### Answer:

A `switch` statement is used when checking one variable against multiple fixed values.

Example:

```typescript
switch(browser){

    case "Chrome":
        break;

    case "Firefox":
        break;

    default:
        console.log("Unsupported Browser");
}
```

---

### Interview Answer (Short)

> "I use switch when there are multiple fixed options, such as browser names or environments."

---

## Q5. When would you choose `switch` instead of `if-else`?

### Answer:

Use:

- `switch` → Multiple fixed values
- `if-else` → Ranges or complex conditions

Example:

✅ Good for switch

```typescript
browser = "Chrome"
```

✅ Good for if-else

```typescript
age >= 18
```

---

### Interview Answer (Short)

> "I use switch for fixed values like browser names, and if-else for comparisons like greater than, less than, or multiple logical conditions."

---

## Q6. Why is `break` important in a switch statement?

### Answer:

`break` stops execution after the matching case.

Without `break`, execution continues to the next cases (called fall-through).

---

### Interview Answer (Short)

> "`break` prevents execution from continuing into other cases after a match is found."

---

## Q7. What is the purpose of the `default` case?

### Answer:

The `default` case executes when no case matches.

It works like the `else` block of an `if-else` statement.

---

### Interview Answer (Short)

> "`default` handles unexpected or unsupported values when none of the cases match."

---

## Q8. Where have you used conditional statements in your Playwright framework?

### Answer:

Common examples:

- Browser selection
- Environment selection
- Login validation
- Role-based validation
- Test execution conditions

Example:

```typescript
if(browser === "Chrome"){

    // Launch Chrome

}
```

---

### Interview Answer (Short)

> "I use conditional statements for browser selection, login validation, environment checks, and controlling test execution."

---

## Q9. What are some best practices when writing conditional statements?

### Answer:

- Prefer `===` over `==`
- Keep conditions simple and readable
- Avoid deeply nested `if` statements
- Always include `default` in `switch`
- Use `switch` only for fixed values

---

### Interview Answer (Short)

> "I keep conditions simple, use strict comparison (`===`), avoid unnecessary nesting, and always include a default case in switch."

---

## Q10. Can a switch statement replace every if-else statement?

### Answer:

No.

`switch` works only with fixed values.

Conditions like:

```typescript
if(age >= 18)
```

cannot be written using `switch`.

---

### Interview Answer (Short)

> "No. Switch is suitable only for fixed values. For range-based or logical conditions, if-else is the better choice."
