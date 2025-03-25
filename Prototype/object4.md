# JavaScript Constructor Functions and Prototypes

## 1️⃣ Create a Constructor Function
A constructor function is a blueprint for creating multiple objects.

```javascript
function Person(name, birthYear) {
  this.name = name;
  this.birthYear = birthYear;
}
```
🔹 What happens here?
- `Person` is a constructor function.
- `this.name` and `this.birthYear` are **instance properties** (each object gets its own copy).

## 2️⃣ Adding a Method to the Prototype
We add a method to `Person.prototype` so that all objects share it.

```javascript
Person.prototype.calAge = function () {
  console.log(`${this.name} is ${2025 - this.birthYear} years old.`);
};
```
🔹 Why use `.prototype`?
- **Saves memory**: Instead of each object having its own `calAge` function, all instances share one.

## 3️⃣ Creating Multiple Objects
Now, let's create multiple objects using `new Person()`.

```javascript
const jonas = new Person("Jonas", 2001);
const sarah = new Person("Sarah", 1995);

jonas.calAge(); // Jonas is 24 years old.
sarah.calAge(); // Sarah is 30 years old.
```
🔹 `jonas` and `sarah` inherit the `calAge()` method from `Person.prototype`.

## 4️⃣ Understanding `.constructor`
Each object keeps a reference to the constructor function that created it.

```javascript
console.log(jonas.constructor); 
// Output: [Function: Person]
```
🔹 What does this mean?
- `jonas.constructor === Person` ✅
- It shows which constructor function was used to create `jonas`.

## 5️⃣ Checking `.prototype`
Every function in JavaScript has a `.prototype` object.

```javascript
console.log(Person.prototype);
// Output: { calAge: [Function] }
```
🔹 What does this contain?
- `Person.prototype` holds all shared methods.
- Objects created using `new Person()` will inherit methods from this prototype.

## 6️⃣ Checking the Prototype of an Object
Every object has a hidden `[[Prototype]]` property that links to its prototype.

```javascript
console.log(jonas.__proto__ === Person.prototype); // true
console.log(sarah.__proto__ === Person.prototype); // true
```
🔹 Both `jonas` and `sarah` inherit from `Person.prototype`.

## 7️⃣ Summary
| Concept | Explanation |
|---------|------------|
| `Person.prototype.calAge` | Shared method for all instances. |
| `new Person(name, birthYear)` | Creates new objects from `Person`. |
| `.constructor` | Points to `Person` function. |
| `.prototype` | Stores shared methods. |
| `__proto__` | Links an object to its prototype. |

This helps in understanding how **constructor functions and prototypes** work in JavaScript. 🚀

