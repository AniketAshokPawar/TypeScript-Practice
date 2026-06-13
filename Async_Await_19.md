# Async / Await in TypeScript

Async/Await is used to handle asynchronous operations in a simple and readable way.

Common asynchronous operations:
- API Calls
- Database Queries
- File Reading
- Browser Actions (Playwright)
- Waiting for Elements

---

# Synchronous Execution

Code executes line by line.

Example:

```ts
console.log("A");
console.log("B");
console.log("C");
```

Output:

```text
A
B
C
```

---

# Asynchronous Execution

Some operations take time to complete.

Example:

```ts
console.log("Step 1");

setTimeout(() => {
    console.log("Step 2");
}, 3000);

console.log("Step 3");
```

Output:

```text
Step 1
Step 3
Step 2
```

Explanation:
- JavaScript does not wait for `setTimeout()`
- It continues executing the next line

---

# What is async?

The `async` keyword is used before a function.

It tells TypeScript:

```text
This function may contain asynchronous operations.
```

## Syntax

```ts
async function functionName(){

}
```

or

```ts
let functionName = async () => {

}
```

---

# Example

```ts
async function greet(){

    console.log("Hello");
}

greet();
```

Output:

```text
Hello
```

---

# Important Rule

An async function always returns a Promise.

Example:

```ts
async function greet(){

    return "Hello";
}
```

Actually returns:

```text
Promise { "Hello" }
```

---

# What is await?

The `await` keyword tells JavaScript:

```text
Wait until the asynchronous operation finishes.
```

---

# Syntax

```ts
await someAsyncOperation();
```

---

# Rule

`await` can only be used inside an async function.

❌ Invalid

```ts
await getUser();
```

✅ Valid

```ts
async function main(){

    await getUser();
}
```

---

# Example

```ts
async function getUser(){

    return "Admin";
}

async function main(){

    let user = await getUser();

    console.log(user);
}

main();
```

Output:

```text
Admin
```

---

# Returning a Value

```ts
async function getBrowser(){

    return "Chrome";
}

async function main(){

    let browser = await getBrowser();

    console.log(browser);
}

main();
```

Output:

```text
Chrome
```

---

# Returning Numbers

```ts
async function add(num1:number, num2:number){

    return num1 + num2;
}

async function main(){

    let result = await add(10,20);

    console.log(result);
}

main();
```

Output:

```text
30
```

---

# async + await + try-catch

Used to handle errors in asynchronous code.

Example:

```ts
async function login(username:string){

    if(username === ""){
        throw new Error("Username Required");
    }

    return "Login Successful";
}

async function main(){

    try{

        let result = await login("");

        console.log(result);
    }
    catch(error){

        console.log(error);
    }
}

main();
```

Output:

```text
Error: Username Required
```

---

# Playwright Example

```ts
await page.goto("https://google.com");

await page.fill("#username","admin");

await page.click("#login");
```

Execution:

```text
Open page
Wait for page load

Fill username
Wait for completion

Click login
Wait for completion
```

---

# Why Use await in Playwright?

Without await:

```ts
page.goto("https://google.com");

page.click("#login");
```

Problem:

```text
Page may still be loading

Click executes too early

Test may fail
```

---

# Correct Way

```ts
await page.goto("https://google.com");

await page.click("#login");
```

Execution:

```text
Open page

Wait for page load

Click login
```

---

# Multiple await Example

```ts
async function test(){

    console.log("Step 1");

    await new Promise(resolve => {

        setTimeout(resolve, 2000);
    });

    console.log("Step 2");
}

test();
```

Output:

```text
Step 1

(wait 2 seconds)

Step 2
```

---

# Interview Questions

## What is async?

`async` marks a function as asynchronous and allows the use of `await` inside it.

---

## What is await?

`await` pauses execution until a Promise is completed.

---

## Can await be used outside an async function?

No.

Invalid:

```ts
await getUser();
```

Valid:

```ts
async function main(){

    await getUser();
}
```

---

## What does an async function return?

An async function always returns a Promise.

---

## Why is await used in Playwright?

To ensure browser actions complete before moving to the next step.

Example:

```ts
await page.goto();
await page.click();
await page.fill();
```

---

# Summary

| Keyword | Purpose |
|----------|----------|
| async | Marks a function as asynchronous |
| await | Waits for async operation to complete |

---

# Important Interview Points

```text
async function always returns a Promise

await can only be used inside async functions

await waits for completion before moving to next line

Playwright heavily uses async/await

Without await, actions may execute too early

async/await makes code easier to read
```
