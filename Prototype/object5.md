# Understanding Property Inheritance & [[Prototype]] in JavaScript

## 1️⃣ How Property Inheritance Works
Imagine JavaScript objects as containers of properties.

🔹 When you try to access a property:
- JavaScript first looks inside the object.
- If the property is not found, JavaScript checks the object's prototype.
- If it’s still not found, it keeps checking up the prototype chain until it reaches an object with `null` as its prototype.

### Example:
```javascript
const animal = { type: "Mammal" };
const dog = Object.create(animal); // dog inherits from animal

console.log(dog.type); // "Mammal" (inherited from animal)
```
🔹 Here, `dog` does not have its own `type` property, so JavaScript looks at `animal` (its prototype) and finds `type: "Mammal"`.

## 2️⃣ What is [[Prototype]]?
`[[Prototype]]` is a hidden link inside every object that points to another object (its prototype).

✅ Checking an Object's Prototype:
```javascript
console.log(Object.getPrototypeOf(dog)); // { type: "Mammal" }
```
✅ Manually Setting an Object's Prototype:
```javascript
const cat = {};
Object.setPrototypeOf(cat, animal);

console.log(cat.type); // "Mammal" (inherited from animal)
```

## 3️⃣ `__proto__` vs `prototype`
| Concept    | Explanation |
|------------|------------|
| `__proto__` | A way to access or modify the `[[Prototype]]` of an object (deprecated, but still widely used). |
| `prototype` | A property on constructor functions, defining what new instances will inherit. |

### Example:
```javascript
function Person(name) {
  this.name = name;
}

console.log(Person.prototype); // {} (the prototype that new objects inherit)
```
🔹 `prototype` is only for constructor functions, while `__proto__` is for objects.

## 4️⃣ Setting `[[Prototype]]` with `__proto__` in Object Literals
```javascript
const animal = { type: "Mammal" };

const dog = {
  breed: "Labrador",
  __proto__: animal, // Setting animal as the prototype
};

console.log(dog.type);  // "Mammal" (inherited from animal)
console.log(dog.breed); // "Labrador" (own property)
```
🔹 `__proto__` inside object literals sets the prototype directly.

## 5️⃣ Summary
| Concept | Explanation |
|---------|------------|
| `[[Prototype]]` | Hidden link connecting an object to its prototype. |
| `Object.create(obj)` | Creates an object with `obj` as its prototype. |
| `Object.getPrototypeOf(obj)` | Retrieves the prototype of `obj`. |
| `Object.setPrototypeOf(obj, prototype)` | Changes the prototype of `obj`. |
| `__proto__` | Non-standard way to access/modify `[[Prototype]]` (not recommended). |
| `.prototype` | Used by constructor functions to define methods for all instances. |

This helps in understanding how **property inheritance and prototypes** work in JavaScript. 🚀

