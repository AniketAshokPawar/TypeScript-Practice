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
