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
