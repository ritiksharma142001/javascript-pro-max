**Optional Chaining (`?.`) in JavaScript**

### **What is Optional Chaining?**
Optional chaining (`?.`) is a feature in JavaScript that allows you to safely access properties or call functions on objects **without causing an error** if the object is `null` or `undefined`.

### **Why Use Optional Chaining?**
- Prevents errors when accessing nested properties.
- Returns `undefined` instead of throwing an error.
- Makes code cleaner and safer.

### **Syntax**
```js
obj?.property // Access property safely
obj?.[index]  // Access array elements safely
func?.()      // Call functions safely
```

### **Examples**

#### **1. Accessing Object Properties**
```js
const user = {
  name: "Alice",
  pet: { name: "Whiskers" }
};
console.log(user.pet?.name);  // "Whiskers"
console.log(user.dog?.name);  // undefined (No error)
```

#### **2. Accessing Array Elements**
```js
const numbers = [1, 2, 3];
console.log(numbers?.[1]);  // 2
console.log(numbers?.[5]);  // undefined
console.log(undefined?.[1]);  // undefined (No error)
```

#### **3. Calling Functions Safely**
```js
const obj = {
  greet: () => "Hello!"
};
console.log(obj.greet?.());  // "Hello!"
console.log(obj.sayGoodbye?.());  // undefined (No error)
```

### **Combining with Nullish Coalescing (`??`)**
```js
const user = { name: "John" };
console.log(user.age?.toString() ?? "Age not available");  
// Output: "Age not available"
```

### **Summary**
✅ Prevents runtime errors when accessing non-existent properties.
✅ Returns `undefined` instead of throwing an error.
✅ Works well with `??` to provide default values.
✅ Makes code more readable and maintainable.

**Use `?.` whenever you're unsure if an object or property exists!** 🚀

