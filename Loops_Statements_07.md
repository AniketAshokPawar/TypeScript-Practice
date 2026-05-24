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
