**Objects in JavaScript (Simple Explanation)**

In JavaScript, an object is a collection of key-value pairs. It is used to store and organize data. Objects can contain properties (variables) and methods (functions).

---

### 1. Creating an Object

#### Method 1: Using Object Literal
```javascript
const person = {
  name: "Alice",
  age: 25,
  greet: function () {
    console.log("Hello, my name is " + this.name);
  },
};
console.log(person.name); // Alice
person.greet(); // Hello, my name is Alice
```
**Explanation:**
- `name` and `age` are properties (variables).
- `greet` is a method (a function inside an object).
- `this.name` refers to the current object’s name property.

#### Method 2: Using `new Object()`
```javascript
const car = new Object();
car.brand = "Tesla";
car.model = "Model X";
car.start = function () {
  console.log(this.brand + " is starting...");
};
console.log(car.brand); // Tesla
car.start(); // Tesla is starting...
```
This method is less commonly used.

#### Method 3: Using Constructor Function
```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.greet = function () {
    console.log("Hello, I am " + this.name);
  };
}
const user1 = new Person("Bob", 30);
console.log(user1.name); // Bob
user1.greet(); // Hello, I am Bob
```
Here, `Person` acts as a blueprint for creating multiple objects.

#### Method 4: Using `class` (ES6)
```javascript
class Animal {
  constructor(name, type) {
    this.name = name;
    this.type = type;
  }
  speak() {
    console.log(this.name + " makes a noise.");
  }
}
const dog = new Animal("Buddy", "Dog");
dog.speak(); // Buddy makes a noise.
```
The `class` keyword simplifies object creation.

---

### 2. Nested Objects
```javascript
const student = {
  name: "John",
  marks: {
    math: 90,
    science: 85,
  },
};
console.log(student.marks.math); // 90
```
Objects can contain other objects inside them.

---

### 3. Accessing Object Properties

**Dot Notation:**
```javascript
console.log(person.name); // Alice
```
**Bracket Notation (Useful for dynamic keys):**
```javascript
console.log(person["name"]); // Alice
```

---

### 4. Looping Through an Object
```javascript
for (let key in person) {
  console.log(key + ": " + person[key]);
}
```
This loops through all properties of the object.

---

### 5. Object Methods

**`Object.keys()` → Get all keys**
```javascript
console.log(Object.keys(person)); // ["name", "age", "greet"]
```
**`Object.values()` → Get all values**
```javascript
console.log(Object.values(person)); // ["Alice", 25, ƒ greet()]
```
**`Object.entries()` → Get key-value pairs**
```javascript
console.log(Object.entries(person));
// [["name", "Alice"], ["age", 25], ["greet", ƒ greet()]]
```

---

### 6. Object Prototypes (Inheritance)
```javascript
const animal = {
  eats: true,
};

const dog = Object.create(animal);
dog.barks = true;

console.log(dog.eats); // true (inherited from animal)
console.log(dog.barks); // true (own property)
```
`dog` gets properties from `animal` through prototypal inheritance.

---

### 7. `Object.getOwnPropertyNames()`
This method returns an array of all properties (keys) directly belonging to an object, including non-enumerable properties.
```javascript
const person = {
  name: "Alice",
  age: 25,
  greet: function () {
    console.log("Hello!");
  },
};
console.log(Object.getOwnPropertyNames(person));
// Output: ["name", "age", "greet"]
```

**Difference Between `Object.keys()` & `Object.getOwnPropertyNames()`**
| Method | Returns | Includes Non-Enumerable? |
|--------|---------|------------------------|
| `Object.keys(obj)` | Only enumerable properties | ❌ No |
| `Object.getOwnPropertyNames(obj)` | All own properties | ✅ Yes |

---

### 8. Enumerable & Non-Enumerable Properties

#### **Enumerable Properties**
These properties show up when using `for...in` loops or `Object.keys()`.
```javascript
const person = {
  name: "Alice",
  age: 25,
};
console.log(Object.keys(person)); // ["name", "age"]
```

#### **Non-Enumerable Properties**
These properties do NOT show up in loops. Created using `Object.defineProperty()`.
```javascript
const car = {
  brand: "Toyota",
};
Object.defineProperty(car, "year", {
  value: 2024,
  enumerable: false,
});
console.log(Object.keys(car)); // ["brand"]
console.log(Object.getOwnPropertyNames(car)); // ["brand", "year"]
```

#### **Checking If a Property is Enumerable**
```javascript
console.log(car.propertyIsEnumerable("brand")); // true
console.log(car.propertyIsEnumerable("year")); // false
```

**Summary:**
| Property Type | Shows in `for...in` & `Object.keys()`? | Shows in `Object.getOwnPropertyNames()`? |
|--------------|--------------------------------|--------------------------------|
| Enumerable | ✅ Yes | ✅ Yes |
| Non-Enumerable | ❌ No | ✅ Yes |

---

### **Conclusion**
- Objects store data as key-value pairs.
- They can have methods (functions inside objects).
- Support inheritance through prototypes.
- The `class` syntax makes object creation easier.
- `Object.getOwnPropertyNames()` includes non-enumerable properties, while `Object.keys()` does not.

Would you like a visual diagram for better understanding? 😊

