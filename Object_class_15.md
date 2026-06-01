# TypeScript Notes: Objects and Classes

## 1. Object Creation

An **object** is a collection of properties (data) and methods (functions).

### Syntax

```ts
let person = {
    name: "Aniket",
    age: 27,

    greet() {
        console.log("Hello");
    }
};
```

### Accessing Properties

```ts
console.log(person.name);
console.log(person.age);
```

### Calling Methods

```ts
person.greet();
```

### Adding Properties Later

```ts
person.city = "Pune";
```

### Using `this`

```ts
let person = {
    name: "Aniket",

    greet() {
        console.log(this.name);
    }
};

person.greet();
```

### Key Points

- Object stores data in properties.
- Object can contain methods (functions).
- Use `this` to access properties of the current object.
- New properties can be added after object creation.

---

## 2. Class Creation

A **class** is a blueprint or template used to create objects.

### Syntax

```ts
class Student {

    name: string;
    rollNumber: number;

    constructor(name: string, rollNumber: number) {
        this.name = name;
        this.rollNumber = rollNumber;
    }

    displayDetails() {
        console.log(`${this.name} - ${this.rollNumber}`);
    }
}
```

---

## Constructor

A constructor is a special method that runs automatically when an object is created.

```ts
constructor(name: string, rollNumber: number) {
    this.name = name;
    this.rollNumber = rollNumber;
}
```

### Purpose

- Initialize object properties.
- Assign values during object creation.

---

## Creating Objects from a Class

```ts
let student1 = new Student("Aniket", 101);
let student2 = new Student("Rahul", 102);
```

---

## Calling Methods

```ts
student1.displayDetails();
student2.displayDetails();
```

---

## Complete Example

```ts
class Employee {

    firstName: string;
    lastName: string;
    salary: number;

    constructor(firstName: string, lastName: string, salary: number) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.salary = salary;
    }

    displayDetails() {
        console.log(
            `Name: ${this.firstName} ${this.lastName}`
        );
    }

    displaySalary() {
        console.log(`Salary: ${this.salary}`);
    }
}

let emp1 = new Employee("Aniket", "Pawar", 30000);

emp1.displayDetails();
emp1.displaySalary();
```

---

## Class vs Object

| Class | Object |
|---------|---------|
| Blueprint/Template | Actual Instance |
| Defines properties and methods | Contains actual values |
| Created using `class` keyword | Created using `new` keyword |

### Example

```ts
class Student {
    name: string;
}

let student1 = new Student();
```

- `Student` → Class
- `student1` → Object

---

## Important Keywords

### `class`

Used to create a blueprint.

```ts
class Employee {}
```

### `constructor`

Special method called automatically during object creation.

```ts
constructor(name: string) {
    this.name = name;
}
```

### `this`

Refers to the current object.

```ts
this.name
```

### `new`

Creates an object from a class.

```ts
let emp1 = new Employee("Aniket");
```

---

## Interview One-Liners

- Object = Collection of properties and methods.
- Class = Blueprint for creating objects.
- Constructor = Special method executed automatically when an object is created.
- `this` = Refers to the current object instance.
- `new` = Creates an object from a class.
- One class can create multiple objects.
- Properties store data, methods perform actions.

---

## Quick Template

```ts
class Employee {

    name: string;
    salary: number;

    constructor(name: string, salary: number) {
        this.name = name;
        this.salary = salary;
    }

    display() {
        console.log(`${this.name} - ${this.salary}`);
    }
}

let emp1 = new Employee("Aniket", 30000);

emp1.display();
```


# Readonly Property

A `readonly` property can be assigned a value only once. After initialization, its value cannot be changed.

### Example

```ts
readonly rollNumber: number;
```

Value is assigned in the constructor:

```ts
this.rollNumber = rollNumber;
```

Valid:

```ts
let s1 = new student(12, "Aniket", 85, "Satara");
```

Invalid:

```ts
s2.rollNumber = 14;
```

Output:

```text
Cannot assign to 'rollNumber' because it is a read-only property.
```

### Use Cases

- Student Roll Number
- Employee ID
- Account Number
- Product ID

