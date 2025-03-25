# JavaScript: Own Properties & Object.getOwnPropertyNames()

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

console.log(dog.name); // "Buddy" (Own property)
console.log(dog.type); // "mammal" (Inherited from animal)

// Checking own properties
console.log(Object.getOwnPropertyNames(dog)); // ["name"]
console.log(dog.hasOwnProperty("type")); // false ❌ (Inherited, not own)
console.log(dog.hasOwnProperty("name")); // true ✅ (Own property)
```
🔹 **"name"** is an own property of `dog`.
🔹 **"type"** is inherited from `animal`, so it's **not** an own property of `dog`.

## 4️⃣ `Object.getPrototypeOf()` – Check Inherited Properties
To check an object's prototype (inherited properties):

```javascript
console.log(Object.getPrototypeOf(dog)); // { type: "mammal" }
```
This shows that `dog` **inherits** from `animal`.

## 5️⃣ Comparing `Object.getOwnPropertyNames()` Results
```javascript
console.log(Object.getOwnPropertyNames(animal)); // ["type"]
console.log(dog.hasOwnProperty("type")); // false ❌ (Inherited, not own)
console.log(Object.getOwnPropertyNames(dog) === Object.getOwnPropertyNames(animal)); // false

console.log(Object.getPrototypeOf(dog)); // { type: "mammal" }
console.log(Object.getPrototypeOf(animal)); // null
```

---

## 📝 Summary
| Method | What It Does |
|--------|-------------|
| `Object.keys(obj)` | Returns only **enumerable** own properties |
| `Object.getOwnPropertyNames(obj)` | Returns **all** own properties (including non-enumerable) |
| `hasOwnProperty(prop)` | Checks if a property is **directly on the object** (not inherited) |
| `Object.getPrototypeOf(obj)` | Returns the **prototype** (parent object) |

This helps in understanding **object properties and inheritance** in JavaScript. 🚀

