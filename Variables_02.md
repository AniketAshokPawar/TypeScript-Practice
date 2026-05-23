# Var, Let, Const in TypeScript

---

# 1. Scope

- `var` → Function Scope
- `let` and `const` → Block Scope

## Example

```ts
function variables(){

    if(true){

        var x = "Aniket";
        let y = "Ashok";
        const z = "Pawar";

        console.log(x);
        console.log(y);
        console.log(z);
    }

    console.log(x);

    // console.log(y);
    // Error:
    // Cannot access 'y' outside block scope

    // console.log(z);
    // Error:
    // Cannot access 'z' outside block scope
}

variables();
```

---

# 2. Declaration and Initialization

- `var` and `let` can be declared first and initialized later.
- `const` must be initialized during declaration.

## Example

```ts
var x;
x = 10;
console.log(x);

let y;
y = 20;
console.log(y);

// const z;
// Error:
// Const declarations must be initialized

// z = 30;
// console.log(z);
```

---

# 3. Re-Declaration

- Re-declaration is allowed only with `var`.

## Example

```ts
var Mname = "Aniket";
var Mname = "Annnniket";

console.log(Mname);
```

## Important Point

```ts
let city = "Mumbai";
// let city = "Pune"; // Error

const country = "India";
// const country = "USA"; // Error
```

---

# 4. Reassignment

- Reassignment is allowed for `var` and `let`.
- Reassignment is NOT allowed for `const`.

## Example

```ts
var age = 45;
age = 60;

console.log(age);

let ht = 45;
ht = 77;

console.log(ht);


// const salary = 50000;
// salary = 70000; // Error
```

---

# Interview Points

| Keyword | Scope | Re-Declaration | Reassignment |
|---|---|---|---|
| var | Function Scope | Allowed | Allowed |
| let | Block Scope | Not Allowed | Allowed |
| const | Block Scope | Not Allowed | Not Allowed |

---

# Best Practice

- Prefer using `const` by default.
- Use `let` when value needs to change.
- Avoid `var` in modern TypeScript/JavaScript.
