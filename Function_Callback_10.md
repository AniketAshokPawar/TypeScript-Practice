# Callback Function in TypeScript

A callback function is:
> a function passed as argument to another function.

It allows dynamic behavior.

---

# Example

```ts
let largest = (...num:number[])=>{

    let large = num[0];

    for(let i=1;i<num.length;i++){

        if(num[i] > large){

            large = num[i];
        }
    }

    console.log(large);
}

let smallest = (...num:number[])=>{

    let small = num[0];

    for(let i=1;i<num.length;i++){

        if(num[i] < small){

            small = num[i];
        }
    }

    console.log(small);
}

let comparison = (

    operation:any,
    ...num:number[]

)=>{

    operation(...num);
}

comparison(largest,12,32,11,3,53);

comparison(smallest,12,32,11,3,53);
```

---

# Output

```text
53
3
```

---

# Explanation

## Callback Functions

```ts
largest()
smallest()
```

These functions are passed into another function.

---

## Main Function

```ts
comparison()
```

This function:
- accepts callback function
- executes passed function dynamically

---

## Function Call

```ts
comparison(largest,12,32,11,3,53);
```

Internally becomes:

```ts
largest(12,32,11,3,53);
```

---

# Important Concepts

| Concept | Meaning |
|---|---|
| Callback Function | Function passed as argument |
| `operation:any` | Stores function reference |
| `...num` | Rest parameter |
| `operation(...num)` | Executes callback function |
| `...` | Spread operator |

---

# Interview Point

Callback functions help create reusable and dynamic code.

---

# Callback Functions in TypeScript

---

## Q1. What is a callback function?

### Answer

A callback function is **a function that is passed as an argument to another function**.

The receiving function can execute the callback whenever required.

---

## Example

```ts
let greet = () => {

    console.log("Good Morning");

}

let execute = (operation: any) => {

    operation();

}

execute(greet);
```

---

## Output

```text
Good Morning
```

---

## Q2. Why do we use callback functions?

### Answer

Callback functions make code:

- Reusable
- Flexible
- Dynamic

Instead of writing separate functions for similar tasks, we can pass different callback functions.

---

## Example

```ts
calculate(square, 5);

calculate(cube, 5);
```

The same `calculate()` function performs different operations based on the callback passed.

---

## Q3. What is the difference between passing a function and calling a function?

### Answer

Passing a function means sending its reference.

Calling a function means executing it.

### Example

```ts
execute(greet);
```

Here,

```ts
greet
```

is **passed**.

Inside `execute()`,

```ts
operation();
```

**calls (executes)** the function.

---

## Q4. Explain the flow of a callback function.

### Answer

Example

```ts
execute(greet);
```

Flow

```
execute(greet)
        ↓
operation = greet
        ↓
operation()
        ↓
greet()
        ↓
Function executes
```

---

## Q5. Where are callback functions used in Playwright?

### Answer

Callback functions are used in almost every Playwright test.

Examples:

- `test()`
- `beforeEach()`
- `afterEach()`
- `describe()`

Example

```ts
test("Login Test", async ({ page }) => {

    // Test steps

});
```

The function passed to `test()` is a callback function.

Playwright executes it while running the test.

---

## Q6. Why are callback functions useful in automation frameworks?

### Answer

They allow the same function to perform different tasks.

Example

Instead of creating multiple execution functions,

```ts
runSmoke();

runRegression();

runSanity();
```

we can write

```ts
executeSuite(runSmoke);

executeSuite(runRegression);

executeSuite(runSanity);
```

This reduces duplicate code.

---

## Q7. Why do we write `operation()` instead of just `operation`?

### Answer

`operation` only stores the function reference.

`operation()` executes the function.

Example

```ts
let greet = () => {

    console.log("Hello");

}

let operation = greet;

operation;     // Reference only

operation();   // Executes function
```

---

## Q8. Can different callback functions be passed to the same function?

### Answer

Yes.

That is the main advantage of callback functions.

Example

```ts
calculate(square, 5);

calculate(cube, 5);
```

The same function behaves differently depending on the callback.

---

## Q9. What are the advantages of callback functions?

### Answer

- Improves code reusability
- Reduces duplicate code
- Makes code flexible
- Easy to maintain
- Widely used in Playwright and JavaScript

---

## Q10. Explain callback functions using your Playwright project.

### Answer

In Playwright, when we write

```ts
test("Login Test", async ({ page }) => {

    // Test steps

});
```

the function passed to `test()` is a callback function.

Similarly,

- `beforeEach()`
- `afterEach()`
- `test.describe()`

also use callback functions.

Playwright calls these functions automatically during test execution.

---

# Interview Summary

- A callback function is a function passed as an argument to another function.
- The receiving function decides when to execute the callback.
- Pass a function using its name (`greet`).
- Execute a function using parentheses (`greet()`).
- Callback functions improve reusability and flexibility.
- Playwright heavily uses callback functions in `test()`, hooks, and `describe()` blocks.
