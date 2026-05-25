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
