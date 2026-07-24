# Loops in TypeScript

Loops are used to execute a block of code repeatedly until a condition becomes false.

---

# Types of Loops

1. while Loop  
2. do-while Loop  
3. for Loop  

---

# 1. while Loop

The `while` loop checks condition first.

If condition is true:
- loop executes
- otherwise loop stops

---

## Syntax

```ts
while(condition){

    // code

    update variable;
}
```

---

## Example

```ts
let num = 1;

while(num <= 5){

    console.log(num);

    num++;
}
```

---

## Output

```text
1
2
3
4
5
```

---

## Important Point

- Condition is checked before execution
- If condition is false initially, loop will not execute

---

# 2. do-while Loop

The `do-while` loop executes code first and checks condition later.

---

## Syntax

```ts
do{

    // code

}while(condition);
```

---

## Example

```ts
let num = 1;

do{

    console.log(num);

    num++;

}while(num <= 5);
```

---

## Output

```text
1
2
3
4
5
```

---

## Important Point

- Executes at least one time even if condition is false

---

# 3. for Loop

The `for` loop is mostly used when number of iterations is known.

---

## Syntax

```ts
for(initialization; condition; increment/decrement){

    // code
}
```

---

## Example

```ts
for(let i = 1; i <= 5; i++){

    console.log(i);
}
```

---

## Output

```text
1
2
3
4
5
```

---

# for Loop Components

| Part | Purpose |
|---|---|
| Initialization | Starting value |
| Condition | Loop execution condition |
| Increment/Decrement | Updates loop variable |

---

# Difference Between while and do-while

| while | do-while |
|---|---|
| Checks condition first | Executes first |
| May execute zero times | Executes at least one time |

---

# break Statement

The `break` statement immediately stops loop execution.

---

## Example

```ts
for(let i = 1; i <= 10; i++){

    if(i == 5){

        break;
    }

    console.log(i);
}
```

---

## Output

```text
1
2
3
4
```

---

## Explanation

- Loop stops when `i` becomes 5

---

# continue Statement

The `continue` statement skips current iteration and moves to next iteration.

---

## Example

```ts
for(let i = 1; i <= 10; i++){

    if(i == 5){

        continue;
    }

    console.log(i);
}
```

---

## Output

```text
1
2
3
4
6
7
8
9
10
```

---

## Explanation

- Number `5` is skipped
- Loop continues with next iteration

---

# Interview Points

- Loops are used for repetitive tasks
- `while` checks condition before execution
- `do-while` executes at least once
- `for` loop is best when iterations are known
- `break` stops loop completely
- `continue` skips current iteration

---

# Best Practices

- Always update loop variable
- Avoid infinite loops
- Use meaningful loop conditions
- Prefer `for` loop for fixed iterations
- Use `break` and `continue` carefully

---

# Loops in TypeScript - VVIP Interview Questions

---

## Q1. What are loops, and why do we use them?

### Interview Answer (Short)

> "Loops execute the same block of code multiple times, helping us avoid duplicate code."

---

## Q2. What is the difference between `for`, `while`, and `do-while`?

### Interview Answer (Short)

> "`for` is used when the number of iterations is known. `while` is used when it is unknown. `do-while` always executes at least once."

---

## Q3. What is the difference between `while` and `do-while`?

### Interview Answer (Short)

> "`while` checks the condition first. `do-while` executes once before checking the condition."

---

## Q4. What is the difference between `break` and `continue`?

### Interview Answer (Short)

> "`break` exits the loop completely, whereas `continue` skips only the current iteration and continues with the next one."

---

## Q5. Why do you prefer `for...of` when iterating arrays?

### Interview Answer (Short)

> "`for...of` directly gives array values, making the code cleaner and easier to read than using array indexes."

---

## Q6. Where have you used loops in your Playwright framework?

### Interview Answer (Short)

> "I have used loops for Data-Driven Testing, reading JSON data, iterating browser lists, validating multiple UI elements, and implementing retry logic."

---

## Q7. Have you used nested loops in automation? Give an example.

### Interview Answer (Short)

> "Yes. For example, when validating rows and columns of a web table or comparing multiple datasets."

---

## Q8. Which loop do you use most in automation projects?

### Interview Answer (Short)

> "Mostly `for` and `for...of` because we frequently iterate through test data, browsers, and UI elements."

---

## Q9. Can every `while` loop be written as a `for` loop?

### Interview Answer (Short)

> "Yes, in many cases. The choice depends on readability. If the number of iterations is known, I prefer `for`; otherwise, I use `while`."

---

## Q10. Give a real Playwright example where `continue` is useful.

### Interview Answer (Short)

> "When running tests on multiple browsers, I can skip a browser that is temporarily unsupported while continuing with the remaining browsers."
