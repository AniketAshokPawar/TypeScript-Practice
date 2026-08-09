###   Q.1 What is TypeScript, and why is it preferred over JavaScript for automation testing?

**TypeScript is a statically typed superset of JavaScript.** It adds features such as type checking, interfaces, access modifiers, and other features on top of JavaScript. TypeScript code is ultimately compiled/transpiled into JavaScript.

For automation testing, especially with frameworks like **Playwright**, TypeScript is preferred because it makes the automation framework more reliable, maintainable, and easier to refactor.

**1\. Type Safety**

TypeScript allows us to specify the expected type of variables, parameters, properties, and return values.

```
function login(username: string, password: string) {
    // ...
}

login("admin", 12345); // TypeScript error

```

Here, TypeScript identifies the problem during development because `password` is expected to be a `string`, but a `number` was passed.

In JavaScript, this type error is generally not caught before execution.

**2\. Better IntelliSense / Autocompletion**

Because TypeScript knows the types of objects, the IDE can provide more accurate suggestions.

For example, in Playwright:

```
const page: Page;

```

When we type:

```
page.

```

VS Code knows that `page` is a Playwright `Page` object and can suggest methods such as:

```
goto()
click()
fill()
locator()
getByRole()
screenshot()

```

JavaScript can also provide IntelliSense through inference and library information, but TypeScript provides explicit type information, making the suggestions more reliable.

**3\. Easier Refactoring**

Suppose a Page Object method is used by many tests.

Initially:

```
login(username: string, password: string)

```

Later, we change it to:

```
login(credentials: LoginCredentials)

```

If old tests still call:

```
login("admin", "admin123");

```

TypeScript can immediately highlight the incompatible usage with a red squiggly line and show the error in the Problems panel.

This helps us find affected code before running the complete test suite.

**4\. Better Maintainability**

In a large automation framework, we may have:

```
tests/
pages/
fixtures/
utils/
test-data/

```

Many classes and tests interact with each other.

TypeScript makes the expected structure and types explicit, so developers can understand how different parts of the framework should interact and can detect many incorrect usages during development.

**5\. Better Playwright Support**

Playwright provides TypeScript types such as:

```
Page
Locator
Browser
BrowserContext

```

For example:

```
import { Page, Locator } from "@playwright/test";

class LoginPage {

    readonly page: Page;
    readonly username: Locator;

    constructor(page: Page) {
        this.page = page;
        this.username = page.locator("#username");
    }
}

```

Because TypeScript knows that `page` is a `Page` and `username` is a `Locator`, we get better type checking and IntelliSense while developing Page Objects.

### Short interview conclusion

**"TypeScript is a statically typed superset of JavaScript. It is preferred for automation testing because type checking catches many errors during development, provides better IntelliSense, makes large frameworks easier to maintain and refactor, and works very well with Playwright's built-in types such as Page and Locator."**

###  Q.2 WHAT IS THE DIFFERENCE BETWEEN `any`, `unknown`, AND `never` IN TYPESCRIPT?

`any`, `unknown`, and `never` are three special TypeScript types, but they have different purposes.

**1\. `any`**

`any` means that TypeScript will not perform type checking for that value.


Example:

```
let value: any = 10;

value = "Hello";

value = true;

```

All of these are allowed.

We can also perform any operation on an `any` value without TypeScript giving a compile-time error.

Example:
```
let value: any = 10;

console.log(value.toUpperCase());
```

TypeScript allows this because `value` is of type `any`.

However, when the code runs, it will fail because `toUpperCase()` is a string method and the actual value is a number.

This is why `any` can lead to runtime errors and should generally be avoided when possible.

In automation, for example:

let responseData: any = await response.json();

console.log(responseData.user.name);

TypeScript will not complain even if the API response does not contain a `user` property.

Therefore, `any` provides flexibility but removes type safety.

**2\. `unknown`**

`unknown` means that a value exists, but its type is not known yet.

Example:
```
let value: unknown = "Hello";
```
We cannot directly perform operations on an `unknown` value.

For example:
```
console.log(value.toUpperCase());
```
TypeScript gives an error because it does not know whether `value` is actually a string.

We first need to check the type:

```if (typeof value === "string") {

    console.log(value.toUpperCase());

}
```
After checking the type, TypeScript knows that `value` is a string and allows string-specific operations.

This is called type narrowing.

The main advantage of `unknown` is that it is safer than `any`.

With `any`, TypeScript trusts us and allows operations directly.

With `unknown`, TypeScript requires us to verify the type before using the value.

