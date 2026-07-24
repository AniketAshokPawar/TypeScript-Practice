# Functions in TypeScript

Functions are reusable blocks of code used to perform specific tasks.

Functions improve:
- code reusability
- readability
- maintainability

---

# Function Syntax

```ts
function functionName(){

    // code
}
```

---

# 1. Named Function with No Parameter and No Return Value

A function that:
- does not take input
- does not return value

---

## Example

```ts
function greet(): void {

    console.log("Welcome to TypeScript");
}

greet();
```

---

## Explanation

- `void` means function does not return anything
- Function only executes code

---

# 2. Named Function with Parameter and Return Value

A function that:
- accepts input
- returns value

---

## Example

```ts
function square(num: number): number {

    return num * num;
}

let result = square(5);

console.log(result);
```

---

## Output

```text
25
```

---

# Explanation

| Part | Meaning |
|---|---|
| `num: number` | Parameter with data type |
| `: number` | Return type |
| `return` | Sends value back |

---

# 3. Named Function with Multiple Parameters of Same Data Type

When number of parameters is not fixed,
we use **Rest Parameters** (`...`).

Rest parameter allows function to accept multiple values of same data type.

---

## Example

```ts
function add(...nums: number[]): number {

    let sum = 0;

    for(let i = 0; i < nums.length; i++){

        sum += nums[i];
    }

    return sum;
}

console.log(add(10, 20));

console.log(add(10, 20, 30, 40));
```

---

# Output

```text
30
100
```

---

# Explanation

| Part | Meaning |
|---|---|
| `...nums` | Rest parameter |
| `number[]` | Array of numbers |
| `nums.length` | Total parameters passed |

---

# Important Point

- Rest parameter accepts variable number of arguments
- All values should be same data type
- Rest parameter should be last parameter

# 4. Named Function with Multiple Parameters of Different Data Types

When function accepts:
- fixed parameters of different data types
- along with multiple values using Rest Parameters

---

# Example

```ts
function employeeDetails(

    name: string,
    age: number,
    ...skills: string[]

): void {

    console.log(`Employee Name: ${name}`);

    console.log(`Employee Age: ${age}`);

    console.log(`Skills: ${skills}`);
}

employeeDetails(

    "Aniket",
    25,
    "Playwright",
    "TypeScript",
    "SQL"
);
```

---

# Output

```text
Employee Name: Aniket
Employee Age: 25
Skills: Playwright,TypeScript,SQL
```

---

# Explanation

| Parameter | Data Type |
|---|---|
| name | string |
| age | number |
| ...skills | string[] |

---

# Important Points

- Function accepts different data types
- Rest parameter stores multiple values
- Rest parameter behaves like an array
- Rest parameter should always be last parameter

---

# Invalid Example

```ts
function test(...skills:string[], age:number){
}
```

## Error

```text
A rest parameter must be last in a parameter list.
```

---

# Interview Point

Rest parameters allow functions to accept variable number of arguments while maintaining Type Safety.

# 5. Named Function with Optional Parameter

Optional parameter uses `?`.

- Parameter may or may not be passed

---

## Example

```ts
function student(name: string, grade?: string): void {

    console.log(`Student Name: ${name}`);

    console.log(`Grade: ${grade}`);
}

student("Aniket");

student("Rahul", "A");
```

---

# Output

```text
Student Name: Aniket
Grade: undefined

Student Name: Rahul
Grade: A
```

---

# Important Point

Optional parameter:
- should generally come after required parameters

---

# 6. Named Function with Default Parameter

Default parameter gets default value if argument is not passed.

---

## Example

```ts
function greetUser(name: string = "Guest"): void {

    console.log(`Welcome ${name}`);
}

greetUser();

greetUser("Aniket");
```

---

# Output

```text
Welcome Guest
Welcome Aniket
```

---

# Difference Between Optional and Default Parameter

| Optional Parameter | Default Parameter |
|---|---|
| May become undefined | Gets default value |
| Uses `?` | Uses `=` |
| Argument optional | Argument optional |

