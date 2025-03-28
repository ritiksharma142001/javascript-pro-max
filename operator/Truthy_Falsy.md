**Truthy and Falsy Values in JavaScript**

### **Falsy Values**
A value is **falsy** if it is treated as `false` in a Boolean context. There are only six falsy values in JavaScript:

1. `false` – The boolean `false`
2. `0` – The number zero
3. `-0` – Negative zero
4. `""` or `''` – Empty string
5. `null` – Represents no value
6. `undefined` – A variable that has not been assigned a value
7. `NaN` – Not-a-Number

#### **Example of Falsy Values:**
```javascript
if (0) {
    console.log("This won't run");
} else {
    console.log("Falsy value detected");
}
```
**Output:** `Falsy value detected`

---

### **Truthy Values**
A **truthy** value is any value that is **not falsy**. This means all values except the six falsy ones are considered **truthy**.

#### **Examples of Truthy Values:**
- `true`
- Any non-zero number (`42`, `-5`, `3.14`)
- Any non-empty string (`"hello"`, `"false"`, `"0"`)
- Arrays (`[]`) and Objects (`{}`) (even empty ones)
- Functions (`function() {}`)
- `Infinity` and `-Infinity`

#### **Example of Truthy Values:**
```javascript
if ("hello") {
    console.log("Truthy value detected");
}
```
**Output:** `Truthy value detected`

---

### **Truthy & Falsy in Logical Operations**
#### **Using `||` (OR)**
```javascript
console.log(false || "Hello"); // Output: "Hello"
```
✅ `false` is falsy, so `"Hello"` is returned.

#### **Using `&&` (AND)**
```javascript
console.log(5 && "World"); // Output: "World"
```
✅ Both `5` (truthy) and `"World"` (truthy) are evaluated, so `"World"` is returned.

---

### **Why is this Useful?**
#### **Default Values using `||`**
```javascript
let name = "" || "Guest";
console.log(name); // Output: "Guest"
```
✅ Since `""` is falsy, `"Guest"` is assigned.

#### **Short-circuit Evaluation using `&&`**
```javascript
let user = { name: "Alice" };
console.log(user && user.name); // Output: "Alice"
```
✅ If `user` is falsy, it prevents accessing `user.name`.

---

### **Checking Falsy & Truthy Values**
#### **1️⃣ Using `if` Condition**
```javascript
let value = "Hello";

if (value) {
    console.log("Truthy");
} else {
    console.log("Falsy");
}
```
✅ **Output:** `Truthy` (because a non-empty string is truthy)

#### **2️⃣ Using `Boolean()` Function**
```javascript
console.log(Boolean(0));       // false (Falsy)
console.log(Boolean(1));       // true  (Truthy)
console.log(Boolean(""));      // false (Falsy)
console.log(Boolean("Hi"));    // true  (Truthy)
console.log(Boolean(null));    // false (Falsy)
console.log(Boolean([]));      // true  (Truthy)
console.log(Boolean({}));      // true  (Truthy)
```

#### **3️⃣ Using Double NOT (`!!`)**
```javascript
console.log(!!0);      // false (Falsy)
console.log(!!"Hi");   // true  (Truthy)
console.log(!!null);   // false (Falsy)
console.log(!!{});     // true  (Truthy)
console.log(!![]);     // true  (Truthy)
```

#### **4️⃣ Checking Falsy Values Using `!`**
```javascript
let testValue = 0;
if (!testValue) {
    console.log("Falsy Value");
} else {
    console.log("Truthy Value");
}
```
✅ **Output:** `Falsy Value` (because `0` is falsy)

---

### **Understanding `5 && "World"`**
#### **Why does `console.log(5 && "World")` print `"World"`?**
- In JavaScript, `&&` (AND) **returns the first falsy value** it encounters.
- If **all values are truthy, it returns the last truthy value**.

##### **Example with a Falsy Value:**
```javascript
console.log(0 && "Hello"); // Output: 0
```
✅ `0` is falsy, so JavaScript **immediately stops** and returns `0`.

##### **Example with Multiple Values:**
```javascript
console.log(5 && "Hello" && 0 && "World"); // Output: 0
```
✅ JavaScript stops at `0` (falsy) and returns it.

---

### **Truth Table for `&&`**
| Left Operand | Right Operand | Output |
|-------------|--------------|--------|
| **Truthy**  | **Truthy**   | Right Operand |
| **Falsy**   | **Truthy**   | Left Operand |
| **Truthy**  | **Falsy**    | Left Operand |
| **Falsy**   | **Falsy**    | Left Operand |

---

### **Key Takeaways**
✅ `&&` **stops at the first falsy value** and returns it.
✅ If **all values are truthy**, it **returns the last value**.

🚀 **Use these concepts for cleaner and more efficient JavaScript code!**