For example, when handling dynamic or external data such as API responses, `unknown` can be safer than `any`.

Example:
```
const responseData: unknown = await response.json();
```

**3\. `never`**

`never` is different from both `any` and `unknown`.

`never` represents a situation where a value can never be produced.

It is commonly used as the return type of functions that never complete normally.

For example, a function that always throws an error:
```
function loginError(message: string): never {

    throw new Error(message);

}
```

This function always throws an error, so it never reaches a normal return statement.

Another example is a function with an infinite loop:

```
function runForever(): never {

    while (true) {

        console.log("Running...");

    }

}
```

This function never finishes normally, so it never returns a value.

Therefore, `never` is used when a function cannot successfully return a value.

**4\. `void` vs `never`**

This is an important interview difference.

`void` means that a function completes normally but does not return a useful value.

Example:

```
function printMessage(): void {

    console.log("Hello");

}
```

The function executes, finishes, and returns nothing.

`never` means that the function does not complete normally.

Example:

```
function throwError(): never {

    throw new Error("Something went wrong");

}
```

The function throws an error and never reaches a normal return.

So:

`void` means the function finishes without returning a value.

`never` means the function never completes normally and therefore never returns a value.

**5\. Main Difference**

`any`:

Type checking is disabled. It can contain any value, and we can perform operations on it without TypeScript checking whether those operations are valid.

`unknown`:

The value can be of any type, but the type is not known yet. We must check or narrow the type before performing operations.

`never`:

Represents a situation where a value can never be produced. It is commonly used for functions that always throw an error or never finish normally.

**6\. Easy Way to Remember**

`any`:

"I don't care about the type."

`unknown`:

"I don't know the type yet, so check it first."

`never`:

"There will never be a value."

**INTERVIEW ANSWER**

`any`, `unknown`, and `never` have different purposes in TypeScript. `any` disables type checking and allows us to perform operations without TypeScript complaining, so it should generally be avoided. `unknown` can hold a value of any type, but we need to check or narrow its type before performing operations, which makes it safer than `any`. `never` represents a situation where a value can never be produced and is commonly used as the return type of functions that never complete normally, such as functions that always throw an error or run indefinitely.


### Q.3 What is Type Inference in TypeScript?
-------------------------------------

**Type Inference** means TypeScript can **automatically determine the type of a variable based on the value assigned to it**, so we don't always need to explicitly specify the type.

### Simple Example

```
let name = "Aniket";
let age = 27;
let isTester = true;
```

We did not explicitly write the types:

```
let name: string
let age: number
let isTester: boolean
```

But TypeScript automatically understands:

```
name     → string
age      → number
isTester → boolean
```

This is called **Type Inference**.

For example:

```
let age = 27;

age = "Aniket";  // ❌ TypeScript error
```

Why?

Because TypeScript inferred `age` as a `number` from the initial value `27`.

### Explicit Type vs Type Inference

Explicit type:

```
let age: number = 27;
```

Here, **we tell TypeScript** that `age` is a number.

Type inference:

```
let age = 27;
```

Here, **TypeScript automatically determines** that `age` is a number.

### Interview Answer

> **Type inference is a TypeScript feature where TypeScript automatically determines the type of a variable based on its assigned value. This means we don't always need to explicitly specify the type.**

### Easy way to remember

**Explicit typing:**\
Developer tells TypeScript the type.

**Type inference:**\
TypeScript figures out the type automatically.

### Q.4 What is the difference between interface and type alias?

`interface`
-----------

An `interface` is mainly used to define the **structure of an object**.

Example:

```
interface User {
    name: string;
    age: number;
}

const user: User = {
    name: "Aniket",
    age: 27
};
```

Here, `User` defines what properties a user object should have.

* * * * *

`type` alias
------------

A `type` alias can also define an object structure.

```
type User = {
    name: string;
    age: number;
};

const user: User = {
    name: "Aniket",
    age: 27
};
```

So for a simple object, **both work almost the same way**.

* * * * *

Main Difference
---------------

The important difference is that `type` can represent **more than just object structures**.

For example:

```
type ID = string | number;
```

This means `ID` can be either a string or a number.

You can also create tuples, unions, intersections, etc. using `type`.

```
type Status = "Pass" | "Fail";
```

An `interface` is primarily designed for defining object/class structures.

### Q.5 What are Union Types and Intersection Types?
--------------------------------------------

Both are used when we want a variable or object to have **multiple types**, but they work differently.

### 1\. Union Type (`|`)

A **Union Type** means a value can be **one of multiple types**.

We use the `|` symbol.

Example:

