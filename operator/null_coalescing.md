The nullish coalescing operator (??) is similar to the logical OR (||) operator, but it only considers null and undefined as "empty" values, while || treats all falsy values (like 0, "", false, NaN) as "empty."

### Difference Between ?? and ||
- **|| (OR Operator)** → Returns the right value if the left value is falsy (e.g., null, undefined, 0, "", false, NaN).
- **?? (Nullish Coalescing Operator)** → Returns the right value only if the left value is null or undefined.

### Example: || vs. ??
```javascript
console.log("" || "Default");  // Output: "Default" ("" is falsy)
console.log("" ?? "Default");  // Output: "" ("" is NOT null/undefined)

console.log(0 || 100);         // Output: 100 (0 is falsy)
console.log(0 ?? 100);         // Output: 0 (0 is NOT null/undefined)

console.log(null || "Hello");  // Output: "Hello" (null is falsy)
console.log(null ?? "Hello");  // Output: "Hello" (null is null)
```

### 🚀 Key Takeaway:
Use ?? when you only want to replace null or undefined, but still allow values like 0 and "" to remain.

### Operator Precedence & Syntax Error
The ?? operator has lower precedence than || but higher than the ternary operator (? :).

⚠ **You cannot mix && or || directly with ?? without parentheses, or you'll get a SyntaxError.**

### Invalid Code (Causes Error)
```javascript
null || undefined ?? "foo";  // ❌ SyntaxError
true && undefined ?? "foo";  // ❌ SyntaxError
```

### ✅ Corrected Code
```javascript
(null || undefined) ?? "foo"; // ✅ Output: "foo"
(true && undefined) ?? "foo"; // ✅ Output: "foo"
```

### Why?
JavaScript does not allow || or && to be used directly with ??, so you must use parentheses to group operations.

---

### Additional Examples
```javascript
console.log(null || undefined); // Output: null  
// Why?
// null is falsy and undefined is also falsy
// The first falsy value is returned, which is null.

console.log(true && undefined); // Output: undefined
// Why?
// true is truthy and undefined is falsy
// The first falsy value is returned, which is undefined.

// Why is the first falsy value returned?
// The && operator returns the first falsy value or the last truthy value.
// In this case, the first falsy value is undefined.
```

