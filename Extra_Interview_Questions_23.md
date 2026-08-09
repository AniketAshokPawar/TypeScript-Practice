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