```
let userId: string | number;

userId = "A101";  // ✅
userId = 101;     // ✅
```

Here, `userId` can be **either a string or a number**.

Think:

> **Union = OR**

### 2\. Intersection Type (`&`)

An **Intersection Type** combines multiple types into **one type**.

We use the `&` symbol.

Example:

```
type Person = {
    name: string;
};

type Employee = {
    employeeId: number;
};

type EmployeeDetails = Person & Employee;
```

Now `EmployeeDetails` must contain **both** `name` and `employeeId`.

```
const employee: EmployeeDetails = {
    name: "Aniket",
    employeeId: 101
};
```

If we omit either property, TypeScript gives an error.

Think:

> **Intersection = AND**

### Q.6 What is Type Assertion (`as`) in TypeScript?
--------------------------------------------

**Type Assertion** is used when we want to tell TypeScript:

> "I know the type of this value better than you do."

We use the `as` keyword.

### Simple Example

```
let value: unknown = "Hello";

let message = value as string;

console.log(message.toUpperCase());
```

Here, TypeScript initially sees:

```
value → unknown
```

We know that the actual value is a string, so we tell TypeScript:

```
value as string
```

Now TypeScript treats `message` as a `string`, so `toUpperCase()` is allowed.

### Important Point

Type assertion **does not change the actual value or convert its type**.

For example:

```
let value: unknown = 100;

let message = value as string;
```

This does NOT convert `100` into `"100"`.

It only tells TypeScript to **treat the value as a string during type checking**.

So remember:

**Type Assertion (`as`) → "I know what the type is; trust me."**

### Type Assertion vs Type Checking

Type assertion:

```
const value = data as string;
```

We are telling TypeScript what we believe the type is.

Type checking:

```
if (typeof data === "string") {
    console.log(data.toUpperCase());
}
```

Here, we actually check the type at runtime.

### Interview Answer

> **Type assertion in TypeScript is a way of telling the compiler to treat a value as a specific type using the `as` keyword. It is useful when we know more about the type than TypeScript does. However, type assertion does not perform type conversion or change the actual value.**

### Q.7 WHAT IS THE DIFFERENCE BETWEEN `null` AND `undefined`?

`undefined` means a variable has been declared but no value has been assigned to it.

Example:

let age;

console.log(age);  // undefined

`null` means we intentionally assign "no value" to a variable.

Example:

let age: number | null = null;

console.log(age);  // null

Simple difference:

`undefined` → No value assigned yet.

`null` → Intentionally no value.

***INTERVIEW ANSWER:***

`undefined` means a value has not been assigned, while `null` is an explicitly assigned value that represents "no value."

### Q. 8 What does an `async` function return? What is a Promise and how is it related to `async/await`?

### 1\. Start with a normal function

Suppose we have:

```
function login() {
    console.log("Login successful");
}

login();
```

This is simple. The function runs and finishes.

Now imagine that login involves sending a request to a server. We **don't get the result immediately** because the server needs some time to respond.

That's where `Promise` comes in.

### 2\. A function that performs an asynchronous operation

For example:

```
async function login() {
    const response = await fetch("https://example.com/login");

    console.log("Login response received");
}
```

Here we have two important keywords:

-   `async`
-   `await`

Let's understand what each one is doing.

### 3\. What does `async` do?

When we write:

```
async function login() {
    ...
}
```

we are telling JavaScript:

> "This function is going to perform asynchronous work."

Most importantly, an `async` function **always returns a Promise**.

For example:

```
async function getName() {
    return "Aniket";
}
```

Even though we wrote:

```
return "Aniket";
```

the function doesn't actually return just `"Aniket"`.

It returns a:

```
Promise
```

which will eventually contain `"Aniket"`.

You can see this with:

```
const result = getName();

console.log(result);
```

You will see a Promise rather than simply `"Aniket"`.

### 4\. So what is a Promise actually?

Think about ordering food at a restaurant.

You order food.

The waiter doesn't immediately give you the food.

Instead, you get something like:

> "Your order has been accepted. We will give you the food when it is ready."

That is similar to a **Promise**.

The Promise is basically an object representing the **status/result of an operation that is currently being processed**.

For example:

```
const result = fetch("https://example.com");
```

`fetch()` needs to communicate with the server.

At the moment you call `fetch()`, the response may not have arrived yet.

So `fetch()` gives you a **Promise**.

### 5\. Now the three Promise states make sense

When you call:

```
const result = fetch("https://example.com");
```

initially, the request is still being processed.

That Promise is:

**Pending**

Meaning:

> "The server hasn't given us the result yet."

