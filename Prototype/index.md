# Prototype in JavaScript (Simple Explanation)

In JavaScript, **prototype** is like a hidden blueprint that objects can use to share properties and methods.

## Example:
```javascript
function Person(name) {
  this.name = name;
}

// Adding a method to the prototype
Person.prototype.sayHello = function () {
  console.log("Hello, my name is " + this.name);
};

const user1 = new Person("Alice");
const user2 = new Person("Bob");

user1.sayHello(); // Hello, my name is Alice
user2.sayHello(); // Hello, my name is Bob
```

## How It Works?
1. `Person` is a constructor function.
2. We add `sayHello` to `Person.prototype`, so all objects (user1, user2) inherit this method.
3. Both objects can use `sayHello()` without having their own copies—**saving memory**.

## Think of It Like:
📌 A **parent object** that gives common properties/methods to **child objects**.

## Why Use Prototype?
- **Saves Memory**: Instead of each object having a copy of `sayHello()`, all objects **share** the same function.
- **Easy to Update**: If you update the prototype, all objects using it get the change automatically.

## Analogy:
Imagine you and your friend live in the same house. Instead of each of you buying a separate fridge, you both use the **shared fridge** in the kitchen.

In JavaScript:
- **The house** = The **prototype**
- **You and your friend** = Objects created from a constructor function
- **The fridge** = A shared method on the prototype

This means all objects **inherit** common behaviors from the prototype, making JavaScript efficient and powerful!

