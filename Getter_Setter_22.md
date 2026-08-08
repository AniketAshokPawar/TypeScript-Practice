# Getter and Setter in TypeScript

Getter and Setter are used mainly for **encapsulation** and provide controlled access to class properties.

They are especially useful with `private` properties.

---

# Getter

A getter is used to **read/access** a property.

### Syntax

```ts
get propertyName() {
    return value;
}
```

### Example

```ts
class Employee {

    private salary: number;

    constructor(salary: number) {
        this.salary = salary;
    }

    get salaryInfo() {
        return this.salary;
    }
}

let emp1 = new Employee(10000);

console.log(emp1.salaryInfo);
```

Output:

```text
10000
```

### Important

Getter is accessed like a property:

```ts
emp1.salaryInfo;      // ✅
```

Not like a method:

```ts
emp1.salaryInfo();    // ❌
```

---

# Setter

A setter is used to **modify/update** a property.

### Syntax

```ts
set propertyName(value) {
    // update property
}
```

### Example

```ts
class Employee {

    private salary: number;

    constructor(salary: number) {
        this.salary = salary;
    }

    get salaryInfo() {
        return this.salary;
    }

    set salaryInfo(amount: number) {
        this.salary = amount;
    }
}

let emp1 = new Employee(10000);

emp1.salaryInfo = 6000;

console.log(emp1.salaryInfo);
```

Output:

```text
6000
```

---

# Why Use Getter and Setter?

`private` prevents direct access from outside the class.

```ts
class Employee {

    private salary: number = 50000;
}

let emp = new Employee();

console.log(emp.salary); // ❌ Error
```

Getter and Setter provide **controlled access**.

```text
private property
       ↓
   ┌───┴───┐
 Getter   Setter
   ↓         ↓
 READ      UPDATE
```

---

# Getter + Setter with Validation

Setter can validate data before updating the property.

```ts
class BankAccount {

    private balance: number;

    constructor(balance: number) {
        this.balance = balance;
    }

    get balanceInfo() {
        return this.balance;
    }

    set balanceInfo(amount: number) {

        if (amount < 0) {
            throw new Error("Balance cannot be negative");
        }

        this.balance = amount;
    }
}
```

Usage:

```ts
let account = new BankAccount(5000);

account.balanceInfo = 10000;  // ✅

account.balanceInfo = -5000;  // ❌ Error
```

---

# Getter/Setter vs Normal Method

### Normal method

```ts
getSalary() {
    return this.salary;
}
```

Called as:

```ts
emp.getSalary();
```

### Getter

```ts
get salaryInfo() {
    return this.salary;
}
```

Called as:

```ts
emp.salaryInfo;
```

---

# Getter and Setter vs Private

| Concept | Purpose |
|---|---|
| `private` | Hides data from outside |
| Getter | Provides controlled read access |
| Setter | Provides controlled update access |
| Validation in setter | Controls what values can be assigned |

---

# Important Interview Point ⭐

**Does every private property require a getter/setter?**

No.

Getter/setter are optional.

Use them when you want to expose **controlled access** to private data.

---

# Encapsulation Connection

```text
Encapsulation
      ↓
Hide internal data
      ↓
private property
      ↓
Controlled access
      ↓
Getter → Read
Setter → Update
```

Definition:

> **Getter and Setter help achieve encapsulation by providing controlled access to private class properties.**

---

# Common Interview Questions

### Q1. What is a getter in TypeScript?

A getter is a special class accessor used to read a property. It is accessed like a property rather than a method.

### Q2. What is a setter in TypeScript?

A setter is a special class accessor used to modify a property. It can also perform validation before updating the value.

### Q3. Why are getter and setter commonly used with private properties?

Because private properties cannot be accessed directly from outside the class. Getter and setter provide controlled read/write access.

### Q4. Can a private property exist without getter/setter?

Yes. Getter and setter are not mandatory. They are used only when controlled external access is required.

### Q5. What is the main difference between getter and setter?

```text
Getter → Read
Setter → Modify/Update
```

---

# Interview VVIP Points

- `private` → prevents direct outside access.
- `get` → controlled read access.
- `set` → controlled write/update access.
- Getter is accessed like a property.
- Setter is assigned like a property.
- Setter can perform validation.
- Getter/setter are commonly associated with **encapsulation**.
- Not every private property needs getter/setter.