These values should remain fixed after object creation.

---

# Optional Property

An optional property is declared using the `?` symbol. It means the property is not mandatory while creating an object.

### Example

```ts
city?: string;
```

Object with city:

```ts
let s1 = new student(12, "Aniket", 85, "Satara");
```

Object without city:

```ts
let s2 = new student(13, "Andy", 89);
```

Both objects are valid because `city` is optional.

### Handling Optional Property

```ts
if (this.city) {
    console.log(`city: ${this.city}`);
}
else {
    console.log("City is not provided.");
}
```

If `city` is supplied, it is displayed. Otherwise, a default message is shown.

### Use Cases

- City
- Address
- Phone Number
- Middle Name

These details may not always be available.

---
### Complete example

```ts
class student{

    readonly rollNumber:number; // Read only variable - can assign value only once
    name:string;
    marks:number;
    city?:string; // Can skip this 

    constructor(rollNumber:number,name:string,marks:number, city?:string){
        this.rollNumber = rollNumber;
        this.name = name;
        this.marks = marks;
        this.city = city;
    }

    displayDetails(){

        console.log(`rollNumber: ${this.rollNumber}`);
        console.log(`name: ${this.name}`);
        console.log(`marks: ${this.marks}`);

        if(this.city){
            console.log(`city: ${this.city}`);
        }
        else{
            console.log("City is not provided.");
        }
        
    }

}

let s1 = new student(12,"Aniket",85,"Satara"); // regular object
s1.displayDetails();

let s2 = new student(13,"Andy",89); // skipped city parameter
s2.displayDetails();

s2.marks = 94;
s2.rollNumber = 14; // error - Cannot assign to 'rollNumber' because it is a read-only property.
s2.displayDetails();
```
# Key Difference

| Readonly Property | Optional Property |
|------------------|------------------|
| Value must be provided and cannot be changed later. | Value may or may not be provided. |
| Uses `readonly` keyword. | Uses `?` symbol. |
| Example: `readonly rollNumber:number` | Example: `city?:string` |
| `s2.rollNumber = 14` ❌ Error | `new student(13,"Andy",89)` ✅ Valid |



# Static Properties and Static Methods in TypeScript

## Static Property

A static property belongs to the **class itself**, not to individual objects. All objects of the class share the same static property value.

### Syntax

```ts
static propertyName: dataType = value;
```

### Example

```ts
static schoolName: string = "ABC Public School";
```

Accessing static property:

```ts
console.log(Student.schoolName);
```

---

## Static Method

A static method belongs to the **class**, not to objects. It can access static properties and is called using the class name.

### Syntax

```ts
static methodName() {
    // code
}
```

### Example

```ts
static displaySchoolName() {
    console.log(`School Name: ${Student.schoolName}`);
}
```

Calling static method:

```ts
Student.displaySchoolName();
```

---

## Why Use Static Members?

Use static members when a value or functionality should be common to all objects.

Examples:

- School Name
- Company Name
- Tax Rate
- Utility Methods

---

## Important Rules

### Access using Class Name

```ts
Student.schoolName;
Student.displaySchoolName();
```

### Cannot Access using Object

```ts
s1.schoolName;          // Error
s1.displaySchoolName(); // Error
```

Static members belong to the class, not to individual objects.

---

## Example

```ts
class Student {

    static schoolName: string = "ABC Public School";

    name: string;
    marks: number;

    constructor(name: string, marks: number) {
        this.name = name;
        this.marks = marks;
    }

    static displaySchoolName() {
        console.log(`School Name: ${Student.schoolName}`);
    }
}
```

---

## Key Difference

| Regular Property/Method | Static Property/Method |
|------------------------|------------------------|
| Belongs to an object | Belongs to the class |
| Access using object | Access using class name |
| Each object has its own copy | Shared by all objects |
| Example: `name`, `marks` | Example: `schoolName` |


