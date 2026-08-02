# Async / Await in TypeScript

## What is Synchronous Execution?

By default, JavaScript and TypeScript execute code **line by line**. The next statement runs only after the current one finishes.

### Example

```ts
console.log("A");
console.log("B");
console.log("C");
```

**Output**

```text
A
B
C
```

---

## What is Asynchronous Execution?

Some operations take time to complete, such as:

* API calls
* Database queries
* Reading files
* Timers (`setTimeout`)
* Playwright browser actions (`goto`, `click`, `fill`, etc.)

Instead of blocking the program, JavaScript starts these operations and continues executing the next lines.

### Example

```ts
console.log("Step 1");

setTimeout(() => {
    console.log("Step 2");
}, 2000);

console.log("Step 3");
```

**Output**

```text
Step 1
Step 3
Step 2
```

---

# Is JavaScript/TypeScript Synchronous or Asynchronous?

This is one of the most common interview questions.

**Answer:**

JavaScript and TypeScript are **synchronous languages by default**.

However, they can execute **asynchronous operations** using APIs such as:

* `setTimeout()`
* `fetch()`
* Promises
* Playwright methods (`goto()`, `click()`, `fill()`, etc.)

So:

```text
Language
↓

Synchronous by default

↓

Asynchronous only when async operations are used
```

---

# Why Do We Need async / await?

Asynchronous operations start in the background.

Without waiting, the next statement may execute before the previous operation finishes.

Example (Playwright)

```ts
page.goto("https://example.com");
page.click("#login");
```

Problem:

```text
goto() starts loading the page

↓

click() executes immediately

↓

Element may not exist yet

↓

Test may fail
```

Correct Way

```ts
await page.goto("https://example.com");
await page.click("#login");
```

Execution:

```text
Open page

↓

Wait until page loads

↓

Click Login
```

---

# What is async?

`async` marks a function as asynchronous.

It allows the use of `await` inside the function.

### Syntax

```ts
async function greet(){

}
```

or

```ts
const greet = async () => {

};
```

---

# Important Rule

An **async function always returns a Promise**, even if you return a normal value.

Example

```ts
async function getBrowser(){

    return "Chrome";
}
```

Actually returns:

```text
Promise<"Chrome">
```

---

# What is await?

`await` pauses execution until a Promise is completed.

### Syntax

```ts
let result = await someAsyncFunction();
```

Example

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

**Output**

```text
Chrome
```

---

# await Can Only Be Used Inside async

❌ Invalid

```ts
await getBrowser();
```

✅ Valid

```ts
async function main(){

    await getBrowser();
}
```

---

# async + await + try...catch

Errors from asynchronous operations should be handled using `try...catch`.

Example

```ts
async function login(username:string){

    if(username===""){

        throw new Error("Username cannot be empty");
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

---

# Simulating Delay

```ts
async function test(){

    console.log("Start");

    await new Promise(resolve=>{

        setTimeout(resolve,2000);

    });

    console.log("End");
}

test();
```

**Output**

```text
Start

(wait 2 seconds)

End
```

---

# Playwright Example

```ts
await page.goto("https://example.com");

await page.fill("#username","admin");

await page.fill("#password","admin123");

await page.click("#login");
```

Execution Flow

```text
Open Page

↓

Wait for page to load

↓

Fill Username

↓

Wait

↓

Fill Password

↓

Wait

↓

Click Login

↓

Wait
```

---

# When Should We Use await?

Use `await` only with asynchronous operations.

✅ Correct

```ts
await page.goto(...);

await page.click(...);

await fetch(...);

await getBrowser();

await new Promise(...);
```

❌ Unnecessary

```ts
await console.log("Hello");

await Math.max(10,20);

await "Chrome";

await 10+20;
```

These are synchronous operations and do not return Promises.

---

# Quick Memory Trick

```text
JavaScript / TypeScript

↓

Synchronous by default

↓

Async operation starts

↓

Use async + await

↓

Execution becomes sequential again
```

---

# Interview Questions

### Is JavaScript synchronous or asynchronous?

JavaScript is synchronous by default but supports asynchronous operations using Promises, async/await, timers, and browser APIs.

---

### Why do we use async?

To declare that a function performs asynchronous operations and to allow the use of `await`.

---

### Why do we use await?

To pause execution until a Promise is completed.

---

### Can await be used outside an async function?

No.

---

### What does an async function return?

An async function always returns a Promise.

---

### Why is await important in Playwright?

Without `await`, Playwright actions may execute before previous actions complete, causing flaky or failed tests.

---

### Can we write `await console.log()`?

Yes, but it has no benefit because `console.log()` is synchronous and does not return a Promise.

---

# Summary

| Keyword       | Purpose                                            |
| ------------- | -------------------------------------------------- |
| `async`       | Marks a function as asynchronous                   |
| `await`       | Waits until a Promise completes                    |
| `Promise`     | Represents the result of an asynchronous operation |
| `try...catch` | Handles errors from asynchronous code              |

---

# One-Line Revision

```text
JavaScript/TypeScript is synchronous by default.

Only asynchronous operations (API calls, timers, Playwright actions, Promises, etc.) require async/await.

async marks a function as asynchronous.

await waits for a Promise to finish before executing the next statement.

Playwright uses async/await to execute browser actions sequentially and reliably.
```
