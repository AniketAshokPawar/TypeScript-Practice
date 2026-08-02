# Abstraction in TypeScript

Abstraction is the OOP concept of **showing only what is required and hiding how it is implemented**.

It focuses on defining a **contract (requirement)** while leaving the implementation to child classes.

In TypeScript, abstraction can be achieved using:

* **Abstract Classes**
* **Interfaces** (covered separately)

---

# Why Do We Need Abstraction?

Without abstraction, developers may forget to implement important methods in child classes.

Abstraction ensures that every child class follows the required contract.

It provides:

* Code consistency
* Better maintainability
* Compile-time error checking
* Common design across all child classes

---

# What vs How

Abstraction separates **WHAT** from **HOW**.

### WHAT

Defines the required behavior.

Example:

```text
Every page must implement:

verifyPage()
```

### HOW

Each child class decides its own implementation.

Example:

```text
Login Page
↓

Verify Login button

Dashboard Page
↓

Verify Dashboard title

Settings Page
↓

Verify Settings heading
```

The abstract class only defines **WHAT** is required.

Each child class decides **HOW** to perform it.

---

# Abstract Class

An abstract class is a special class that:

* Can contain normal methods.
* Can contain abstract methods.
* Cannot be instantiated directly.

Syntax:

```ts
abstract class BasePage{

}
```

Invalid:

```ts
let page = new BasePage(); // Error
```

---

# Abstract Method

An abstract method has:

* No implementation
* Only declaration

Syntax:

```ts
abstract verifyPage(): void;
```

The child class **must** implement this method.

---

# Example

```ts
abstract class BasePage{

    click(){
        console.log("Click");
    }

    fill(){
        console.log("Fill");
    }

    abstract verifyPage(): void;

}

class LoginPage extends BasePage{

    verifyPage(){

        console.log("Verify Login Page");

    }

}
```

---

# Why Does Abstract Class Use `extends`?

An abstract class is still a class.

Therefore, child classes inherit it using:

```ts
extends
```

Example:

```ts
class LoginPage extends BasePage{

}
```

---

# Inheritance vs Abstraction

## Inheritance

Purpose:

```text
Reuse existing code.
```

Example:

```ts
class BasePage{

    click(){}

    fill(){}

}

class LoginPage extends BasePage{

}
```

The child automatically gets:

* click()
* fill()

---

## Abstraction

Purpose:

```text
Force every child to implement required behavior.
```

Example:

```ts
abstract class BasePage{

    abstract verifyPage(): void;

}
```

Every child must implement:

```ts
verifyPage()
```

---

# Inheritance + Abstraction Together

In real projects, both concepts are commonly used together.

Example:

```ts
abstract class BasePage{

    click(){}

    fill(){}

    wait(){}

    abstract verifyPage(): void;

}
```

Here:

Inheritance provides:

```text
click()

fill()

wait()
```

Abstraction provides:

```text
Every page MUST implement verifyPage().
```

---

# Real Playwright Example

```text
BasePage
│
├── click()
├── fill()
├── wait()
└── abstract verifyPage()

        ▲
        │ extends
        │

----------------------------

LoginPage

verifyPage(){

    Verify Login Button

}

----------------------------

DashboardPage

verifyPage(){

    Verify Dashboard Title

}
```

Every page reuses common methods while implementing its own verification logic.

---

# Advantages

* Enforces coding standards.
* Prevents developers from forgetting required methods.
* Improves maintainability.
* Supports framework design.
* Provides compile-time safety.

---

# Real-Time Use Cases

In automation frameworks:

* BasePage
* BaseTest
* BaseAPI
* BaseComponent

Common reusable methods:

```text
click()

fill()

wait()

scroll()

takeScreenshot()
```

Common required methods:

```text
verifyPage()

loadData()

initialize()

cleanup()
```

---

# Interview One-Liners

* Abstraction means defining **what** should be done while hiding **how** it is implemented.
* Abstract classes cannot be instantiated.
* Abstract methods have only declarations and no implementation.
* Child classes must implement all abstract methods.
* Abstract classes can contain both normal and abstract methods.
* Inheritance provides code reuse, whereas abstraction enforces a contract.
* In Playwright, an abstract `BasePage` can provide common utilities while forcing every page to implement methods like `verifyPage()`.

---

# Quick Revision

| Inheritance                   | Abstraction                           |
| ----------------------------- | ------------------------------------- |
| Reuses existing code          | Defines required behavior             |
| Uses `extends`                | Uses `abstract` class or `interface`  |
| Child inherits implementation | Child must implement abstract methods |
| Can exist independently       | Can exist independently               |

---

# Easy Memory Trick

```text
Inheritance
↓

"I already wrote this code.
Take it."

----------------------------

Abstraction
↓

"I don't know HOW you'll do it,
but you MUST do it."

----------------------------

Together
↓

Reuse common code
+

Force required implementation
```

# Interface in TypeScript

An **interface** is a blueprint that defines a contract for a class.

It specifies **what properties and methods must exist**, but **does not provide their implementation**.

A class that implements an interface must provide implementations for all its members.

---

# Why Do We Need Interface?