## Complete example
```ts
class student{

    name:string;
    id:number;
    age:number;
    static schoolName:string = "NESS";

    constructor(name:string,id:number,age:number){

            this.name = name;
            this.id = id;
            this.age = age;
    }

    displayDetails(){
        console.log(`Name: ${this.name} \nID: ${this.id} \n Age: ${this.age} \nSchool name: ${student.schoolName}`);
    }

    changeSchoolName(Sname:string){
        student.schoolName = Sname;
    }
}

let s1 = new student("Aniket",101,27);

s1.displayDetails();

s1.changeSchoolName("SSOEP");

s1.displayDetails();

```

---

# Method Overloading in TypeScript

Method overloading allows a method to be called in multiple ways by defining multiple method signatures with different parameters.

TypeScript supports method overloading using:

1. Multiple overload signatures
2. One common implementation method

---

## Syntax

```ts
method(param1: type): returnType;
method(param1: type, param2: type): returnType;

method(param1: type, param2?: type): returnType {
    // implementation
}
```

---

## Example

```ts
class Calculator {

    add(a: number, b: number): number;
    add(a: number, b: number, c: number): number;

    add(a: number, b: number, c?: number): number {

        if (c !== undefined) {
            return a + b + c;
        }

        return a + b;
    }
}
```

Usage:

```ts
const calc = new Calculator();

calc.add(10, 20);      // 30
calc.add(10, 20, 30);  // 60
```

---

## Important Rules

### 1. Multiple Signatures Allowed

```ts
add(a: number, b: number): number;
add(a: number, b: number, c: number): number;
```

These define the valid ways to call the method.

---

### 2. Only One Implementation

```ts
add(a: number, b: number, c?: number): number {
    // logic
}
```

The implementation must handle all overload cases.

---

### 3. Invalid Calls Produce Errors

```ts
calc.add(10);              // Error
calc.add("10", "20");      // Error
calc.add(10, 20, 30, 40);  // Error
```

---

## Advantages

- Improves code readability.
- Allows the same method to handle different parameter combinations.
- Provides better type checking and IntelliSense support.

---

## Key Point

In TypeScript, method overloading exists only at compile time. At runtime, there is only one actual implementation method.

---

# Inheritance, Method Overriding and super Keyword

## Inheritance

Inheritance allows a child class to acquire the properties and methods of a parent class using the `extends` keyword.

### Example

```ts
class student extends person
```

Here, `student` inherits:

- `name`
- `age`
- `displayDetails()`

from the `person` class.

---

## super Keyword

The `super` keyword is used inside a child class to access members of the parent class.

### Calling Parent Constructor

```ts
super(name, age);
```

This invokes the constructor of the `person` class and initializes the inherited properties.

Without `super()`, the child class cannot access or initialize parent class properties.

### Calling Parent Method

```ts
super.displayDetails();
```

This invokes the `displayDetails()` method of the parent class from inside the child class.

---

## Method Overriding

Method overriding occurs when a child class provides its own implementation of a method already present in the parent class.

### Parent Method

```ts
displayDetails() {
    console.log(`Name: ${this.name} \n Age: ${this.age}`);
}
```

### Child Method (Overridden)

```ts
displayDetails() {

    super.displayDetails();
    console.log(`${this.marks}`);
}
```

When `displayDetails()` is called on a `student` object, the child class version executes instead of the parent version.

---

## Accessing Parent Properties Through Child Object

Since `student` inherits `person`, the child object can access parent properties.

### Example

```ts
let s1 = new student("Aniket", 27, 85);

console.log(s1.name);
console.log(s1.age);
console.log(s1.marks);
```

---

## Parent Reference Holding Child Object

```ts
let per: person = new student("Anik", 28, 99);
```

- Reference Type = `person`
- Object Type = `student`

A parent reference can store a child object.

### Valid

```ts
per.displayDetails();
```

Because `displayDetails()` exists in the `person` class.

### Invalid

```ts
per.displayDetails2();
```

Error:

```text
Property 'displayDetails2' does not exist on type 'person'
```

because `displayDetails2()` is only available in the `student` class.

---

## Key Points

- `extends` is used for inheritance.
- `super()` calls the parent class constructor.
- `super.methodName()` calls a parent class method.
- A child class can override parent methods.
- A parent reference can hold a child object.
- A parent reference can access only members declared in the parent class.
- When an overridden method is called, the child class implementation executes (runtime polymorphism).


