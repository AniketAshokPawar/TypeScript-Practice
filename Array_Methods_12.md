# Array Methods in TypeScript

---

# 1. push()

Used to add one or more elements at the end of an array.

## Syntax

```ts
array.push(value);
```

## Example

```ts
let nums:number[] = [10,20];

nums.push(30);

console.log(nums);
```

### Output

```text
[10,20,30]
```

---

# 2. pop()

Used to remove the last element from an array.

Returns removed element.

## Syntax

```ts
array.pop();
```

## Example

```ts
let nums:number[] = [10,20,30];

let removed = nums.pop();

console.log(nums);

console.log(removed);
```

### Output

```text
[10,20]

30
```

---

# 3. shift()

Used to remove the first element from an array.

Returns removed element.

## Syntax

```ts
array.shift();
```

## Example

```ts
let nums:number[] = [10,20,30];

let removed = nums.shift();

console.log(nums);

console.log(removed);
```

### Output

```text
[20,30]

10
```

---

# 4. unshift()

Used to add one or more elements at the beginning of an array.

## Syntax

```ts
array.unshift(value);
```

## Example

```ts
let nums:number[] = [20,30];

nums.unshift(10);

console.log(nums);
```

### Output

```text
[10,20,30]
```

---

# 5. concat()

Used to merge two or more arrays.

Does NOT modify original arrays.

## Syntax

```ts
array1.concat(array2);
```

## Example

```ts
let arr1:number[] = [10,20];

let arr2:number[] = [30,40];

let result = arr1.concat(arr2);

console.log(result);
```

### Output

```text
[10,20,30,40]
```

---

# 6. slice()

Used to extract a portion of an array.

Does NOT modify original array.

## Syntax

```ts
array.slice(startIndex,endIndex);
```

## Example

```ts
let nums:number[] = [10,20,30,40,50];

let result = nums.slice(1,4);

console.log(result);
```

### Output

```text
[20,30,40]
```

---

# 7. splice()

Used to:
- add elements
- remove elements
- replace elements

Modifies original array.

## Syntax

```ts
array.splice(startIndex,deleteCount,newValue);
```

## Example

```ts
let nums:number[] = [10,20,30,40];

nums.splice(2,1,300);

console.log(nums);
```

### Output

```text
[10,20,300,40]
```

---

# 8. indexOf()

Used to find index of an element.

Returns:
- index if found
- -1 if not found

## Syntax

```ts
array.indexOf(value);
```

## Example

```ts
let nums:number[] = [10,20,30,40];

console.log(nums.indexOf(30));
```

### Output

```text
2
```

---

# 9. includes()

Used to check whether an element exists in array.

Returns:
- true
- false

## Syntax

```ts
array.includes(value);
```

## Example

```ts
let nums:number[] = [10,20,30];

console.log(nums.includes(20));
```

### Output

```text
true
```

---

# 10. toString()

Converts array into comma-separated string.

## Syntax

```ts
array.toString();
```

## Example

```ts
let nums:number[] = [10,20,30];

let result = nums.toString();

console.log(result);

console.log(typeof result);
```

### Output

```text
10,20,30

string
```

---

# Interview Revision Table

| Method | Purpose | Original Array Modified? |
|----------|----------|----------|
| `push()` | Add at end | ✅ Yes |
| `pop()` | Remove last element | ✅ Yes |
| `shift()` | Remove first element | ✅ Yes |
| `unshift()` | Add at beginning | ✅ Yes |
| `concat()` | Merge arrays | ❌ No |
| `slice()` | Extract elements | ❌ No |
| `splice()` | Add/Remove/Replace | ✅ Yes |
| `indexOf()` | Find index | ❌ No |
| `includes()` | Check existence | ❌ No |
| `toString()` | Convert to string | ❌ No |

---

# Most Important Interview Question

## Difference Between slice() and splice()

| slice() | splice() |
|----------|----------|
| Extracts elements | Adds/Removes/Replaces elements |
| Does not modify original array | Modifies original array |
| Returns extracted array | Returns removed elements |