Interfaces ensure that different classes follow the same structure.

They provide:

* Code consistency
* Better maintainability
* Compile-time type checking
* Loose coupling
* Better framework design

---

# Interface Syntax

```ts
interface InterfaceName{

    propertyName: dataType;

    methodName(): returnType;

}
```

---

# Example

```ts
interface Employee{

    name: string;

    salary: number;

    displayDetails(): void;

}
```

Here, the interface only defines the required members.

It does **not** provide their implementation.

---

# Implementing an Interface

A class implements an interface using the `implements` keyword.

```ts
class ClassName implements InterfaceName{

}
```

---

# Example

```ts
interface Employee{

    name: string;

    salary: number;

    displayDetails(): void;

}

class QAEngineer implements Employee{

    name: string;

    salary: number;

    constructor(name:string,salary:number){

        this.name = name;

        this.salary = salary;

    }

    displayDetails(){

        console.log(`${this.name} - ${this.salary}`);

    }

}
```

---

# Creating Object

```ts
let emp1 = new QAEngineer("Aniket",50000);

emp1.displayDetails();
```

---

# Why Must We Implement Every Method?

If a class implements an interface, it **must** implement every property and method declared in that interface.

Example:

```ts
interface Employee{

    displayDetails(): void;

}
```

Invalid:

```ts
class QAEngineer implements Employee{

}
```

Error:

```text
Class 'QAEngineer' incorrectly implements interface 'Employee'.
```

---

# Multiple Interfaces

A class can implement more than one interface.

Syntax:

```ts
class Employee implements Interface1, Interface2{

}
```

Example:

```ts
interface Login{

    login(): void;

}

interface Logout{

    logout(): void;

}

class User implements Login, Logout{

    login(){

        console.log("Login");

    }

    logout(){

        console.log("Logout");

    }

}
```

---

# Interface Can Extend Another Interface

Interfaces can inherit from other interfaces.

```ts
interface Person{

    name: string;

}

interface Employee extends Person{

    salary: number;

}
```

Now Employee contains:

```text
name

salary
```

---

# Interface vs Class

## Interface

Defines only the contract.

```text
What is required?
```

## Class

Provides actual implementation.

```text
How it works?
```

---

# Interface vs Abstract Class

| Interface                     | Abstract Class                    |
| ----------------------------- | --------------------------------- |
| Uses `interface` keyword      | Uses `abstract class`             |
| Uses `implements`             | Uses `extends`                    |
| No implementation (generally) | Can contain implementation        |
| Cannot store object state     | Can store properties and state    |
| Supports multiple interfaces  | Single inheritance only           |
| Pure contract                 | Partial implementation + contract |

---

# Abstract Class vs Interface

## Abstract Class

```ts
abstract class BasePage{

    click(){

        console.log("Click");

    }

    abstract verifyPage(): void;

}
```

Provides:

* Common implementation
* Required methods

---

## Interface

```ts
interface Page{

    verifyPage(): void;

}
```

Provides only:

```text
Contract
```

No implementation.

---

# Real Playwright Example

```ts
interface LoginActions{

    login(): void;

}

class LoginPage implements LoginActions{

    login(){

        console.log("Perform Login");

    }

}
```

Every page implementing LoginActions must provide:

```text
login()
```

---

# When Should We Use Interface?

Use interface when:

* Multiple classes should follow the same structure.
* You only want to define the contract.
* No common implementation is needed.
* Different classes implement the behavior differently.

---

# Interface vs Inheritance

Inheritance

```text
Reuse existing code.
```

Interface

```text
Force classes to follow the same contract.
```

---

# Real Industry Examples

Interfaces are commonly used for:

* Page Contracts
* API Contracts
* Service Layer
* Repository Pattern
* Dependency Injection
* Mock Objects in Unit Testing

---

# Important Keywords

## interface

Creates a contract.

```ts
interface Employee{

}
```

---

## implements

Used by a class to implement an interface.

```ts
class QAEngineer implements Employee{

}
```

---

## extends (Interface)

Used when one interface inherits another.

```ts
interface Employee extends Person{

}
```

---

# Interview One-Liners

* Interface defines a contract.
* Interfaces do not provide implementation.
* A class uses `implements` to implement an interface.
* A class must implement every member of an interface.
* One class can implement multiple interfaces.
* Interfaces support abstraction.
* Interfaces provide loose coupling.
* Abstract class uses `extends`; interface uses `implements`.

---

# Quick Revision

| Feature              | Interface    |
| -------------------- | ------------ |
| Keyword              | `interface`  |
| Implemented Using    | `implements` |
| Multiple Interfaces  | ✅ Yes        |
| Constructors         | ❌ No         |
| Object Creation      | ❌ No         |
| Contract Only        | ✅ Yes        |
| Supports Abstraction | ✅ Yes        |

---

# Easy Memory Trick

```text
Class
↓

Complete implementation

-------------------------

Abstract Class
↓

Some implementation

+

Some compulsory methods

-------------------------

Interface
↓

Only rules

No implementation

-------------------------

Inheritance
↓

Reuse code

-------------------------

Interface
↓

Follow the contract
```
