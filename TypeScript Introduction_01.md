# TypeScript Introduction


TypeScript (TS) is a **superset of JavaScript** developed by Microsoft.  
It adds **static typing**, **interfaces**, **classes**, and **better error checking** to JavaScript.

- All JavaScript code is valid TypeScript.
- TypeScript compiles to plain JavaScript that runs anywhere JS runs.
- Helps catch errors **before running the code**.

---

## Why TypeScript is used in Playwright?

Playwright supports **both JavaScript and TypeScript**, but TypeScript is preferred because:

1. **Static typing**: The data type of a variable is checked before running the program (during development/compilation).
2. **Better IDE support**: Auto-completion, IntelliSense, and code hints.
3. **Structured code**: Easier to manage large test suites.
4. **Playwright typings**: TypeScript knows element locators, page objects, and fixtures automatically.

> Using TypeScript in Playwright makes your automation code safer, more readable, and maintainable.

---
# Interview questions


## Q1. Why did your company choose TypeScript instead of JavaScript for Playwright automation?

### Answer:

Our company chose **TypeScript** because it provides some advantages over JavaScript, especially for large automation frameworks.

### 1. It catches errors before running the code.

**JavaScript**

```javascript
let age = 25;

age = "Aniket";   // Allowed
```

JavaScript allows this, so the mistake may only be found while running the program.

**TypeScript**

```typescript
let age: number = 25;

age = "Aniket";   // Error
```

TypeScript immediately shows an error while writing the code.

This helps us fix mistakes earlier and reduces debugging time.

---

### 2. Better VS Code support

When writing Playwright code:

```typescript
page.
```

TypeScript provides proper suggestions like:

- goto()
- click()
- locator()
- fill()
- screenshot()

Because it already knows what `page` is.

In JavaScript, suggestions are available but are generally less accurate because JavaScript doesn't always know the exact type of an object.

---

### 3. Easier to maintain large frameworks

A Playwright framework usually contains:

- Page Objects
- Fixtures
- Utilities
- Test Data
- Helper Functions

As the framework grows, TypeScript helps organize the code using features like interfaces, classes, and type checking, making the framework easier to maintain.

---

### Interview Answer (Short)

> "We chose TypeScript because it catches errors while coding, provides better auto-completion in VS Code, and makes large Playwright automation frameworks easier to maintain than JavaScript."

---

## Q2. If Java also provides static typing, why not use Java instead of TypeScript?

### Answer:

Java also provides static typing, so both Java and TypeScript help catch errors before execution.

The difference is not that Java is worse.

The main reason is that **Playwright is primarily designed for JavaScript and TypeScript**, and TypeScript has the best support for Playwright.

Comparison:

| Java + Selenium | TypeScript + Playwright |
|-----------------|-------------------------|
| Best suited for Selenium | Best suited for Playwright |
| Strong typing | Strong typing |
| OOP support | OOP support |
| Official Selenium support | Official Playwright support |

So, if a project uses **Selenium**, Java is a very good choice.

If a project uses **Playwright**, TypeScript is generally the preferred choice because of its better ecosystem and official support.

---

### Interview Answer (Short)

> "Java also supports static typing, but since our project uses Playwright, TypeScript is the better choice because Playwright is primarily built and maintained for JavaScript and TypeScript."

---

## Q3. TypeScript is called a superset of JavaScript. What does that mean?

### Answer:

A **superset** means that every valid JavaScript code is also valid TypeScript code.

For example, this JavaScript code works exactly the same in TypeScript:

```javascript
let username = "admin";
console.log(username);
```

The difference is that **TypeScript provides additional features that JavaScript does not**, such as:

- Static typing
- Interfaces
- Enums
- Access modifiers (`public`, `private`, `protected`)
- Compile-time error checking

Example:

```typescript
interface User {
    username: string;
    password: string;
}

let user: User = {
    username: "admin",
    password: "admin123"
};
```

The above code is valid in TypeScript but not in JavaScript because JavaScript does not support **interfaces**.

Similarly, TypeScript supports access modifiers:

```typescript
class LoginPage {

    public username: string;

    private password: string;
}
```

JavaScript does not support `public`, `private`, or `protected` keywords like TypeScript.

Finally, TypeScript code is converted (compiled) into plain JavaScript before it runs in the browser or Node.js.

---

### Interview Answer (Short)

> "TypeScript is called a superset of JavaScript because all JavaScript code can run in TypeScript. On top of JavaScript, TypeScript adds features like static typing, interfaces, enums, access modifiers, and compile-time error checking, which help write safer and more maintainable code."

---

## Q4. What is static typing, and why is it useful?

### Answer:

