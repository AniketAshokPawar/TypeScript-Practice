# Array Iteration Methods in TypeScript

These methods are commonly used to traverse and process arrays.

---

# 1. forEach()

Used to perform an action on each array element.

Returns:
```text
Nothing (void)
```

---

## Syntax

```ts
array.forEach((value,index) => {

});
```

---

## Example

```ts
let nums:number[] = [10,20,30];

nums.forEach((num,index)=>{

    console.log(`Index: ${index}, Value: ${num}`);
});
```

### Output

```text
Index: 0, Value: 10
Index: 1, Value: 20
Index: 2, Value: 30
```

---

# 2. map()

Used to transform each element and create a new array.

Returns:
```text
New Array
```

---

## Syntax

```ts
array.map((value,index)=>{

});
```

---

## Example

```ts
let nums:number[] = [10,20,30];

let doubled = nums.map(num => num*2);

console.log(doubled);
```

### Output

```text
[20,40,60]
```

---

# 3. filter()

Used to select elements matching a condition.

Returns:
```text
New Filtered Array
```

---

## Syntax

```ts
array.filter((value,index)=>{

});
```

---

## Example

```ts
let nums:number[] = [10,15,20,25,30];

let even = nums.filter(num => num%2==0);

console.log(even);
```

### Output

```text
[10,20,30]
```

---

# 4. some()

Checks whether at least one element satisfies a condition.

Returns:
```text
true / false
```

---

## Syntax

```ts
array.some((value,index)=>{

});
```

---

## Example

```ts
let nums:number[] = [10,20,30];

let result = nums.some(num => num>25);

console.log(result);
```

### Output

```text
true
```

Because:

```text
30 > 25
```

---

# 5. every()

Checks whether all elements satisfy a condition.

Returns:
```text
true / false
```

---

## Syntax

```ts
array.every((value,index)=>{

});
```

---

## Example

```ts
let nums:number[] = [10,20,30];

let result = nums.every(num => num>5);

console.log(result);
```

### Output

```text
true
```

Because all numbers are greater than 5.

---

# 6. reduce()

Used to reduce an array into a single value.

Returns:
```text
Single Value
```

---

## Syntax

```ts
array.reduce((accumulator,currentValue)=>{

},initialValue);
```

---

## Example

```ts
let nums:number[] = [10,20,30];

let sum = nums.reduce((acc,num)=>{

    return acc + num;

},0);

console.log(sum);
```

### Output

```text
60
```

---

# Difference Between Methods

| Method | Purpose | Return Type |
|----------|----------|----------|
| `forEach()` | Perform action on each element | `void` |
| `map()` | Transform elements | New Array |
| `filter()` | Select matching elements | New Array |
| `some()` | At least one matches? | Boolean |
| `every()` | All match? | Boolean |
| `reduce()` | Convert array into single value | Single Value |

---

# Quick Memory Trick

```text
forEach() → Do something

map() → Modify every element

filter() → Select elements

some() → At least one?

every() → Everyone?

reduce() → One final value
```

---

# Visual Example

```ts
let nums = [10,15,20,25,30];
```

```text
forEach()
↓
10
15
20
25
30

--------------------

map(num=>num*2)
↓
[20,30,40,50,60]

--------------------

filter(num=>num%2==0)
↓
[10,20,30]

--------------------

some(num=>num>25)
↓
true

--------------------

every(num=>num>5)
↓
true

--------------------

reduce((acc,num)=>acc+num,0)
↓
100
```

# Interview Priority (Playwright)

```text
1. forEach() ⭐⭐⭐⭐⭐
2. filter()  ⭐⭐⭐⭐⭐
3. map()     ⭐⭐⭐⭐
4. some()    ⭐⭐⭐
5. every()   ⭐⭐⭐
6. reduce()  ⭐⭐
```