---

## Example

```ts
// inheritance, method overriding, super keyword to invoke parent class constructor properties

// Parent class

class person{

    name:string;
    age:number;

    constructor(name:string, age:number){

        this.name = name;
        this.age = age;
    }

    displayDetails(){

        console.log(`Name: ${this.name} \n Age: ${this.age}`);
    }
    displayDetails2(){
        console.log("Extra function only in parent function");
    }
}

// Child class

class student extends person{

    marks:number;

    constructor(name:string, age:number,marks:number){

        super(name,age);                                // using parent class constructor properties using super keyword
        this.marks = marks;
    }

// Method overriding

    displayDetails(){

        super.displayDetails();
        console.log(`${this.marks}`)
    }
    displayDetails3(){
        console.log("Extra .....function");
    }
}

let s1 = new student("Aniket", 27,85);
s1.displayDetails();

s1.displayDetails2(); // accessing method from parent class into child class

let per:person = new student("Anik", 28, 99);
//per.displayDetails3(); // give error - Property 'displayDetails3' does not exist on type 'person'.
```
---

# Access Modifiers in TypeScript

Access modifiers control the visibility and accessibility of class properties and methods.

TypeScript provides three access modifiers:

- `public`
- `protected`
- `private`

---

# Public Access Modifier

A `public` member can be accessed from anywhere:

- Inside the same class
- Inside child classes
- Through objects

### Example

```ts
public name: string;
```

Accessing through object:

```ts
console.log(s1.name);
```

### Use Cases

- Name
- Email
- Product Name

Properties that should be accessible to everyone.

---

# Protected Access Modifier

A `protected` member can be accessed:

- Inside the same class
- Inside child classes

It cannot be accessed directly through an object.

### Example

```ts
protected age: number;
```

Access inside child class:

```ts
console.log(this.age);
```

Invalid access:

```ts
console.log(s1.age);
```

Error:

```text
Property 'age' is protected and only accessible within class 'Person' and its subclasses.
```

### Use Cases

- Employee Details
- Student Information
- Internal Data Needed by Child Classes

---

# Private Access Modifier

A `private` member can be accessed only inside the class where it is declared.

It cannot be accessed:

- Through objects
- Inside child classes

### Example

```ts
private salary: number;
```

Valid:

```ts
showSalary() {
    console.log(this.salary);
}
```

Invalid:

```ts
console.log(this.salary); // Inside child class
console.log(s1.salary);   // Through object
```

Error:

```text
Property 'salary' is private and only accessible within class 'Person'.
```
### Complete Example

```ts

class person{

    public name:string;    // available to all
    protected age: number; // only in parent and there child class
    private salary:number; // only in current class

    constructor(name:string,age:number,salary:number){

        this.name = name;
        this.age = age;
        this.salary = salary;
    }

    showSalary(){
        console.log(`Salary: ${this.salary}`);
    }
} 

class student extends person{

    displaydetails(){
        console.log(`Name: ${this.name}`);
        console.log(`Age: ${this.age}`);
        //console.log(`salary: ${this.salary}`); // Property 'salary' is private and only accessible within class 'person'.
    }
}

let s1 = new student("Aniket", 27,30000);

s1.displaydetails();
s1.showSalary();

console.log(s1.name);
//console.log(s1.age); // Property 'age' is protected and only accessible within class 'person' and its subclasses.
//console.log(s1.salary); //Property 'salary' is private and only accessible within class 'person'.

```

### Use Cases

- Salary
- Password
- Bank Balance
- Sensitive Data

---

# Accessibility Table

| Modifier | Same Class | Child Class | Object |
|-----------|-----------|-----------|---------|
| `public` | ✅ | ✅ | ✅ |
| `protected` | ✅ | ✅ | ❌ |
| `private` | ✅ | ❌ | ❌ |

---

# Key Points

- `public` → Accessible everywhere.
- `protected` → Accessible inside the class and child classes only.
- `private` → Accessible only inside the same class.
- Access modifiers help implement data hiding and encapsulation.
- If no access modifier is specified, TypeScript uses `public` by default.