**Static typing** means the data type of a variable is checked **while writing/compiling the code**, before the program runs.

### Example

**JavaScript (Dynamic Typing)**

```javascript
let age = 25;

age = "Aniket";   // Allowed
```

No error is shown while writing the code.

---

**TypeScript (Static Typing)**

```typescript
let age: number = 25;

age = "Aniket";   // Error
```

TypeScript immediately shows an error because a `string` cannot be assigned to a `number`.

---

### Why is it useful?

- Catches errors before execution.
- Reduces debugging time.
- Makes code more reliable.
- Very useful for large Playwright automation frameworks where many developers work on the same codebase.

---

### Interview Answer (Short)

> "Static typing means TypeScript checks variable data types before the code runs. It helps catch mistakes early, reduces runtime errors, and makes automation code safer and easier to maintain."

---

## Q5. JavaScript is dynamically typed. What does that mean?

### Answer:

**Dynamic typing** means you don't need to declare a variable's data type. A variable can store different types of values during execution.

### Example

```javascript
let value = 10;        // Number

value = "Aniket";      // String

value = true;          // Boolean
```

JavaScript allows this because it determines the data type **at runtime**, not while writing the code.

---

### Why can this be a problem?

Since JavaScript doesn't check types before execution, some mistakes are found only when the program runs.

Example:

```javascript
let age = 25;

age = "Aniket";

console.log(age + 5);
```

Output:

```
Aniket5
```

Instead of performing numeric addition, JavaScript concatenates the string and number.

---

### Interview Answer (Short)

> "Dynamic typing means JavaScript decides the variable's data type at runtime. A variable can hold different types of values, making JavaScript flexible but also increasing the chances of runtime errors."

---

## Q6. TypeScript vs JavaScript – When would you choose each?

### Answer:

The choice depends on the project size and requirements.

### Choose **JavaScript** when:

- The project is small.
- You need to quickly write scripts or prototypes.
- Type safety is not a major concern.

### Choose **TypeScript** when:

- The project is large.
- Multiple developers/testers are working together.
- You want to catch errors early.
- You are building a Playwright automation framework.
- Code should be easy to maintain in the long term.

---

### Comparison

| TypeScript | JavaScript |
|------------|------------|
| Static typing | Dynamic typing |
| Errors found before execution | Errors found during execution |
| Better IntelliSense | Limited type information |
| Better for large projects | Better for small projects |
| More maintainable | More flexible |

---

### Interview Answer (Short)

> "I would choose JavaScript for small or simple projects because it's quick and flexible. For large Playwright automation frameworks, I prefer TypeScript because it catches errors early, provides better IntelliSense, and makes the framework easier to maintain."

---

## Q7. What is compile-time error vs runtime error?

### Answer:

The difference is **when the error is detected**.

- **Compile-time error:** Error found before running the program.
- **Runtime error:** Error occurs while the program is running.

---

### Compile-time Error Example (TypeScript)

```typescript
let age: number = 25;

age = "Aniket";  // Error
```

TypeScript detects this mistake while writing the code because `age` should contain only numbers.

---

### Runtime Error Example (JavaScript)

```javascript
let user;

console.log(user.name);
```

The code runs, but fails during execution because `user` is undefined.

---

### Why is this important in automation?

In automation frameworks, compile-time checking helps identify issues early and reduces debugging time.

Example:

Wrong method usage, wrong data type, or incorrect function parameters can be caught before executing tests.

---

### Interview Answer (Short)

> "Compile-time errors are detected before execution, while runtime errors occur during execution. TypeScript helps reduce many errors by catching type-related issues before running the automation tests."

---

## Q8. Why does TypeScript provide better IntelliSense/auto-completion?

### Answer:

TypeScript provides better IntelliSense because it knows the **type and structure of objects** while writing code.

Since TypeScript understands:

- Variable types
- Function parameters
- Classes
- Interfaces
- Imported objects

the IDE can provide accurate suggestions.

---

### Example:

In Playwright:

```typescript
page.
```

TypeScript knows that `page` is a Playwright Page object, so VS Code suggests:

```
goto()
click()
locator()
fill()
screenshot()
waitForSelector()
```

---

In JavaScript:

```javascript
page.
```

JavaScript may provide suggestions, but it has less information about what `page` actually contains because types are not defined explicitly.

---

### Why is this useful in automation?

In large frameworks containing:

- Page Objects
- Fixtures
- Utilities
- Helper classes

better IntelliSense helps write code faster and reduces mistakes.

---

### Interview Answer (Short)

> "TypeScript provides better IntelliSense because it knows the types and structure of objects. In Playwright, it understands objects like Page and Locator, so it provides accurate method suggestions and helps reduce coding mistakes."
