# Logical AND (&&) and Logical OR (||) Operators - JavaScript Notes

## Logical AND (&&)

### What is Logical AND (&&)?
The logical AND (&&) operator checks multiple conditions and returns:
- **true** if **all** conditions are true.
- The **first falsy value** found (or the last truthy value if all are true).

#### Basic Example:
```js
const a = 3;
const b = -2;
console.log(a > 0 && b > 0); // Output: false (b > 0 is false)
```

### How && Works:
- It **evaluates values from left to right**.
- If a **falsy** value is found, it stops and returns that value.
- If **all are truthy**, it returns the last truthy value.

#### Examples:
```js
console.log("" && "foo");  // Output: "" (empty string is falsy)
console.log(2 && 0);        // Output: 0 (0 is falsy)
console.log("foo" && 4);    // Output: 4 (both are truthy, so last one is returned)
```

### Short-Circuit Evaluation
- If a falsy value is found, further evaluation stops.
- This is useful to prevent unnecessary function calls.

```js
function A() {
  console.log("called A");
  return false;
}
function B() {
  console.log("called B");
  return true;
}
console.log(A() && B());
// Logs "called A" and stops. B() is not called since A() returns false.
```

### Operator Precedence
- **&& has a higher precedence than || (OR)**.
- This means `&&` is evaluated **before** `||`.

```js
console.log(true || false && false);   // Output: true
console.log(true && (false || false)); // Output: false
console.log((2 === 3) || (4 < 0) && (1 === 1)); // Output: false
```

### More Examples
```js
a1 = true && true;       // true
a2 = true && false;      // false
a3 = false && true;      // false
a4 = "Cat" && "Dog";    // "Dog" (both truthy, returns last one)
a5 = false && "Cat";    // false (false is falsy, stops)
a6 = "Cat" && false;    // false (stops at false)
```

### Boolean Conversion Rules
You can convert **AND** to **OR** and vice versa:
```js
bCondition1 && bCondition2 === !(!bCondition1 || !bCondition2)
bCondition1 || bCondition2 === !(!bCondition1 && !bCondition2)
```

### Parentheses in Complex Expressions
- Logical expressions are **evaluated left to right**, so sometimes parentheses can be removed.

```js
bCondition1 || (bCondition2 && bCondition3) === bCondition1 || bCondition2 && bCondition3;
```

🚀 **Key Takeaway:**
- `&&` stops at the first falsy value.
- It has **higher precedence** than `||`.
- Short-circuits to optimize performance.

✅ Use `&&` carefully in conditions and function calls!

---

## Logical OR (||)

### What is Logical OR (||)?
The logical OR (||) operator:
- **Returns true** if **at least one** operand is true.
- **Returns the first truthy value** it encounters, or the last operand if all are falsy.

#### Basic Example:
```js
const a = 3;
const b = -2;
console.log(a > 0 || b > 0); // Output: true (a > 0 is true)
```

### How || Works:
- It **evaluates values from left to right**.
- If a **truthy** value is found, it stops and returns that value.
- If **all are falsy**, it returns the last falsy value.

#### Examples:
```js
console.log("" || "foo");  // Output: "foo" (empty string is falsy)
console.log(0 || 42);       // Output: 42 (0 is falsy, returns 42)
console.log("bar" || 4);    // Output: "bar" (first truthy value)
```

### Short-Circuit Evaluation
- If a truthy value is found, further evaluation stops.
- This is useful to provide default values.

```js
function A() {
  console.log("called A");
  return false;
}
function B() {
  console.log("called B");
  return true;
}
console.log(B() || A());
// Logs "called B" and stops. A() is not called since B() returns true.
```

### Operator Precedence
- **|| has lower precedence than && (AND)**.
- This means `&&` is evaluated **before** `||` unless parentheses are used.

```js
console.log(true || false && false);   // Output: true (&& evaluated first)
console.log((true || false) && false); // Output: false (Grouping changes order)
```

### More Examples
```js
a1 = true || true;        // true
a2 = false || true;       // true
a3 = true || false;       // true
a4 = "Cat" || "Dog";    // "Cat" (returns first truthy value)
a5 = false || "Cat";    // "Cat" (false is falsy, so returns "Cat")
a6 = "" || false;       // false (both are falsy, returns last one)
```

### Boolean Conversion Rules
You can convert **OR** to **AND** and vice versa:
```js
bCondition1 || bCondition2 === !(!bCondition1 && !bCondition2)
bCondition1 && bCondition2 === !(!bCondition1 || !bCondition2)
```

### Parentheses in Complex Expressions
- Logical expressions are **evaluated left to right**, so sometimes parentheses can be removed.

```js
bCondition1 && (bCondition2 || bCondition3) === bCondition1 && bCondition2 || bCondition3;
```

🚀 **Key Takeaway:**
- `||` stops at the first truthy value.
- It has **lower precedence** than `&&`.
- Short-circuits to optimize performance.

✅ Use `||` for default values and condition checks!

