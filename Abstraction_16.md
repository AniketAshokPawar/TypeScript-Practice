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

# TypeScript Interface - VVIP Interview Questions & Answers

Target:

* 0–2.5 Years Automation Tester / SDET
* TypeScript + Playwright Interviews

Focus:

* Interface
* implements
* extends
* Interface vs Abstract Class
* Multiple Interfaces
* Playwright Usage

---

# Q1. What is an Interface in TypeScript?

## Answer

An interface is a blueprint (contract) that defines what properties and methods a class must have.

It specifies **what should exist**, but not **how it should be implemented**.

Example:

```ts
interface Employee{

    name: string;

    displayDetails(): void;

}
```

Any class implementing this interface must provide both:

* `name`
* `displayDetails()`

### Interview Point

* Interface defines a contract.
* It improves consistency and type safety.

---

# Q2. What is the difference between `extends` and `implements`?

## Answer

### `extends`

Used for inheritance.

A child class inherits properties and methods from a parent class.

Example:

```ts
class Student extends Person{

}
```

---

### `implements`

Used when a class follows an interface.

The class must implement all members declared in the interface.

Example:

```ts
class QAEngineer implements Employee{

}
```

### Interview Point

* `extends` → Reuse code.
* `implements` → Follow a contract.

---

# Q3. What happens if a class does not implement all members of an interface?

## Answer

TypeScript gives a compile-time error.

Example:

```ts
interface Employee{

    displayDetails(): void;

}

class QAEngineer implements Employee{

}
```

Error:

```text
Class 'QAEngineer' incorrectly implements interface 'Employee'.
```

### Interview Point

A class must implement every property and method declared in the interface.

---

# Q4. Can a class implement multiple interfaces?

## Answer

Yes.

A class can implement multiple interfaces.

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

### Interview Point

Interfaces support multiple inheritance of contracts.

---

# Q5. Difference between Interface and Abstract Class?

## Answer

| Interface                              | Abstract Class                               |
| -------------------------------------- | -------------------------------------------- |
| Uses `interface` keyword               | Uses `abstract class`                        |
| Uses `implements`                      | Uses `extends`                               |
| Defines only a contract                | Can provide partial implementation           |
| No constructor                         | Can have constructor                         |
| No object state                        | Can maintain object state                    |
| Multiple interfaces can be implemented | Only one abstract/base class can be extended |

### Interview Point

Use:

* **Interface** → When you only need to define rules.
* **Abstract Class** → When you want common code + compulsory methods.

---

# Q6. Can an Interface extend another Interface?

## Answer

Yes.

Interfaces can inherit from other interfaces using `extends`.

Example:

```ts
interface Person{

    name: string;

}

interface Employee extends Person{

    department: string;

}
```

Now `Employee` contains:

* `name`
* `department`

### Interview Point

Interface inheritance is different from class inheritance.

It extends the contract, not implementation.

---

# Q7. Why do Interfaces support multiple inheritance but Classes do not?

## Answer

Interfaces contain only contracts, so there is no implementation conflict.

Example:

```ts
class User implements Login, Logout{

}
```

Both interfaces simply declare methods.

If classes supported multiple inheritance:

```text
Class A
↓

display()

Class B
↓

display()
```

The child class would not know which implementation to inherit.

This is called the **Diamond Problem**.

### Interview Point

* Interfaces → Multiple inheritance supported.
* Classes → Single inheritance only.

---

# Q8. What is an Interface Reference?

## Answer

An interface reference can store an object of any class that implements that interface.

Example:

```ts
interface Payment{

    pay(): void;

}

class CreditCardPayment implements Payment{

    pay(){

        console.log("Payment Successful");

    }

}

let payment: Payment = new CreditCardPayment();

payment.pay();
```

### Interview Point

Only members declared in the interface can be accessed through the interface reference.

---

# Q9. How are Interfaces used in Playwright Frameworks?

## Answer

Interfaces are commonly used to define contracts between different components.

Examples:

* Page Contracts
* API Service Contracts
* Repository Pattern
* Dependency Injection
* Mock Objects for Unit Testing

Example:

```ts
interface LoginActions{

    login(): void;

}

class LoginPage implements LoginActions{

    login(){

        console.log("Login");

    }

}
```

### Interview Point

Interfaces improve maintainability and loose coupling in large automation frameworks.

---

# Q10. When should you choose an Interface instead of an Abstract Class?

## Answer

Choose an **Interface** when:

* You only need to define a contract.
* Different classes will implement the behavior differently.
* No common implementation is required.
* Multiple contracts are needed.

Choose an **Abstract Class** when:

* You want to share common code.
* You need constructors or common properties.
* You want both reusable code and compulsory methods.

### Interview Point

A common guideline:

* Interface = Rules.
* Abstract Class = Rules + Shared implementation.

---

# Quick Interview Revision

| Question                                          | One-Line Answer                                                                      |
| ------------------------------------------------- | ------------------------------------------------------------------------------------ |
| What is an Interface?                             | A contract that defines required properties and methods.                             |
| `implements` vs `extends`?                        | `implements` follows a contract; `extends` inherits implementation.                  |
| Can a class implement multiple interfaces?        | Yes.                                                                                 |
| Can an interface extend another interface?        | Yes.                                                                                 |
| Interface vs Abstract Class?                      | Interface = contract only; Abstract Class = contract + partial implementation.       |
| Why multiple interfaces but not multiple classes? | Interfaces have no implementation conflict; classes would cause the Diamond Problem. |
| Interface reference?                              | An interface variable can hold an object of any implementing class.                  |
| Playwright usage?                                 | Contracts for pages, services, APIs, dependency injection, and mocks.                |

