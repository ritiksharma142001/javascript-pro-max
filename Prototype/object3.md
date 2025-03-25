# JavaScript: Own Properties, Object.getOwnPropertyNames(), and `__proto__`

In JavaScript, objects have properties that can either be **own properties** (directly defined on the object) or **inherited properties** (from the prototype chain).

## 1️⃣ What is an "Own Property"?
An **own property** belongs directly to an object and is not inherited.

### Example:
```javascript
const person = {
  name: "Alice",
};

console.log(person.hasOwnProperty("name")); // true ✅ (Own property)
console.log(person.hasOwnProperty("toString")); // false ❌ (Inherited from Object.prototype)
```
📝 **"name"** is an own property because it belongs directly to `person`.
📝 **"toString"** is inherited from `Object.prototype`.

## 2️⃣ `Object.getOwnPropertyNames()` – Get All Own Properties (Even Hidden Ones)
This method returns **all own properties**, including **non-enumerable** ones.

### Example:
```javascript
const car = {
  brand: "Toyota",
};

// Adding a hidden (non-enumerable) property
Object.defineProperty(car, "year", {
  value: 2024,
  enumerable: false, // Hidden from normal loops
});

console.log(Object.keys(car)); // ["brand"] (Only enumerable properties)
console.log(Object.getOwnPropertyNames(car)); // ["brand", "year"] (Includes non-enumerable properties)
```
🚀 `Object.getOwnPropertyNames(car)` returns **everything**, even hidden properties like **"year"**.

## 3️⃣ Difference Between Own and Inherited Properties
Properties can either be **own properties** (directly on the object) or **inherited** (from the prototype).

### Example:
```javascript
const animal = {
  type: "mammal",
};

const dog = Object.create(animal); // dog inherits from animal
dog.name = "Buddy";

dog.type = "reptile"; // Overriding inherited property

console.log(dog.name); // "Buddy" (Own property)
console.log(dog.type); // "reptile" (Own property, overridden)

// Checking own properties
console.log(Object.getOwnPropertyNames(dog)); // ["name", "type"]
console.log(dog.hasOwnProperty("type")); // true ✅ (Own property after override)
console.log(dog.hasOwnProperty("name")); // true ✅ (Own property)
```
🔹 **"name"** and **"type"** are own properties of `dog` after the override.
🔹 Before overriding, **"type"** would have been inherited from `animal`.

## 4️⃣ `Object.getPrototypeOf()` – Check Inherited Properties
To check an object's prototype (inherited properties):

```javascript
console.log(Object.getPrototypeOf(dog)); // { type: "mammal" }
```
This shows that `dog` **inherits** from `animal`.

## 5️⃣ `__proto__` – Accessing & Modifying Prototype
Every object has an internal `[[Prototype]]`, accessible via `__proto__`.

### Example:
```javascript
const vehicle = {
  wheels: 4,
};

const car = {
  brand: "Toyota",
};

car.__proto__ = vehicle; // Inherit from `vehicle`

console.log(car.brand); // "Toyota" (Own property)
console.log(car.wheels); // 4 (Inherited from `vehicle`)
console.log(car.hasOwnProperty("wheels")); // false ❌ (Not an own property)
```
🔹 If a property exists in both the object and prototype, JavaScript uses the **own property first**.

## 6️⃣ `__proto__` vs. `prototype`
| Feature | `__proto__` | `prototype` |
|---------|------------|-------------|
| Belongs to | Objects | Functions (Constructors) |
| Used for | Getting/setting prototype of objects | Defines prototype for new objects created by a function |

### Example:
```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.sayHello = function () {
  console.log("Hello, I'm " + this.name);
};

const user = new Person("Alice");

console.log(user.__proto__); // Same as Person.prototype
console.log(Person.prototype); // Prototype of all objects created using Person
```
🔹 `__proto__` exists in every object.
🔹 `prototype` exists only in constructor functions.

## 7️⃣ Best Practices: Use `Object.getPrototypeOf()` and `Object.setPrototypeOf()`
Instead of modifying `__proto__`, use safer methods:

```javascript
console.log(Object.getPrototypeOf(dog)); // Get prototype
Object.setPrototypeOf(dog, null); // Remove prototype
```

## 📝 Summary
| Method | Explanation |
|--------|------------|
| `Object.keys(obj)` | Returns only **enumerable** own properties |
| `Object.getOwnPropertyNames(obj)` | Returns **all** own properties (including non-enumerable) |
| `hasOwnProperty(prop)` | Checks if a property is **directly on the object** (not inherited) |
| `Object.getPrototypeOf(obj)` | Returns the **prototype** (parent object) |
| `Object.setPrototypeOf(obj, proto)` | Safely sets an object's prototype |
| `__proto__` | Access or modify prototype (not recommended) |
| `prototype` | Defines prototype for constructor functions |

This helps in understanding **object properties, prototypes, and inheritance** in JavaScript. 🚀