If the server responds successfully:

**Fulfilled**

Meaning:

> "The operation completed successfully, and here is the result."

If something goes wrong, such as a network failure:

**Rejected**

Meaning:

> "The operation failed."

So you can think:

```
fetch() called
    ↓
Pending
    ↓
Server responds successfully → Fulfilled
    OR
Something goes wrong → Rejected
```

You don't manually decide whether it's pending or fulfilled. **JavaScript/Promise machinery tracks the state based on what happens with the asynchronous operation.**

### 6\. Now where does `await` come in?

Suppose:

```
async function getData() {
    const response = await fetch("https://example.com");

    console.log("Response received");
}
```

Here:

```
fetch("https://example.com")
```

returns a Promise.

`await` tells JavaScript:

> "Wait here until this Promise is completed, then give me the actual result."

So:

```
const response = await fetch("https://example.com");
```

means:

> Start the request → wait for its Promise to complete → store the actual response in `response`.

That's why we don't have to manually deal with the Promise result in most cases.

### 7\. What if the Promise fails?

For example:

```
async function getData() {
    try {
        const response = await fetch("https://example.com");

        console.log(response);
    }
    catch (error) {
        console.log("Request failed");
    }
}
```

If the request succeeds, `await` gives us the response.

If the Promise is rejected, the `await` expression throws an error, which we can handle using `try/catch`.

### 8\. Now connect this to Playwright

This is exactly why you see `async/await` everywhere in Playwright.

For example:

```
test("Login", async ({ page }) => {

    await page.goto("https://example.com");

    await page.locator("#username").fill("admin");

    await page.locator("#password").fill("admin123");

    await page.locator("#loginBtn").click();

});
```

Methods such as:

```
page.goto()
page.fill()
page.click()
```

perform asynchronous operations and return Promises.

So we use:

```
await page.goto(...)
```

to wait for that operation to complete before moving to the next statement.

And because we use `await`, the test function itself is written as:

```
async ({ page }) => {
```

### The interview explanation I'd recommend you give

Don't start with a textbook definition. Explain it like this:

> **"In JavaScript and Playwright, many operations are asynchronous. For example, when we call `page.goto()` or `fetch()`, the operation takes some time to complete, so the method returns a Promise. A Promise represents the current result of that operation. Initially, it is pending while the operation is running. If the operation completes successfully, it becomes fulfilled, and if it fails, it becomes rejected.**
>
> **To work with the Promise easily, we use `async/await`. We mark the function as `async`, and inside it we use `await` before a Promise. `await` waits for that asynchronous operation to complete and gives us the actual result. An `async` function itself always returns a Promise."**

### Q.9 What is optional chaining (`?.`)?
Optional chaining (`?.`) is used when we want to access a property or call a method **without getting an error if the value before it is `null` or `undefined`**.

### Simple example

Suppose:

```
let user = {
    name: "Aniket"
};

console.log(user.address.city);
```

This will cause a runtime error because `address` doesn't exist.

Instead, we can write:

```
console.log(user.address?.city);
```

Now, if `address` is `undefined` or `null`, the result is simply `undefined` instead of throwing an error.

### Q.10 What is Nullish Coalescing (`??`)?

`??` is used when we want to provide a **default value if the value is `null` or `undefined`**.

### Simple example

```
let username: string | null = null;

let name = username ?? "Guest";

console.log(name);
```

Output:

```
Guest
```

Because `username` is `null`, `"Guest"` is used.

### Q. 11 What is the difference between `??` and `||`?

The easiest difference is:

**`??` checks only `null` and `undefined`.**

**`||` checks whether the value is falsy.**

### Simple example

```
let age = 0;

console.log(age ?? 18);  // 0
console.log(age || 18);  // 18
```

Why?

With `??`:

```
0 is not null
0 is not undefined
```

So it keeps `0`.

With `||`:

```
0 is a falsy value
```

So it uses `18`.

### What values does `||` consider falsy?

Common ones are:

```
false
0
""
null
undefined
NaN
```

But `??` only cares about:

```
null
undefined
```

### Another example

```
let name = "";

console.log(name ?? "Guest");  // ""
console.log(name || "Guest");  // "Guest"
```

The empty string is a valid value, so `??` keeps it, while `||` replaces it.

### Easy way to remember

**`??` → "Is it null or undefined?"**

**`||` → "Is it falsy?"**

### Interview Answer

> **The main difference is that `??` returns the default value only when the left side is `null` or `undefined`, whereas `||` returns the default value for any falsy value such as `0`, `false`, or an empty string.**