---

# Interview Points

- Functions improve code reusability
- Parameters are inputs to functions
- `return` sends value back
- `void` means no return value
- Optional parameters use `?`
- Default parameters use `=`

---

# Best Practices

- Use meaningful function names
- Keep functions small and focused
- Define proper parameter types
- Define return types clearly

---

# Functions in TypeScript - VVIP Interview Questions

---

## Q1. What is a function and why do we use it?

### Answer

A function is a reusable block of code that performs a specific task.

We use functions to:
- Avoid duplicate code
- Improve readability
- Make code easier to maintain

### Interview Answer (Short)

> "A function is a reusable block of code. It helps avoid duplicate code and makes the automation framework easier to maintain."

---

## Q2. Why are functions heavily used in Playwright frameworks?

### Answer

Almost every action in Playwright is written as a function.

Examples:
- login()
- logout()
- click()
- fill()
- takeScreenshot()
- waitForLoader()

### Interview Answer (Short)

> "Playwright frameworks use functions to make actions reusable. Instead of writing the same code in every test, we create methods and call them whenever needed."

---

## Q3. What is the difference between a parameter and an argument?

### Answer

- **Parameter** → Variable defined in the function.
- **Argument** → Actual value passed while calling the function.

Example:

```ts
function login(username: string) // username = Parameter

login("admin"); // "admin" = Argument
```

### Interview Answer (Short)

> "A parameter is declared in the function definition, while an argument is the value passed when calling the function."

---

## Q4. What is the difference between `void` and a return type?

### Answer

- `void` → Function does not return any value.
- Return type (`string`, `number`, `boolean`, etc.) → Function returns a value.

### Interview Answer (Short)

> "`void` means the function performs an action but returns nothing. A return type means the function sends a value back to the caller."

---

## Q5. When should you return a value instead of using `console.log()`?

### Answer

Use `return` when the result may be used later.

Use `console.log()` only for displaying output.

### Interview Answer (Short)

> "I prefer returning values because the caller can reuse them. `console.log()` is mainly for debugging or displaying output."

---

## Q6. What are rest parameters? When have you used them?

### Answer

Rest parameters (`...`) allow a function to accept a variable number of arguments.

Example:

```ts
function add(...numbers: number[])
```

### Interview Answer (Short)

> "Rest parameters are useful when I don't know how many values will be passed. They collect all values into an array."

---

## Q7. What is the difference between optional parameters and default parameters?

### Answer

| Optional (`?`) | Default (`=`) |
|---------------|---------------|
| May be `undefined` | Gets a default value |
| Uses `?` | Uses `=` |

### Interview Answer (Short)

> "Optional parameters may be omitted and become `undefined`, whereas default parameters automatically receive a predefined value."

---

## Q8. Where have you used functions in your Playwright framework?

### Answer

Examples:
- LoginPage methods
- BasePage common actions
- Utility methods
- Hooks
- Helper methods

### Interview Answer (Short)

> "I have used functions in Page Objects, BasePage, utility classes, and hooks to keep the framework reusable and maintainable."

---

## Q9. Why do we keep common methods in BasePage instead of writing them in every Page Object?

### Answer

Common methods like `click()`, `fill()`, and `waitForElement()` are used across many pages.

Keeping them in BasePage:
- Avoids duplicate code
- Improves maintainability
- Makes updates easier

### Interview Answer (Short)

> "BasePage stores common actions so all page classes can reuse them. This avoids duplication and makes maintenance easier."

---

## Q10. Can a function have multiple return statements?

### Answer

Yes.

A function can contain multiple `return` statements, but only one is executed depending on the condition.

Example:

```ts
function checkAge(age: number): string {

    if(age >= 18){

        return "Eligible";

    }

    return "Not Eligible";

}
```

### Interview Answer (Short)

> "Yes. A function can have multiple `return` statements, but only one executes based on the condition."
