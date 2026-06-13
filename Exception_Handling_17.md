# Exception Handling in TypeScript

Exception Handling is used to handle runtime errors gracefully without stopping the program abruptly.

Benefits:
- Prevents application crashes
- Handles unexpected situations
- Displays meaningful error messages
- Allows program execution to continue

---

# What is an Exception?

An exception is an error that occurs during program execution.

Example:

```ts
let num = 10;

console.log(num.toUpperCase());
```

Output:

```text
TypeError: num.toUpperCase is not a function
```

---

# Exception Handling Keywords

```text
try
catch
finally
throw
```

---

# 1. try Block

The `try` block contains code that may generate an error.

## Syntax

```ts
try{

    // risky code
}
```

## Example

```ts
try{

    let num:number = 10;

    console.log(num.toUpperCase());
}
```

---

# 2. catch Block

The `catch` block handles errors generated inside the `try` block.

## Syntax

```ts
try{

    // code
}
catch(error){

    // handle error
}
```

## Example

```ts
try{

    let num:number = 10;

    console.log(num.toUpperCase());
}
catch(error){

    console.log("Error Handled");
}
```

Output:

```text
Error Handled
```

---

# Why Use catch?

Without catch:

```ts
let num:number = 10;

console.log(num.toUpperCase());

console.log("Program End");
```

Program stops due to error.

With catch:

```ts
try{

    let num:number = 10;

    console.log(num.toUpperCase());
}
catch(error){

    console.log("Error Handled");
}

console.log("Program End");
```

Output:

```text
Error Handled
Program End
```

---

# Error Object

The `catch` block receives an error object.

Example:

```ts
try{

    let num:number = 10;

    console.log(num.toUpperCase());
}
catch(error){

    console.log(error);
}
```

Output:

```text
TypeError: num.toUpperCase is not a function
```

---

# 3. finally Block

The `finally` block always executes.

It runs whether:
- Error occurs
- No error occurs

## Syntax

```ts
try{

}
catch(error){

}
finally{

}
```

## Example

```ts
try{

    console.log("Executing");
}
catch(error){

    console.log("Error");
}
finally{

    console.log("Execution Completed");
}
```

Output:

```text
Executing
Execution Completed
```

---

# Example with Error

```ts
try{

    let num:number = 10;

    console.log(num.toUpperCase());
}
catch(error){

    console.log("Error Handled");
}
finally{

    console.log("Execution Completed");
}
```

Output:

```text
Error Handled
Execution Completed
```

---

# Why Use finally?

Common Uses:
- Close browser
- Close file
- Close database connection
- Cleanup resources

Automation Example:

```ts
finally{

    await browser.close();
}
```

Even if test execution fails, the browser will close.

---

# 4. throw Keyword

The `throw` keyword is used to create custom errors.

## Syntax

```ts
throw new Error("message");
```

## Example

```ts
let age = -5;

if(age < 0){

    throw new Error("Age cannot be negative");
}
```

Output:

```text
Error: Age cannot be negative
```

---

# Example with try-catch

```ts
try{

    let age = -5;

    if(age < 0){

        throw new Error("Age cannot be negative");
    }

    console.log(age);
}
catch(error){

    console.log(error);
}
```

Output:

```text
Error: Age cannot be negative
```

---

# Important Point About throw

`throw` does not print anything by itself.

Example:

```ts
throw new Error("Invalid Age");
```

This only creates and throws the error.

To see the message:

```ts
catch(error){

    console.log(error);
}
```

or

```ts
catch(error:any){

    console.log(error.message);
}
```

---

# Real Interview Example

```ts
function login(username:string){

    if(username === ""){

        throw new Error("Username cannot be empty");
    }

    console.log("Login Successful");
}

try{

    login("");
}
catch(error){

    console.log(error);
}
```

Output:

```text
Error: Username cannot be empty
```

---

# Complete Example

```ts
try{

    let age = -10;

    if(age < 0){

        throw new Error("Invalid Age");
    }

    console.log(age);
}
catch(error){

    console.log(error);
}
finally{

    console.log("Execution Completed");
}
```

Output:

```text
Error: Invalid Age
Execution Completed
```

---

# Interview Questions

## What is Exception Handling?

Exception Handling is a mechanism used to handle runtime errors and prevent application crashes.

---

## What is the purpose of try?

`try` contains code that may generate an exception.

---

## What is the purpose of catch?

`catch` handles exceptions generated in the `try` block.

---

## What is the purpose of finally?

`finally` always executes regardless of whether an exception occurs.

---

## What is the purpose of throw?

`throw` is used to create custom exceptions.

---

# Summary

| Keyword | Purpose |
|----------|----------|
| try | Contains risky code |
| catch | Handles errors |
| finally | Always executes |
| throw | Creates custom error |

---

# Important Interview Points

```text
try → Contains risky code

catch → Handles errors

finally → Always executes

throw → Creates custom error

Program continues after catch

finally executes even if no error occurs

throw does not print error messages directly

catch(error) receives the thrown error
```
