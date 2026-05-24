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
